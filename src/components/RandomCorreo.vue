<script setup>
import TheHeaderCard from "./global/TheHeaderCard.vue";
import TheMainList from "./global/TheMainList.vue";
import emailImg from "@/assets/email.png";
import { onMounted, ref } from "vue";

const emails = ref([]);

function getRandomString(length, isEmailDomain) {
  const pool = isEmailDomain
    ? "abcdefghijklmnopqrstuvwxyz"
    : "abcdefghijklmnopqrstuvwxyz0123456789";

  let randomString = "";

  for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * pool.length);
    randomString += pool.charAt(randomIndex);
  }
  return randomString;
}

function getRandomEmail() {
  const user = getRandomString(5);
  const domainName = getRandomString(5);
  const domain = getRandomString(2, true);
  return `${user}@${domainName}.${domain}`;
}

function generarEmails() {
  emails.value = [];
  for (let i = 0; i < 10; i++) {
    emails.value.push(getRandomEmail());
  }
}

onMounted(() => {
  generarEmails();
});
</script>
<template>
  <div class="container flex flex-col gap-8">
    <header>
      <TheHeaderCard
        title="Correo Random"
        description="Genera una lista con 10 correos aleatorios"
        :img-src="emailImg"
        @action:generate="generarEmails"
      />
    </header>
    <main>
      <TheMainList :items="emails" />
    </main>
  </div>
</template>
