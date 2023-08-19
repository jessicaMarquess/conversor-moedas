<template>
 <div id="app">
  <h1>Currency Converter</h1>
    <div class="container"> 
      <Conversor tipo-um="USD" tipo-dois="BRL"/>
      <Conversor tipo-um="BRL" tipo-dois="USD"/>
      <Conversor tipo-um="USD" tipo-dois="BRLT"/>
      <Conversor tipo-um="BRLT" tipo-dois="USD"/>
      <Conversor tipo-um="BTC" tipo-dois="BRL"/>
      <Conversor tipo-um="BRL" tipo-dois="BTC"/>
      <Conversor tipo-um="BRL" tipo-dois="EUR"/>
      <Conversor tipo-um="EUR" tipo-dois="BRL"/>
    </div>
 </div>
</template>

<script>
import Conversor from './components/Conversor.vue';

export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #495057;
}
#app h1 {
  color: #fca311;
}
body {
  background-color: #000000;
  display: flex;
  justify-content: center; 
  align-items: center;
}

.container {
  width: 64rem;
  display: flex;
  flex-wrap: wrap;
  flex-grow: 1;
  justify-content: space-between;
  align-items: center;
  row-gap: 2rem;
  align-content: center;
  margin: 0 6.25rem;
  padding: 0.5rem 1rem;
}

</style>
