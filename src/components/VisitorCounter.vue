<template>
  <div>
    <h2>จำนวนผู้เข้าชม: {{ count }}</h2>
    <button @click="increase">เพิ่ม</button>
    <button @click="decrease">ลด</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)

function increase() {
  count.value++
}

function decrease() {
  if (count.value > 0) count.value--
}
</script>