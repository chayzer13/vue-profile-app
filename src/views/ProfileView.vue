<template>
  <div class="profile">
    <h1>My profile</h1>
    <div v-if="error" class="error">{{ error }}</div>
    <div v-else-if="user" class="profile-info">
      <div class="profile-content">
        <div class="profile-fields">
          <div class="profile-field">
            <label>Username:</label>
            <span>{{ user.username }}</span>
          </div>
          <div class="profile-field">
            <label>Name:</label>
            <span>{{ user.firstName }}</span>
          </div>
          <div class="profile-field">
            <label>Lastname:</label>
            <span>{{ user.lastName }}</span>
          </div>
          <div class="profile-field">
            <label>Gender:</label>
            <span>{{ user.gender }}</span>
          </div>
          <div class="profile-field">
            <label>Email:</label>
            <span>{{ user.email }}</span>
          </div>
        </div>
        <div class="profile-image">
          <img src="@/assets/avatar.png" alt="Profile picture" />
        </div>
      </div>
      <button @click="handleLogout" class="logout-btn">Logout</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProfileView',
  data() {
    return {
      user: null,
      error: null
    }
  },
  methods: {
    handleLogout() {
      localStorage.removeItem('token')
      this.$router.push('/login')
    }
  },
  async created() {
    const token = localStorage.getItem('token')
    if (!token) {
      this.$router.push('/login')
      return
    }

    try {
      const response = await fetch('https://dummyjson.com/auth/me', {
        method: 'GET',
        headers: {
          'Authorization': `Bearer ${token}`
        }
      })
      
      if (!response.ok) {
        throw new Error('Invalid token')
      }
      
      this.user = await response.json()
    } catch (error) {
      this.error = 'Failed to load profile data'
      localStorage.removeItem('token')
    }
  }
}
</script>

<style scoped>
.profile {
  padding: 32px 16px;
  max-width: 1152px;
  margin: 0 auto;
}

.profile h1 {
  margin: 0 0 32px 0;
  font-size: 44px;
  font-weight: 700;
  line-height: 60px;
  color: #21243D;
}

.profile-info {
  background: white;
  padding: 32px;
  border-radius: 4px;
  box-shadow: 0 4px 10px rgba(187, 225, 250, 0.25);
}

.profile-content {
  display: flex;
  gap: 48px;
}

.profile-fields {
  flex: 1;
}

.profile-field {
  margin-bottom: 24px;
  display: flex;
  align-items: center;
}

.profile-field:last-child {
  margin-bottom: 0;
}

.profile-field label {
  font-weight: 500;
  margin-right: 16px;
  min-width: 120px;
  color: #21243D;
  font-size: 16px;
  line-height: 24px;
}

.profile-field span {
  color: #8695A4;
  font-size: 16px;
  line-height: 24px;
}

.profile-image {
  flex-shrink: 0;
  width: 240px;
}

.profile-image img {
  width: 240px;
  height: 240px;
  border-radius: 6px;
  object-fit: cover;
  box-shadow: 0 4px 10px rgba(187, 225, 250, 0.25);
}

.error {
  color: #FF6464;
  margin: 20px 0;
  padding: 16px;
  background: #FFEAEA;
  border-radius: 2px;
  font-size: 16px;
  line-height: 24px;
  text-align: center;
}

.logout-btn {
  display: block;
  margin: 32px auto 0;
  padding: 12px 24px;
  background: #FF6464;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
  transition: all 0.2s ease;
}

.logout-btn:hover {
  background: #FF5252;
  transform: translateY(-2px);
}

.logout-btn:active {
  transform: translateY(0);
}

@media (max-width: 768px) {
  .profile h1 {
    font-size: 32px;
    line-height: 40px;
    margin-bottom: 24px;
  }

  .profile-content {
    flex-direction: column-reverse;
    gap: 32px;
  }

  .profile-image {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .profile-image img {
    width: 200px;
    height: 200px;
  }

  .profile-info {
    padding: 24px;
  }
}
</style> 