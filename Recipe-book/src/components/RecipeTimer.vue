<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const timeLeft = ref(100)
let timerId = null

onMounted(() => {
  timerId = setInterval(() => {
    if (timeLeft.value > 0) {
      timeLeft.value--
    }
  }, 1000)
  console.log('Таймер запущен!')
})

onUnmounted(() => {
  clearInterval(timerId)
  console.log('Таймер остановлен и очищен!')
})
</script>

<template>
  <div class="timer-box">
    <span>Осталось: {{ timeLeft }} сек</span>
  </div>
</template>

<style scoped>
.timer-box {
  margin-top: 8px;
  padding: 6px;
  background-color: #e8f5e9;
  border-radius: 4px;
  font-weight: bold;
}
</style>