<script setup>
import RandomRut from "./components/RandomRut.vue";
import RandomCorreo from "./components/RandomCorreo.vue";
</script>

<template>
  <div class="relative m-auto max-h-screen">
    <main
      class="md:grid md:grid-cols-2 w-[90%] p-12 m-auto sm:flex sm:flex-col transition-all duration-300 sm:gap-10 md:gap-20"
    >
      <div class="flex flex-col">
        <RandomRut />
      </div>
      <div class="flex flex-col">
        <RandomCorreo />
      </div>
    </main>
    <footer class="fixed bottom-0 right-4">
      <span class="text-xs bg-[#181818] px-2 py-1">Made by PC &copy;</span>
    </footer>
  </div>
</template>
