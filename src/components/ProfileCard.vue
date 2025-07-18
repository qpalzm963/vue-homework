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
</template>

<script>
export default {
  name: 'ProfileCard',
  data() {
    return {
      name: 'John',
      job: 'Engineer',
      age: 15,
      profileImage: 'https://via.placeholder.com/150x150/4CAF50/white?text=John',
      showDetail: true
    }
  },
  methods: {
    toggleDetail() {
      this.showDetail = !this.showDetail
    }
  }
}
</script>

<style scoped>
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