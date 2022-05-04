<script setup>
defineProps({
  title: String,
  description: String,
  imgSrc: String,
});

const emit = defineEmits(["action:generate"]);

function generar() {
  emit("action:generate");
}
</script>
<template>
  <div class="flex">
    <figure class="w-1/3 grid content-center">
      <img :src="imgSrc" alt="" width="" />
    </figure>
    <main class="w-2/3 flex flex-col justify-center content-center gap-5">
      <h1 class="text-green-500 text-center text-[2.6rem]">
        {{ title }}
      </h1>
      <p class="text-center text-xl mb-1 sm:hidden md:hidden xl:block">
        {{ description }}
      </p>
      <button
        class="text-white text-2xl bg-green-500 hover:bg-green-700 w-2/3 self-center rounded-full py-2 px-7 transition-all duration-300"
        @click="generar"
      >
        Generar
      </button>
    </main>
  </div>
</template>
