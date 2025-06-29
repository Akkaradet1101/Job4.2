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
      <div class="contact-card animate-pop">
        <h2>Contact Us</h2>
        <p>
          <span class="icon">
            <!-- iOS mail outline icon -->
            <svg width="1.3em" height="1.3em" viewBox="0 0 24 24" fill="none" stroke="#6cb6ff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="5" width="18" height="14" rx="2"/><polyline points="3 7 12 13 21 7"/></svg>
          </span>
          Email: <a href="mailto:support@computerstore.com">akkaradetthuengkan@gmail.com</a><br>
          <span class="icon">
            <!-- iOS call outline icon -->
            <svg width="1.3em" height="1.3em" viewBox="0 0 24 24" fill="none" stroke="#6cb6ff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92V21a2 2 0 0 1-2.18 2A19.72 19.72 0 0 1 3 5.18 2 2 0 0 1 5 3h4.09a2 2 0 0 1 2 1.72c.13 1.13.37 2.23.72 3.28a2 2 0 0 1-.45 2.11l-1.27 1.27a16 16 0 0 0 6.29 6.29l1.27-1.27a2 2 0 0 1 2.11-.45c1.05.35 2.15.59 3.28.72A2 2 0 0 1 22 16.92z"/></svg>
          </span>
          Tel: <a href="tel:0991234567">063-2549255</a>
        </p>
        <form class="contact-form">
          <input type="text" placeholder="Your Name" required />
          <input type="email" placeholder="Your Email" required />
          <textarea placeholder="Your Message" rows="4" required></textarea>
          <button type="submit">Send Message</button>
        </form>
      </div>
    </main>
  </div>
</template>

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
.contact-card {
  background: rgba(58,74,90,0.97);
  color: #fff;
  padding: 2.5rem 2rem;
  border-radius: 30px;
  box-shadow: 0 8px 32px rgba(0,0,0,0.5);
  min-width: 400px;
  max-width: 90vw;
  text-align: center;
  transition: transform 0.2s, box-shadow 0.2s;
  border: 2px solid #b6e0ff;
  position: relative;
}
.contact-card:hover {
  transform: translateY(-8px) scale(1.03);
  box-shadow: 0 16px 48px #6cb6ff55;
  border-color: #3399ff;
}
.animate-pop {
  animation: popIn 0.8s cubic-bezier(.68,-0.55,.27,1.55);
}
@keyframes popIn {
  0% { transform: scale(0.7); opacity: 0; }
  80% { transform: scale(1.05); opacity: 1; }
  100% { transform: scale(1); }
}
.contact-card h2 {
  font-size: 2.3rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
  letter-spacing: 1px;
  color: #b6e0ff;
  text-shadow: 0 2px 8px #0002;
}
.contact-card p {
  font-size: 1.2rem;
  font-weight: 500;
  margin-top: 1.2rem;
  line-height: 2;
}
.contact-card a {
  color: #6cb6ff;
  text-decoration: none;
  transition: color 0.2s;
  font-weight: bold;
}
.contact-card a:hover {
  color: #b6e0ff;
  text-decoration: underline;
}
.icon {
  font-size: 1.3em;
  vertical-align: middle;
  margin-right: 0.3em;
}
.fade-menu-enter-active, .fade-menu-leave-active {
  transition: opacity 0.25s;
}
.fade-menu-enter-from, .fade-menu-leave-to {
  opacity: 0;
}
.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
}
.contact-form input,
.contact-form textarea {
  padding: 0.8rem 1rem;
  border-radius: 8px;
  border: 1.5px solid #b6e0ff;
  font-size: 1rem;
  outline: none;
  transition: border 0.2s;
}
.contact-form input:focus,
.contact-form textarea:focus {
  border: 1.5px solid #3399ff;
}
.contact-form button {
  background: linear-gradient(90deg, #6cb6ff 60%, #b6c6d6 100%);
  color: #234;
  border: none;
  border-radius: 8px;
  padding: 0.8rem 1.2rem;
  font-size: 1.1rem;
  font-weight: bold;
  cursor: pointer;
  transition: background 0.2s, color 0.2s, transform 0.15s;
  box-shadow: 0 2px 12px #6cb6ff22;
}
.contact-form button:hover {
  background: linear-gradient(90deg, #3a4a5a 60%, #6cb6ff 100%);
  color: #fff;
  transform: translateY(-2px) scale(1.04);
}
</style>

<script setup>
import { ref } from 'vue';
const menuOpen = ref(true);
function toggleMenu() {
  menuOpen.value = !menuOpen.value;
}
</script>