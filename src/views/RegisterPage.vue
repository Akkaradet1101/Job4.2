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
          <router-link to="/info" class="menu-btn">Products</router-link>
          <router-link to="/contact" class="menu-btn">Contact</router-link>
          <router-link to="/register" class="menu-btn">Register</router-link>
        </div>
      </transition>
    </aside>
    <main class="main-content center-content">
      <ion-page>
        
        <ion-content class="ion-padding register-bg">
          <div class="form-container animate-pop">
            <h2 class="form-title">Register for Activities</h2>
            <form @submit.prevent="submitForm" class="register-form">
              <label>
                <span class="icon"><svg width="24" height="24" fill="none" stroke="#3880ff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24"><circle cx="12" cy="8" r="4"/><path d="M4 20c0-3.3 3.6-6 8-6s8 2.7 8 6"/></svg></span> Full Name
                <input v-model="name" type="text" placeholder="Enter your full name" required />
              </label>
              <label>
                <span class="icon"><svg width="24" height="24" fill="none" stroke="#3880ff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24"><rect x="3" y="5" width="18" height="14" rx="4"/><path d="M3 7l9 6 9-6"/></svg></span> Email
                <input v-model="email" type="email" placeholder="Enter your email" required />
              </label>
              <label>
                <span class="icon"><svg width="24" height="24" fill="none" stroke="#3880ff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24"><path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/></svg></span> Interested Activities
                <input v-model="phone" type="text" placeholder="Enter activities of interest" required />
              </label>
              <label>
                <span class="icon"><svg width="24" height="24" fill="none" stroke="#3880ff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg></span> Student Password
                <input v-model="password" type="password" placeholder="Enter student password" required />
              </label>
              <button type="submit" class="glow-btn">Register</button>
            </form>
          </div>
        </ion-content>
      </ion-page>
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const name = ref('');
    const email = ref('');
    const phone = ref('');
    const password = ref('');
    const menuOpen = ref(true);
    const toggleMenu = () => {
      menuOpen.value = !menuOpen.value;
    };
    const submitForm = () => {
      console.log('Full Name:', name.value);
      console.log('Email:', email.value);
      console.log('Interested Activities:', phone.value);
      console.log('Student Password:', password.value);
    };
    return { name, email, phone, password, submitForm, menuOpen, toggleMenu };
  }
});
</script>

<style scoped>
.sidebar-layout {
  display: flex;
  height: 100vh;
  background: linear-gradient(135deg, #e3f0ff 0%, #b6c6d6 100%);
  animation: fadeInBg 1.2s;
}
.sidebar {
  width: 220px;
  background: #3a4a5a;
  color: #fff;
  padding: 2rem 1rem;
  min-height: 100vh;
  box-shadow: 4px 0 24px #0002;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
.menu-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  cursor: pointer;
  user-select: none;
  margin-bottom: 0.5rem;
  padding: 0.2rem 0.5rem 0.2rem 0;
}
.menu-header h2 {
  color: #b6e0ff;
  font-size: 1.3rem;
  margin: 0;
  letter-spacing: 1px;
  text-shadow: 0 2px 8px #0002;
}
.menu-toggle-icon {
  font-size: 1.2rem;
  color: #3880ff;
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
  display: flex;
  justify-content: center;
  align-items: center;
  background: transparent;
}
.center-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
.register-bg {
  background: transparent;
  min-height: 100vh;
  animation: fadeInBg 1.2s;
}
@keyframes fadeInBg {
  from { opacity: 0; }
  to { opacity: 1; }
}
.form-container {
  max-width: 420px;
  margin: 56px auto 0 auto;
  background: #fff;
  padding: 40px 24px 32px 24px;
  border-radius: 24px;
  box-shadow: 0 8px 40px #b6e0ff55, 0 1.5px 8px #fff2;
  animation: popIn 0.8s cubic-bezier(.68,-0.55,.27,1.55);
  display: flex;
  flex-direction: column;
  align-items: center;
  border: none;
  position: relative;
  overflow: hidden;
}
.form-title {
  color: #3880ff;
  margin-bottom: 2.2rem;
  font-size: 2.2rem;
  font-weight: 700;
  text-align: center;
  letter-spacing: 1.5px;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 2.5em;
  text-shadow: 0 4px 24px #b6e0ff33, 0 1.5px 8px #fff2;
  background: none;
}
.register-form label {
  display: flex;
  align-items: center;
  margin-bottom: 22px;
  color: #234;
  font-size: 1.13rem;
  font-weight: 600;
  letter-spacing: 0.5px;
  transition: color 0.2s;
  gap: 0.8em;
}
.register-form .icon {
  font-size: 1.6em;
  vertical-align: middle;
  margin-right: 0.7em;
  color: #3880ff;
  min-width: 1.6em;
  display: flex;
  align-items: center;
  justify-content: center;
}
.register-form input {
  flex: 1 1 0%;
  padding: 16px 18px;
  border: none;
  border-radius: 16px;
  background: #f4f6fb;
  color: #234;
  font-size: 1.13rem;
  transition: box-shadow 0.2s, background 0.2s;
  box-shadow: 0 2px 12px #b6e0ff22;
  outline: none;
  font-family: 'SF Pro Display', 'Segoe UI', Arial, sans-serif;
  margin-left: 0.5em;
}
.register-form input:focus {
  background: #fff;
  color: #3880ff;
  box-shadow: 0 0 16px #3880ff55;
}
.glow-btn {
  width: 100%;
  padding: 16px;
  background: linear-gradient(90deg, #3880ff 60%, #b6e0ff 100%);
  color: #fff;
  border: none;
  border-radius: 16px;
  font-size: 1.18rem;
  font-weight: 700;
  cursor: pointer;
  margin-top: 18px;
  box-shadow: 0 2px 16px #3880ff44;
  transition: background 0.2s, box-shadow 0.2s, transform 0.15s, color 0.2s;
  letter-spacing: 1.2px;
  outline: none;
  text-shadow: 0 2px 8px #3880ff33;
  font-family: 'SF Pro Display', 'Segoe UI', Arial, sans-serif;
  text-transform: uppercase;
  letter-spacing: 2px;
}
.glow-btn:hover {
  background: linear-gradient(90deg, #b6e0ff 60%, #3880ff 100%);
  color: #3880ff;
  box-shadow: 0 4px 32px #6cb6ff55;
  transform: translateY(-2px) scale(1.04);
}
.register-form label:focus-within {
  color: #3880ff;
}
@media (max-width: 600px) {
  .form-container {
    max-width: 98vw;
    padding: 18px 4vw 18px 4vw;
    border-radius: 16px;
  }
  .form-title {
    font-size: 1.3rem;
  }
}
.fade-menu-enter-active, .fade-menu-leave-active {
  transition: opacity 0.25s;
}
.fade-menu-enter-from, .fade-menu-leave-to {
  opacity: 0;
}
</style>