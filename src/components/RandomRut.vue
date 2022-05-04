<script setup>
import TheHeaderCard from "./global/TheHeaderCard.vue";
import identityImg from "@/assets/identity.png";
import TheMainList from "./global/TheMainList.vue";
import { ref } from "vue";
import { validate, format } from "@fiquu/cl-rut";

const ruts = ref([]);

function getRandomNumber(max, min) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function getRandomRut() {
  const guiones = "0123456789K";
  const digitos = getRandomNumber(3000000, 25000000);
  const dVerificador = guiones.charAt(getRandomNumber(0, 10));
  const rutNoValidado = `${digitos}-${dVerificador}`;
  return rutNoValidado;
}

function getValidRandomRut() {
  let rut = "";
  while (!validate(rut)) {
    rut = getRandomRut();
  }
  return format(rut);
}

function generarRuts() {
  ruts.value = [];
  for (let i = 0; i < 10; i++) {
    ruts.value.push(getValidRandomRut());
  }
}
</script>
<template>
  <div class="container flex flex-col gap-8">
    <header>
      <TheHeaderCard
        title="RUT Random"
        description="Genera una lista con 10 ruts aleatorios"
        :img-src="identityImg"
        @action:generate="generarRuts"
      />
    </header>
    <main>
      <TheMainList :items="ruts" />
    </main>
  </div>
</template>
