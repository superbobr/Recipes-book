<script setup>
import { ref } from 'vue'
const title = ref("Настроить окружение Vue")
const description = ref('Ipsum')
const isCompleted = ref(false)
const id = ref(1)
const toggleStatus = () => isCompleted.value = !isCompleted.value

</script>
<template>
<div class="card">
<span>номер: {{ id }}</span>
<p :class="{completed: isCompleted}">Название задачи: {{ title }}</p>
<p>Описание: {{ description }}</p>
<p>Статус: {{ isCompleted ? 'Выполнено' : 'В работе' }}</p>
<button @click="toggleStatus">Отметить как выполненное</button>
</div>
</template>

<style scoped>
.card {
    width: 30%;
    border: solid 2px darkgreen;
    padding: 10px;
}
.completed {
    text-decoration: line-through;
}
</style>