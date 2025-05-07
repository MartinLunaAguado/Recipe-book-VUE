<template>
  <div>
    <h1 class="text-2xl font-bold mb-4">{{ recipe?.name }}</h1>
    <p class="mb-4">{{ recipe?.description }}</p>
    <div class="flex items-center gap-4">
      <RouterLink :to="{ name: 'edit-recipe', params: { id: recipe?.id } }" class="hover:underline"
        >Edit</RouterLink
      >
      <button
        v-if="recipe"
        @click="recipeStore.toggleFavorite(recipe.id)"
        class="px-4 py-2 bg-orange-600 text-white rounded hover:bg-orange-700"
      >
        {{ isFavorite ? 'Remove from favorites' : 'Add to favorites' }}
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useRecipeStore } from '@/stores/recipe';
import { computed, onMounted } from 'vue';
import { RouterLink, useRoute, useRouter } from 'vue-router';

const route = useRoute();
const recipeStore = useRecipeStore();
const router = useRouter();

const recipe = computed(() => recipeStore.getRecipeById(route.params.id as string));

onMounted(() => {
  const invalidId = route.params.id as string;
  console.log('Invalid ID:', invalidId); // Depuración: verifica el valor del ID

  if (!recipe.value) {
    // Si el ID no es válido, redirige a la página de error con el ID incorrecto
    router.push({ name: 'not-found', query: { invalidId } });
  }
});
const isFavorite = computed(() => (recipe.value ? recipeStore.isFavorite(recipe.value.id) : false));
</script>
