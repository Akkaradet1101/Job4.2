<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Contact Us</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <transition name="fade-menu">
        <div class="menu-buttons">
          <router-link to="/" class="menu-btn">Home</router-link>
          <router-link to="/info" class="menu-btn">Activities</router-link>
          <router-link to="/contact" class="menu-btn">Contact</router-link>
          <router-link to="/register" class="menu-btn">Register</router-link>
        </div>
      </transition>
      <form @submit.prevent="submitContactForm">
        <ion-item>
          <ion-label position="floating">Name</ion-label>
          <ion-input v-model="name" required></ion-input>
        </ion-item>
        <ion-item>
          <ion-label position="floating">Email</ion-label>
          <ion-input type="email" v-model="email" required></ion-input>
        </ion-item>
        <ion-item>
          <ion-label position="floating">Message</ion-label>
          <ion-textarea v-model="message" required></ion-textarea>
        </ion-item>
        <ion-button expand="full" type="submit">Send Message</ion-button>
      </form>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      name: '',
      email: '',
      message: ''
    };
  },
  methods: {
    submitContactForm() {
      // Handle form submission logic here
      console.log('Contact Form Submitted:', {
        name: this.name,
        email: this.email,
        message: this.message
      });
      // Reset form fields
      this.name = '';
      this.email = '';
      this.message = '';
    }
  }
});
</script>

<style scoped>
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
.fade-menu-enter-active, .fade-menu-leave-active {
  transition: opacity 0.25s;
}
.fade-menu-enter-from, .fade-menu-leave-to {
  opacity: 0;
}
</style>