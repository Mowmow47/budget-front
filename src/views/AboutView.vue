<script setup>
import { ref, watchEffect } from "vue";

const API_URL = `http://api.budget.lan/account`;
const accounts = ref(null);

watchEffect(async () => {
  accounts.value = await (await fetch(API_URL)).json();
});

console.log(accounts);
</script>

<template>
  <h1>Lastest accounts from the api</h1>
  <ul>
    <li v-for="account in accounts">
      <span class="title">{{ account.title }}</span
      ><br />Contenu : {{ account.content }}
    </li>
  </ul>
</template>

<style>
.title {
  font-weight: bold;
  text-decoration: underline;
}
</style>
