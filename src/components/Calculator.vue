<template>
    <div class="calculator">
        <h1>計算器</h1>
        <div>
            <input class="input-box" v-model="a" type="number" />
            <input v-model="b" type="number" />
        </div>
        <p v-if="isError">{{ errorMessage }}</p>
        <p v-else :class="result">
            結果：{{ result }}
        </p>
        <div>
            <button class="calc_button" @click="add">加</button>
            <button class="calc_button" @click="subtract">減</button>
            <button class="calc_button" @click="multiply">乘</button>
            <button class="calc_button" @click="divide">除</button>
        </div>
    </div>


</template>

<script>
import { ref } from 'vue'

export default {
    name: 'Calculator',
    setup() {
        const errorMessage = ref('')
        const isError = ref(false)

        const isCalculated = ref(false)
        const operationType = ref('')

        // 使用 ref 創建響應式數據
        const a = ref(0)
        const b = ref(0)
        const result = ref(0)

        // 定義加法函數
        const add = () => {
            result.value = a.value + b.value    // 更新狀態
            isCalculated.value = true
            operationType.value = 'add'

            // 一段時間後取消高亮
            setTimeout(() => {
                isCalculated.value = false
            }, 1000)

        }
        const subtract = () => {
            isError.value = false
            result.value = a.value - b.value
        }
        const multiply = () => {
            isError.value = false
            result.value = a.value * b.value
        }
        const divide = () => {
            // 先清除之前的錯誤
            errorMessage.value = ''
            isError.value = false

            // 檢查各種錯誤情況
            if (b.value == 0) {
                errorMessage.value = '除數不得為0'
                isError.value = true
                return
            }

            // 正常計算
            result.value = a.value / b.value
        }

        // 返回需要在模板中使用的數據和方法
        return {
            a,
            b,
            result,
            add,
            subtract,
            multiply,
            divide,
            isError,
            errorMessage,
            isCalculated,
            operationType,
        }
    }
}

</script>
<style>
.calculator {
    width: 300px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: #f9f9f9;
}

.input-box {
    display: flex;
    flex-direction: column;
    margin-bottom: 10px;
}

.result {
    transition: all 0.5s ease;
}

.calc_button {
    margin: 5px;
    padding: 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

.calc_button:hover {
    background-color: #45a049;
}
</style>