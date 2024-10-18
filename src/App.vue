<script setup lang="ts">
import { RouterView } from 'vue-router'
import NavBar from '@/components/NavBar.vue'
</script>

<template>
  <NavBar />
  <!-- Add padding to the top to avoid content overlapping the fixed navbar -->
  <main>
    <RouterView />
  </main>
</template>
