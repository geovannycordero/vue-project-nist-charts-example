<template>
  <Dialog :open="isOpen" @close="setIsOpen" class="relative z-50">
    <div
      class="fixed inset-0 bg-black bg-opacity-50 transition-opacity"
      aria-hidden="true"
    ></div>
    <div class="fixed inset-0 flex items-center justify-center p-4">
      <DialogPanel
        class="w-full max-w-lg rounded-lg bg-white shadow-lg transform transition-all"
      >
        <DialogTitle
          class="text-lg font-medium leading-6 text-gray-900 p-4 border-b"
          >{{ profile }}</DialogTitle
        >
        <DialogDescription class="p-4 text-gray-600">
          Información de la mejora: {{ data }}
        </DialogDescription>

        <div class="p-4 text-gray-700">
          <p>
            El area de mejora ha sido identificada y se ha generado un plan de
            acción para mejorar la situación.
          </p>
        </div>

        <div class="p-4 flex justify-end space-x-2 border-t">
          <!-- <button
            @click="setIsOpen(false)"
            class="px-4 py-2 bg-red-600 text-white rounded-md hover:bg-red-700 transition"
          >
            Desactivar
          </button> -->
          <button
            @click="setIsOpen(false)"
            class="px-4 py-2 bg-gray-300 text-gray-700 rounded-md hover:bg-gray-400 transition"
          >
            Aceptar
          </button>
        </div>
      </DialogPanel>
    </div>
  </Dialog>
</template>

<script setup lang="ts">
// import { ref } from 'vue'
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  DialogDescription,
} from '@headlessui/vue'

defineProps<{
  isOpen: boolean
  profile: string
  data: string
  setIsOpen: (value: boolean) => void
}>()
</script>
