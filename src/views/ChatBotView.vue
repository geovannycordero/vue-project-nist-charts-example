<template>
  <div class="rounded-lg shadow-md w-[70dvw] h-[85dvh] p-6 my-10">
    <h1 class="pl-10 text-3xl font-bold mb-6">Chat Bot</h1>
    <div class="flex flex-col justify-between mt-4 h-[70dvh]">
      <div
        id="message-list"
        class="mx-5 h-[60dvh] overflow-y-auto p-4 bg-gray-50 rounded-lg"
      >
        <div class="mb-4">
          <div class="bg-blue-100 p-3 rounded-lg text-left">
            <p class="text-sm">
              ¡Hola! ¿Puedes darme detalles sobre las prácticas de seguridad de
              la empresa?
            </p>
          </div>
          <div class="text-xs text-gray-500 mt-1">Bot</div>
        </div>
        <div class="mb-4 text-right">
          <div class="bg-green-100 p-3 rounded-lg inline-block">
            <p class="text-sm">
              Claro, seguimos las prácticas de seguridad de NIST y NIST CFT para
              garantizar la protección de datos.
            </p>
          </div>
          <div class="text-xs text-gray-500 mt-1">Tú</div>
        </div>
        <div class="mb-4">
          <div class="bg-blue-100 p-3 rounded-lg text-left">
            <p class="text-sm">
              ¿Podrías especificar algunas de esas prácticas?
            </p>
          </div>
          <div class="text-xs text-gray-500 mt-1">Bot</div>
        </div>
        <div class="mb-4 text-right">
          <div class="bg-green-100 p-3 rounded-lg inline-block">
            <p class="text-sm">
              Implementamos controles de acceso, cifrado de datos y auditorías
              regulares para cumplir con los estándares de NIST.
            </p>
          </div>
          <div class="text-xs text-gray-500 mt-1">Tú</div>
        </div>
        <div class="mb-4">
          <div class="bg-blue-100 p-3 rounded-lg text-left">
            <p class="text-sm">
              Puedes elaborar más sobre los controles de acceso?
            </p>
          </div>
          <div class="text-xs text-gray-500 mt-1">Bot</div>
        </div>
      </div>
      <div
        id="message-input"
        class="py-2 mx-5 px-4 rounded-md bg-gray-100 text-gray-700 flex items-center justify-between"
      >
        <input
          type="text"
          placeholder="Escribe un mensaje..."
          class="bg-transparent outline-none"
        />
        <button class="ml-2 text-blue-500">Enviar</button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts"></script>
