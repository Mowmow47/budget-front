<script setup>
import { ref, watchEffect } from "vue";

const API_URL = `http://api.budget.lan/accounts`;
const accounts = ref(null);

watchEffect(async () => {
  accounts.value = await (await fetch(API_URL)).json();
});
</script>

<template>
  <h1>Accounts list</h1>
  <ul>
    <li v-for="account in accounts">
      <span class="title">{{ account.name }} - {{ account.accountNumber }}</span
      ><br />Banque : {{ account.bankName }} <br />Taux d'interêt : {{ account.interestRate }}
    </li>
  </ul>
</template>

<style>
.title {
  font-weight: bold;
  text-decoration: underline;
}
</style>
