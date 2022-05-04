<script setup>
import { ref } from "vue";

defineProps({
  items: Array,
});

const copiados = ref([]);

function copiar(texto) {
  navigator.clipboard.writeText(texto);
  copiados.value.push(texto);
}

function isDisabled(texto) {
  const found = copiados.value.find((item) => item === texto);
  return found ? true : false;
}
</script>
<template>
  <ul class="flex flex-col gap-2">
    <li
      class="flex justify-between content-center"
      v-for="item in items"
      :key="item"
    >
      <span
        class="self-center text-xl transition-all duration-300"
        :class="isDisabled(item) ? 'line-through' : ''"
        >{{ item }}</span
      >
      <button
        class="text-white text-xl bg-green-500 hover:bg-green-700 self-center rounded-full py-2 px-7 transition-all duration-300 disabled:bg-gray-400 disabled:text-black"
        @click="copiar(item)"
        :disabled="isDisabled(item)"
      >
        {{ isDisabled(item) ? "Copiado" : "Copiar" }}
      </button>
    </li>
  </ul>
</template>
