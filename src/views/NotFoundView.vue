<script setup lang="ts">
import { useRoute } from 'vue-router';

const route = useRoute();
const invalidId = route.query.invalidId as string;
console.log('Invalid ID in NotFoundView:', invalidId); // Depuración
</script>

<template>
  <div class="text-center space-y-6">
    <h1 class="text-5xl font-extrabold text-orange-600 mb-4">404 - Page Not Found</h1>
    <p v-if="invalidId" class="text-lg text-gray-700">
      Sorry, the recipe with ID <span class="font-bold text-red-600">"{{ invalidId }}"</span> does not exist.
    </p>
    <p v-else class="text-lg text-gray-700">
      Sorry, the page <span class="font-bold text-red-600">"{{ $route.params.pathMatch }}"</span> does not exist.
    </p>
    <div class="space-y-4">
      <RouterLink to="/" class="text-orange-600 hover:underline text-lg">
        Go back to Home
      </RouterLink>
      <div>
        <RouterLink to="/add-recipe" class="text-orange-600 hover:underline text-lg">
        Add a new recipe
      </RouterLink>
      </div>

    </div>
  </div>
</template>
