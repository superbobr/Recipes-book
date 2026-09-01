 <script setup>
 import { ref } from 'vue'
 const title = ref('')
 const description = ref('')
 const id = ref(2)
 const emit = defineEmits(['add-task'])
 const handleSubmit = () => {
  if (!title.value.trim()) return

  emit('add-task', {
    id: taskId.value++,
    title: title.value,
    description: description.value,
    isCompleted: false
  })
  title.value = ''
  description.value = ''
}
</script>
<template>
<div class="form">
<input type="text" v-model="title" placeholder="Введите название задачи" required>
<textarea v-model="description" placeholder="Введите описание задачи"></textarea>
<button @submit.prevent="handleSubmit">Создать задачу</button>
</div>
</template>
<style scoped>
.form {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    width: 30%;
    border: solid 2px darkgreen;
    padding: 10px;
}
</style>