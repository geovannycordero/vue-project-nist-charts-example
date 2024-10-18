<script lang="ts" setup>
import { RouterLink } from 'vue-router'
</script>

<template>
  <header class="fixed top-0 left-0 w-full bg-white shadow-md z-10">
    <div class="wrapper flex items-center justify-between px-4 py-2">
      <img class="logo h-10" src="./icons/security.svg" alt="Logo" />
      <nav class="space-x-4">
        <RouterLink class="text-gray-700 hover:text-blue-600" to="/" exact>
          Inicio
        </RouterLink>
        <RouterLink class="text-gray-700 hover:text-blue-600" to="/chat">
          Chat
        </RouterLink>
        <RouterLink class="text-gray-700 hover:text-blue-600" to="/profile">
          Perfil
        </RouterLink>
        <RouterLink class="text-gray-700 hover:text-blue-600" to="/about">
          Acerca de
        </RouterLink>
      </nav>
    </div>
  </header>
</template>
