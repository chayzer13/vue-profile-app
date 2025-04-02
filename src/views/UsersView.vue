<template>
  <div class="users">
    <h1>Users</h1>
    <div class="users-list">
      <div v-for="user in users" :key="user.id" class="user-card">
        <h3>{{ user.firstName }} {{ user.lastName }} {{ user.maidenName }}</h3>
        <p>{{ user.email }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UsersView',
  data() {
    return {
      users: []
    }
  },
  async created() {
    try {
      const response = await fetch('https://dummyjson.com/users')
      const data = await response.json()
      this.users = data.users
    } catch (error) {
      console.error('Error fetching users:', error)
    }
  }
}
</script>

<style scoped>
.users {
  padding: 32px 16px;
  max-width: 1152px;
  margin: 0 auto;
}

h1 {
  font-size: 44px;
  font-weight: 700;
  line-height: 60px;
  color: #21243D;
  margin-bottom: 40px;
}

.users-list {
  display: grid;
  gap: 20px;
}

.user-card {
  background: white;
  padding: 24px 32px;
  border-radius: 12px;
  box-shadow: 0 12px 30px rgba(187, 225, 250, 0.45);
  transition: transform 0.2s, box-shadow 0.2s;
}

.user-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 16px 40px rgba(187, 225, 250, 0.55);
}

.user-card h3 {
  margin: 0 0 8px 0;
  font-size: 20px;
  font-weight: 500;
  line-height: 29px;
  color: #21243D;
}

.user-card p {
  margin: 0;
  color: #8695A4;
  font-size: 16px;
  line-height: 24px;
}

@media (max-width: 768px) {
  h1 {
    font-size: 32px;
    line-height: 40px;
    margin-bottom: 32px;
  }

  .user-card {
    padding: 20px;
  }
}
</style> 