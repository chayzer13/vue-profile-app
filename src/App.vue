<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import linkedinIcon from './assets/linkedin.svg'
import facebookIcon from './assets/facebook.svg'
import twitterIcon from './assets/twitter.svg'
import instagramIcon from './assets/instagram.svg'
</script>

<template>
  <div class="app">
    <header>
      <nav>
        <router-link to="/">Home</router-link>
        <router-link to="/users">Users</router-link>
        <router-link to="/login">Login</router-link>
        <router-link to="/profile">Profile</router-link>
      </nav>
    </header>

    <main>
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>

    <footer>
      <div class="social-links">
        <a href="#" class="social-link">
          <img :src="facebookIcon" alt="Facebook" />
        </a>
        <a href="#" class="social-link">
          <img :src="twitterIcon" alt="Twitter" />
        </a>
        <a href="#" class="social-link">
          <img :src="instagramIcon" alt="Instagram" />
        </a>
        <a href="#" class="social-link">
          <img :src="linkedinIcon" alt="LinkedIn" />
        </a>
      </div>
      <p>© 2024 Your Company. All rights reserved.</p>
    </footer>
  </div>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  background-color: #ffffff;
  min-height: 100vh;
  color: #333333;
}

#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
  padding-bottom: 40px;
  margin-top: 60px;
  transition: padding 0.3s ease;
}

header {
  background: white;
  padding: 16px 0;
  box-shadow: 0 1px 2px rgba(0,0,0,0.1);
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
}

nav {
  max-width: 1152px;
  margin: 0 auto;
  display: flex;
  justify-content: flex-end;
  gap: 32px;
  padding: 0 16px;
}

nav a {
  text-decoration: none;
  color: #333333;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;
  position: relative;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

nav a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background-color: #FF6464;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

nav a:hover::after,
nav a.router-link-active::after {
  width: 100%;
}

nav a.router-link-active {
  color: #FF6464;
}

footer {
  background: white;
  padding: 32px 0;
  margin-top: auto;
  transition: background-color 0.3s ease;
}

footer:hover {
  background-color: #f8f8f8;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 35px;
  margin-bottom: 26px;
}

.social-link img {
  width: 30px;
  height: 30px;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.social-link:hover {
  opacity: 0.8;
  transform: translateY(-2px);
}

.social-link:active {
  transform: translateY(0);
}

footer p {
  text-align: center;
  color: #333333;
  font-size: 14px;
  line-height: 21px;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-enter-from {
  opacity: 0;
  transform: scale(0.98);
  filter: blur(3px);
}

.fade-leave-to {
  opacity: 0;
  transform: scale(1.02);
  filter: blur(3px);
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
  transform: scale(1);
  filter: blur(0);
}

.fade-enter-active {
  transition-delay: 0.3s;
}

nav a {
  position: relative;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

nav a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background-color: #FF6464;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

nav a:hover::after,
nav a.router-link-active::after {
  width: 100%;
}

.social-link {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.social-link:hover {
  opacity: 0.8;
  transform: translateY(-2px);
}

button {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

button:hover {
  background-color: #FF5252;
  transform: translateY(-1px);
}

.card {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.card:hover {
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
  transform: translateY(-2px);
}

input, textarea {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

input:focus, textarea:focus {
  border-color: #FF6464;
  box-shadow: 0 0 0 2px rgba(255,100,100,0.1);
  transform: translateY(-1px);
}

img {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

img:hover {
  opacity: 0.9;
  transform: scale(1.02);
}

h1, h2, h3 {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

h1:hover, h2:hover, h3:hover {
  color: #FF6464;
  transform: translateX(2px);
}

header {
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

header:hover {
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
</style>
