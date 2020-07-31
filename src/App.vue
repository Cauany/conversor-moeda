<template>
  <div id="app">
    <Conversor
      moedaA="USD"
      moedaB="BRL"
    />
  </div>
</template>

<script>
import Conversor from './components/Conversor.vue'

export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>
#app{
  text-align: center;
}
</style>
