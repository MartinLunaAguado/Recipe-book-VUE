<template>
  <header>
    <nav class="  bg-orange-600 text-white p-4 shadow-lg">
      <div class="text-2xl font-bold">
        <RouterLink :to="{ name: 'home' }" class="hover:text-orange-200 hover:underline" >🍴 RECIPE BLOG</RouterLink>
      </div>
      <ul class="flex gap-18 items-center justify-between bg-orange-600 text-white p-4 shadow-lg ">
        <li>
          <RouterLink :to="{ name: 'home' }" class="hover:underline">Home</RouterLink>
        </li>
        <li>
          <RouterLink :to="{ name: 'favorites' }" class="hover:underline">Favorites</RouterLink>
        </li>
        <li>
          <RouterLink :to="{ name: 'add-recipe' }" class="hover:underline">Add Recipe</RouterLink>
        </li>
      </ul>
    </nav>
  </header>

  <main class="bg-gray-100 min-h-screen py-8">
    <RouterView />
  </main>
</template>

<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
</script>
