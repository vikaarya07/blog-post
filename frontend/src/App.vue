<template>
  <div class="min-h-screen bg-sky-50/55">
    <Header />
    <router-view />
  </div>
</template>

<script setup>
import { RouterView } from 'vue-router'
import Header from "./components/Header.vue"
</script>
