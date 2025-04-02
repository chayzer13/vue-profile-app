<template>
  <div class="home">
    <h1>Home page</h1>
    <div class="content">
      <div class="text-content">
        <p>Amet minim mollit non deserunt ullamco est sit aliqua dolor do amet sint. Velit officia consequat duis enim velit mollit. Exercitation veniam consequat sunt nostrud amet.</p>
        <router-link to="/login" class="auth-button">Authorization</router-link>
      </div>
      <div class="image-content">
        <img src="@/assets/tools.svg" alt="Tools" class="tools-image" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView'
}
</script>

<style scoped>
.home {
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

.content {
  display: flex;
  align-items: flex-start;
  gap: 60px;
  margin: 0 0 40px;
}

.text-content {
  flex: 1;
}

.text-content p {
  font-size: 16px;
  line-height: 24px;
  color: #21243D;
  margin-bottom: 38px;
}

.auth-button {
  display: inline-block;
  padding: 12px 20px;
  background-color: #FF6464;
  color: white;
  text-decoration: none;
  border-radius: 2px;
  font-size: 20px;
  font-weight: 500;
  line-height: 29px;
  transition: background-color 0.2s;
}

.auth-button:hover {
  background-color: #FF5252;
}

.image-content {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.tools-image {
  max-width: 100%;
  height: auto;
}

@media (max-width: 768px) {
  .content {
    flex-direction: column;
    gap: 32px;
  }

  .image-content {
    order: -1;
  }

  h1 {
    font-size: 32px;
    line-height: 40px;
    margin-bottom: 32px;
  }
}
</style> 