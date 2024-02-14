<script setup>
const route = useRoute()
const { data } = await useFetch('/api/ticker?id=' + route.params.id)
const coin = data.value[0]
</script>

<template>
  <div>
    <h2>{{  coin.name }} Default Page</h2>
    <table class="crypto-table">
      <thead>
        <th>Symbol</th>
        <th>Rank</th>
        <th>Price - US $</th>
        <th>Market Cap - US $</th>
      </thead>
      <tr>
        <td>{{ coin.symbol }}</td>
        <td>{{ coin.rank }}</td>
        <td>{{ coin.price_usd }}</td>
        <td>{{ coin.market_cap_usd }}</td>
      </tr>
    </table>
  </div>
</template>


<style scoped>
  body {
    background-color: #363636;
  }
  
  table {
    width: 100%;
  }

  .crypto-table {
    border: 1px solid #000;
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
  }
</style>