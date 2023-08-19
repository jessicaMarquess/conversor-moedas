<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="convert">
    <h2 class='title-convert'>{{ tipoUm }} to {{ tipoDois }}</h2>
   <div>
    <input type="text" v-model="moedaTipoUm" v-bind:placeholder="tipoUm" class="input-convert">
    <input type="button" value="CONVERT" v-on:click="converter" class="btn-convert">
   </div>
    <h3>the converted currency will remains: <span>{{ moedaTipoDois }}</span></h3>
  </div>
</template>

<script>
  export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Conversor',
    props: ['tipoUm', 'tipoDois'],
    data() {
      return {
        moedaTipoUm: '',
        moedaTipoDois: 0,
      };
    },
    methods: {  
      async converter() {
      try {
        let formatTextUrl = `${this.tipoUm}-${this.tipoDois}`;
        let url = `https://economia.awesomeapi.com.br/json/last/${formatTextUrl}`
        let concatenatedTypes = this.tipoUm.concat(this.tipoDois);

        const response = await fetch(url);
        const json = await response.json();

        if (json[concatenatedTypes]) {
          let cotacao = json[concatenatedTypes].high;
          this.moedaTipoDois = (cotacao * parseFloat(this.moedaTipoUm)).toFixed(2);
        } else {
          console.error('Dados de conversão não encontrados');
        }
      } catch (error) {
        console.error('Ocorreu um erro ao converter:', error);
      }
    },
  },
  }
</script>

<style scoped>
  .convert {
    display: flex;
    flex-direction: column;
    padding: 1rem;
    width: 25rem;
    background-color: #ffffff;
    border-radius: 0.5rem;
  }

  .btn-convert {
    display: inline-block;
    padding: 0.625rem 1.25rem;
    background-color: #fca311; 
    color: #fff; 
    border: none;
    border-radius: 0.25rem;
    cursor: pointer;
    font-size: 1rem;
    font-weight: bold;
    margin-left: 0.5rem;
  }

  .btn-convert:hover {
    opacity: 0.89;
  }

  .input-convert {
    display: inline-block;
    padding: 0.625rem 1.25rem;
    border-radius: 0.25rem;
  }
  
  span {
    color: #fca311;
  }

</style>