<template>
  <div class="profile-card">
    <h1>個人資料卡片</h1>
    
    <div class="basic-info">
      <img :src="profileImage" alt="個人頭像" class="profile-image" />
      <h2>{{ name }}</h2>
    </div>
    
    <div v-if="showDetail" class="details">
      <p><strong>年齡：</strong>{{ age }} 歲</p>
      <p><strong>職業：</strong>{{ job }}</p>
    </div>
    
    <div v-else class="hidden-message">
      <p>詳細資料已隱藏</p>
    </div>
    
    <button @click="toggleDetail" class="toggle-btn">
      {{ showDetail ? '隱藏詳細資料' : '顯示詳細資料' }}
    </button>
  </div>
  <div> </div>
  <div class="profile-my-card">
    <h1>個人卡片</h1>
    <p>{{ name }}</p>
    <div class="profile-detail"  v-if="showDetail"> 
      <p>年齡 : {{ age }}</p>
      <p>職業 : {{ job }}</p>
    </div>
    <button class="myBt" @click="toggleDetail"> {{ showDetail?'隱藏':'顯示' }}</button>
  </div>

</template>

<script>
import { ref } from 'vue'

export default {
  name: 'ProfileCard',
  setup() {
    // 使用 ref 創建響應式數據
    const name = ref('John')
    const job = ref('Engineer')
    const age = ref(15)
    const profileImage = ref('https://via.placeholder.com/150x150/4CAF50/white?text=John')
    const showDetail = ref(true)
    
    // 定義方法
    const toggleDetail = () => {
      showDetail.value = !showDetail.value
    }
    
    // 返回需要在模板中使用的數據和方法
    return {
      name,
      job,
      age,
      profileImage,
      showDetail,
      toggleDetail
    }
  }
}
</script>

<style scoped>
.myBt{
  background-color: #4CAF50;
  border-color: #ddd;
  shape-rendering: 0;
  cursor: pointer;
  color: white;
  margin: 20px 0;
  border-radius: 10px;
  padding: 10px 25px;
} 
.profile-detail{
  background-color: white;
  border-radius: 10px;
  padding: 15;
}
.profile-my-card{
  height: 300px;
  width: 300px;
  background-color: #e1e1e1;
  text-align: center;
  border-radius: 20px;
  padding: 20px;
}

.profile-card {
  max-width: 400px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  text-align: center;
  font-family: Arial, sans-serif;
}

.basic-info {
  margin-bottom: 20px;
}

.profile-image {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  margin-bottom: 10px;
}

.details {
  background-color: #f9f9f9;
  padding: 15px;
  border-radius: 5px;
  margin: 15px 0;
}

.details p {
  margin: 8px 0;
  text-align: left;
}

.hidden-message {
  color: #999;
  font-style: italic;
  margin: 15px 0;
}

.toggle-btn {
  background-color: #4CAF50;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

.toggle-btn:hover {
  background-color: #45a049;
}
</style>