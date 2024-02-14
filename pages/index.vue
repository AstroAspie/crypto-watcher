<script setup>
const { data } = await useFetch('/api/tickers?limit=10')
</script>

<template>
  <main>
    <h1 class="title">Astr0's Crypto Watcher</h1>

    <table border="1px solid">
      <thead>
      <tr>
        <th>Name</th>
        <th>Symbol</th>
        <th>Price</th>
        <th>Details</th>
      </tr>
      </thead>
      <tr v-for="currency in data.data" :key="data.data.id">
        <td>{{ currency.name }}</td>
        <td>{{ currency.symbol }}</td>
        <td>{{ currency.price_usd }}</td>
        <td>
          <NuxtLink :to="'/currency/' + currency.id">{{ currency.id }}</NuxtLink>
        </td>
      </tr>
    </table>
  </main>
</template>

<style scoped>
  body {
    background-color: #363636;
  }
  table {
    width: 100%;
  }
  
  th {
    background-color: #000;
    color: #fff;
  }
  
  td {
    padding: 10px;
  }
  
  tr:nth-child(even) {
    background-color: #f2f2f2;
    color: cornsilk;
  }
  
  tr:nth-child(odd) {
    background-color: #f2f2f2;
    color: #8d8d8d
  }
  
  a {
    color: #000;
  }
  
  a:hover {
    color: #fff;
  }
  
  .title {
    color: #35abbb;
  }
</style>