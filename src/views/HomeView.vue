<template>
  <main>
    <h1 class="text-2xl font-bold mb-4">Recipe Book</h1>
   <div>
    <ul class="flex items-center justify-between bg-orange-600 text-white p-4 shadow-lg">
    <span>Category: {{ category }}</span>
      <input type="text" placeholder="Seach recipes..." v-model="searchQuery" class="p-2 border rounded mb-4 w-full" />
   </ul> </div>
    <RecipeList :recipes="filteredRecipes" />
  </main>
</template>

<script setup lang="ts">
import RecipeList from '@/components/RecipeList.vue';
import { useRecipeStore } from '@/stores/recipe';
import { computed, ref } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const category = route.query.id ; // Accede al parámetro "category"

const recipeStore = useRecipeStore();
const searchQuery = ref('');
const filteredRecipes = computed(
  () => recipeStore.filteredRecipes(searchQuery.value)
);
</script>
