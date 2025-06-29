<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title></ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <home-component />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import HomeComponent from '../components/HomeComponent.vue';

export default defineComponent({
  components: {
    HomeComponent
  }
});
</script>

<style scoped>
/* Add any specific styles for the HomePage here */
</style>