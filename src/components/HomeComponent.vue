<template>
  <div class="sidebar-layout">
    <aside class="sidebar">
      <div class="menu-header" @click="toggleMenu">
        <h2>Menu</h2>
        <span class="menu-toggle-icon">{{ menuOpen ? '▲' : '▼' }}</span>
      </div>
      <transition name="fade-menu">
        <div v-if="menuOpen" class="menu-buttons">
          <router-link to="/" class="menu-btn">Home</router-link>
          <router-link to="/info" class="menu-btn">Computer Products</router-link>
          <router-link to="/contact" class="menu-btn">Contact</router-link>
          <router-link to="/register" class="menu-btn">Register</router-link>
        </div>
      </transition>
    </aside>
    <main class="main-content center-content">
      <div class="welcome-card animate-pop">
        <h1 class="welcome-title">Welcome to the Computer World</h1>
        <b class="welcome-desc">Explore the latest innovations, tips, and products in the world of computers!</b>
        <div class="welcome-actions">
          <router-link to="/info" class="glow-btn">View Computer Products</router-link>
          <router-link to="/register" class="glow-btn alt">Register Your Computer</router-link>
        </div>
        <VisitorCounter />
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import VisitorCounter from '../components/VisitorCounter.vue'
const menuOpen = ref(true)
function toggleMenu() {
  menuOpen.value = !menuOpen.value
}
</script>

<style scoped>
.sidebar-layout {
  display: flex;
  height: 100vh;
  background: linear-gradient(135deg, #e3f0ff 0%, #b6c6d6 100%);
  animation: fadeInBg 1.2s;
}
@keyframes fadeInBg {
  from { opacity: 0; }
  to { opacity: 1; }
}
.sidebar {
  width: 220px;
  background: #3a4a5a;
  color: #fff;
  padding: 2rem 1rem;
  min-height: 100vh;
  box-shadow: 4px 0 24px #0002;
  z-index: 2;
}
.menu-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  user-select: none;
  margin-bottom: 0.5rem;
}
.menu-header h2 {
  color: #b6e0ff;
  text-shadow: 0 2px 8px #0002;
}
.menu-toggle-icon {
  font-size: 1.2rem;
  color: #b6e0ff;
  margin-left: 0.5rem;
  transition: transform 0.2s;
}
.menu-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}
.menu-btn {
  display: block;
  padding: 0.7rem 1.2rem;
  background: linear-gradient(90deg, #6cb6ff 60%, #b6c6d6 100%);
  color: #234;
  border: none;
  border-radius: 8px;
  font-size: 1.08rem;
  font-weight: 500;
  text-align: center;
  text-decoration: none;
  transition: background 0.2s, box-shadow 0.2s, transform 0.15s, color 0.2s;
  box-shadow: 0 2px 12px #6cb6ff22;
  cursor: pointer;
  outline: none;
}
.menu-btn:hover, .menu-btn.router-link-active {
  background: linear-gradient(90deg, #3a4a5a 60%, #6cb6ff 100%);
  color: #fff;
  box-shadow: 0 4px 24px #6cb6ff55;
  transform: translateY(-2px) scale(1.04);
}
.main-content {
  flex: 1;
  background: transparent;
}
.center-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.welcome-card {
  background: rgba(58,74,90,0.98);
  padding: 2.5rem 2.2rem 2.2rem 2.2rem;
  border-radius: 32px;
  box-shadow: 0 8px 32px #6cb6ff44;
  min-width: 400px;
  max-width: 90vw;
  text-align: center;
  border: 2px solid #b6e0ff;
  position: relative;
  animation: popIn 0.8s cubic-bezier(.68,-0.55,.27,1.55);
}
@keyframes popIn {
  0% { transform: scale(0.7); opacity: 0; }
  80% { transform: scale(1.05); opacity: 1; }
  100% { transform: scale(1); }
}
.welcome-card:hover {
  box-shadow: 0 16px 48px #6cb6ff55;
  border-color: #6cb6ff;
  transform: translateY(-6px) scale(1.02);
  transition: 0.2s;
}
.welcome-title {
  color: #b6e0ff;
  font-size: 2.3rem;
  font-weight: bold;
  margin-bottom: 1.2rem;
  letter-spacing: 1px;
  text-shadow: 0 2px 8px #0002;
  animation: fadeInText 1.2s;
}
@keyframes fadeInText {
  from { opacity: 0; transform: translateY(-30px);}
  to { opacity: 1; transform: translateY(0);}
}
.welcome-desc {
  font-size: 1.2rem;
  color: #fff;
  margin-bottom: 2rem;
  display: block;
  animation: fadeInText 1.5s 0.2s backwards;
}
.welcome-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  margin-top: 1.2rem;
}
.glow-btn {
  padding: 0.8rem 1.6rem;
  background: linear-gradient(90deg, #6cb6ff 60%, #b6c6d6 100%);
  color: #234;
  border: none;
  border-radius: 10px;
  font-size: 1.1rem;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 2px 12px #6cb6ff22;
  transition: background 0.2s, box-shadow 0.2s, transform 0.15s, color 0.2s;
  text-decoration: none;
  letter-spacing: 1px;
  outline: none;
  display: inline-block;
}
.glow-btn:hover, .glow-btn.alt:hover {
  background: linear-gradient(90deg, #3a4a5a 60%, #6cb6ff 100%);
  color: #fff;
  box-shadow: 0 4px 24px #6cb6ff55;
  transform: translateY(-2px) scale(1.04);
}
.glow-btn.alt {
  background: linear-gradient(90deg, #b6c6d6 60%, #6cb6ff 100%);
  color: #234;
}
.fade-menu-enter-active, .fade-menu-leave-active {
  transition: opacity 0.25s;
}
.fade-menu-enter-from, .fade-menu-leave-to {
  opacity: 0;
}
</style>