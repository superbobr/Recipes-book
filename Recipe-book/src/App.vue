<script setup>
import { ref, computed } from 'vue'
import RecipeTimer from '@/components/RecipeTimer.vue';
const showTimer = ref(false)
const timerToggle = () => showTimer.value = !showTimer.value
const recipes = ref([
  {
    id: 1,
    title: 'Яйцо пашот',
    category: 'Завтрак',
    cookingTime: 180
  },
  {
    id: 2,
    title: 'Паста Карбонара',
    category: 'Обед',
    cookingTime: 600
  }
])
const totalRecipes = computed(() => recipes.value.length)
</script>

<template>
  <main class="container">
    <h1>Моя Кулинарная Книга</h1>
    <p>Всего рецептов в книге: {{ totalRecipes }}</p>

    <div class="recipe-list">
      <div 
        v-for="recipe in recipes" 
        :key="recipe.id" 
        class="recipe-card"
      >
        <h3>{{ recipe.title }}</h3>
        <p>Категория: <strong>{{ recipe.category }}</strong></p>
        <p>Время варки: {{ recipe.cookingTime }} сек.</p>
        <button @click="timerToggle">Таймер</button>
        <RecipeTimer v-if="showTimer"/>
      </div>
    </div>
  </main>
</template>

<style scoped>
.container {
  max-width: 500px;
  margin: 20px auto;
  font-family: sans-serif;
}
.recipe-card {
  border: 1px solid #4caf50;
  border-radius: 8px;
  padding: 12px;
  margin-bottom: 12px;
  background-color: #f9fbf9;
}
</style>
