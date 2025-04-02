<template>
  <div class="login">
    <div class="login-form">
      <h2>Authorization</h2>
      <div class="login-hint">
        Use <strong>emilys</strong> / <strong>emilyspass</strong> to login
      </div>
      <div v-if="error" class="error-message">{{ error }}</div>
      <div class="form-group">
        <label>Username</label>
        <input type="text" v-model="username" placeholder="Enter username">
      </div>
      <div class="form-group">
        <label>Password</label>
        <input type="password" v-model="password" placeholder="Enter password">
      </div>
      <button @click="handleSubmit" class="submit-btn">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginView',
  data() {
    return {
      username: '',
      password: '',
      error: ''
    }
  },
  methods: {
    async handleSubmit() {
      try {
        const response = await fetch('https://dummyjson.com/auth/login', {
          method: 'POST',
          headers: { 
            'Content-Type': 'application/json',
            'Accept': 'application/json'
          },
          body: JSON.stringify({
            username: this.username.trim(),
            password: this.password.trim()
          })
        })
        const data = await response.json()
        console.log('Server response:', data)
        
        if (!response.ok) {
          throw new Error(data.message || 'Invalid credentials')
        }
        
        localStorage.setItem('token', data.accessToken)
        this.$router.push('/profile')
      } catch (error) {
        this.error = 'An error occurred. Please try again.'
        console.error('Login error:', error)
      }
    }
  }
}
</script>

<style scoped>
.login {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: calc(100vh - 200px);
  padding: 20px;
}

.login-form {
  background: white;
  padding: 32px;
  border-radius: 12px;
  box-shadow: 0 12px 30px rgba(187, 225, 250, 0.45);
  width: 100%;
  max-width: 400px;
}

.login-form h2 {
  margin: 0 0 32px 0;
  font-size: 34px;
  font-weight: 700;
  line-height: 50px;
  color: #21243D;
  text-align: center;
}

.login-hint {
  text-align: center;
  color: #8695A4;
  font-size: 14px;
  margin-bottom: 24px;
  padding: 12px;
  background: #F5F5F5;
  border-radius: 8px;
}

.login-hint strong {
  color: #21243D;
  font-weight: 500;
}

.form-group {
  margin-bottom: 24px;
}

.form-group label {
  display: block;
  margin-bottom: 8px;
  color: #21243D;
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
}

.form-group input {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid #E0E0E0;
  border-radius: 8px;
  font-size: 16px;
  line-height: 24px;
  color: #21243D;
  transition: all 0.2s;
  background: #FFFFFF;
}

.form-group input::placeholder {
  color: #8695A4;
}

.form-group input:focus {
  outline: none;
  border-color: #FF6464;
  box-shadow: 0 0 0 3px rgba(255, 100, 100, 0.1);
}

.submit-btn {
  width: 100%;
  padding: 12px;
  background: #FF6464;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
  transition: all 0.2s;
}

.submit-btn:hover {
  background: #FF5252;
  transform: translateY(-1px);
}

.submit-btn:active {
  transform: translateY(0);
}

.error-message {
  color: #FF6464;
  margin-bottom: 24px;
  font-size: 16px;
  line-height: 24px;
  padding: 12px 16px;
  background: #FFEAEA;
  border-radius: 2px;
  text-align: center;
}

@media (max-width: 768px) {
  .login-form {
    padding: 24px;
  }

  .login-form h2 {
    font-size: 28px;
    line-height: 40px;
    margin-bottom: 24px;
  }
}
</style> 