<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>สมัครสมาชิก</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <form @submit.prevent="register">
        <ion-item>
          <ion-label position="floating">ชื่อผู้ใช้</ion-label>
          <ion-input v-model="username" required></ion-input>
        </ion-item>
        <ion-item>
          <ion-label position="floating">อีเมล</ion-label>
          <ion-input type="email" v-model="email" required></ion-input>
        </ion-item>
        <ion-item>
          <ion-label position="floating">รหัสผ่าน</ion-label>
          <ion-input type="password" v-model="password" required></ion-input>
        </ion-item>
        <ion-button expand="full" type="submit">สมัครสมาชิก</ion-button>
      </form>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const username = ref('');
    const email = ref('');
    const password = ref('');

    const register = () => {
      // Handle registration logic here
      console.log('Registering:', { username: username.value, email: email.value, password: password.value });
    };

    return {
      username,
      email,
      password,
      register
    };
  }
});
</script>

<style scoped>
/* Add any specific styles for the RegisterComponent here */
</style>