<template>
  <div class="container">
    <h2 class="title">Stocks App</h2>
    <Stocks />
  </div>
</template>

<script lang="ts">
import { ref, defineComponent } from 'vue'
import Stocks from './components/Stocks.vue'

export default defineComponent({
  name: 'App',
  components: {
    Stocks
  }
})
</script>
