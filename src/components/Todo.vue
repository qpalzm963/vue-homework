<template>
    <input v-model="newTodo" />
    <button @click="addTodo">新增待辦事項</button>
    <p>已完成：{{ completedCount }} / {{ tods.length }}</p>
    <ul v-for="todo in tods">
        <li :key="todo.text">
            <input type="checkbox" v-model="todo.completed" />
            <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
                {{ todo.text }}
            </span>
            <button @click="removeTodo(todo)"> - </button>
        </li>
    </ul>
</template>

<script>

import { ref, computed } from 'vue'

export default {
    name: 'Todo',
    setup() {
        const tasks = ref([])
        const completedCount = computed(() => {
            return tasks.value.filter(task => task.completed).length
        })
        const pendingCount = computed(() => {
            return tasks.value.length - completedCount.value
        })
        const newTodo = ref('')
        function addTodo() {
            if (newTodo.value.trim() !== '') {
                tasks.value.push({ text: newTodo.value, completed: false })
                newTodo.value = ''
            }
        }
        function removeTodo(item) {
            tasks.value = tasks.value.filter(task => task != item)
        }

        return {
            tods: tasks,
            newTodo,
            addTodo,
            removeTodo,
            completedCount
        }
    }
}
</script>

<style></style>