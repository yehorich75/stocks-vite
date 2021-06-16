<template>
  <div class="stock">
    <div class="stock-item" v-for="value in stock" :key="value.stock">
      <div class="stock-item__info">
        <div class="stock-item__cover">
          <img :src="value.image" :alt="value.companyName">
        </div>
        <h3 class="stock-item__title">
          {{ value.companyName }}
          <span>{{ value.symbol}}</span>
        </h3>
      </div>
      <span class="stock-item__price">{{ value.price }} $</span>
    </div>
  </div>
  <div>
    <h3>Get Info</h3>
    <select v-model="selected">
      <option value="" disabled>Select Company</option>
      <option v-for="value in stock" :key="value.stock" :value="value.description">{{ value.companyName }}</option>
    </select>
    <div class="info">
        {{ selected }}
    </div>
  </div>
</template>

<script lang="ts">
  import axios from 'axios'

  export default {
    name: 'Stocks',
    data() {
      return {
        stock: [],
        errors: [],
        selected: ''
      }
    },
    created() {
      axios.get('https://financialmodelingprep.com/api/v3/profile/AAPL,NVDA,TSLA,OKTA,INTC,DOCU,GDDY,PINS,TRIP,AMZN,DAL,V,SPCE,MDB,AMD,OZON?apikey=6e30ab1eaa8a5986f14b002b47b4d02c')
      .then(responce => {
        this.stock = responce.data
        console.log(responce)
      })
      .catch(e => {
        this.errors.push(e)
      })
    }
  }
</script>

