<template>
  <div class="p-6 max-w-4xl mx-auto">
    <nav class="mb-6 space-x-4">
      <RouterLink to="/" class="text-blue-500">Home</RouterLink>
      <RouterLink to="/about" class="text-blue-500">About</RouterLink>
      <RouterLink to="/posts" class="text-blue-500">Blog</RouterLink>
      <RouterLink to="/contact" class="text-blue-500">Contact</RouterLink>
    </nav>
    <router-view />
  </div>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>
