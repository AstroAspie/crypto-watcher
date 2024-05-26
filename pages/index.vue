<script setup>
const { data } = await useFetch('/api/tickers?limit=10')
</script>

<template>
  <main>
    <h1 class="title">Astr0's Crypto Watcher</h1>
    <div class="container">
      <table class="crypto-table">
        <thead class="table-header">
        <tr>
          <th>Name</th>
          <th>Symbol</th>
          <th>Price</th>
          <th>Details</th>
        </tr>
        </thead>
        <tr v-for="currency in data.data" :key="currency.id" class="table-item">
          <td>{{ currency.name }}</td>
          <td>{{ currency.symbol }}</td>
          <td>{{ currency.price_usd }}</td>
          <td>
            <NuxtLink :to="'/currency/' + currency.id">{{ currency.id }}</NuxtLink>
          </td>
        </tr>
      </table>
    </div>
  </main>
</template>

<style scoped>
  body {
    background-color: #363636;
  }

  .container {
    display: flex;
    justify-content: center;
    height: 100vh;
  }
  
  table {
    width: 80%;
    border: 1px solid #000;
  }
  
  .table-header {
    color: #fff;
  }
  
  .crypto-table {
    width: 80%;
  }
  
  th {
    background-color: #000;
    color: #fff;
  }
  
  td {
    padding: 10px;
  }
  
  .table-item:nth-child(even) {
    color: #35abbb;
  }
  
  .table-item:nth-child(odd) {
    color: #fff;
  }
  
  .table-item:nth-child(even) {
    background-color: black;
  }
  
  a {
    color: lightblue;
  }
  
  a:hover {
    color: #fff;
  }
  
  .title {
    color: #35abbb;
  }
</style>