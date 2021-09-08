<template>
  <header>
    <h2>Reais para Dólares</h2>
  </header>
  <main>
    <br /><br />
    <span class="p-float-label">
      <InputText
        id="quantidadeEmReais"
        type="text"
        v-model="quantidadeEmReais"
      />
      <label for="quantidadeEmReais">Quantidade em Reais</label>
    </span>

    <br /><br />
    <span class="p-float-label">
      <InputText id="cotacaoEmDolar" type="text" v-model="cotacaoDoDolar" />
      <label for="cotacaoEmDolar">Cotação do Dólar</label>
    </span>

    <br /><br />
    <div>
      <Button label="Limpar" @click="limpar" />
      <Button label="Calcular" @click="calcular" />
    </div>

    <br /><br />
    <div v-show="resultadoConversao">
      <p>Com {{ quantidadeEmReais }} reais é possível comprar {{ resultadoConversao }} dólares a {{ cotacaoDoDolar }} cada</p>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {
      quantidadeEmReais: null,
      cotacaoDoDolar: null,
      resultadoConversao: null,
    };
  },
  methods: {
    limpar() {
      this.quantidadeEmReais = null;
      this.cotacaoDoDolar = null;
      this.resultadoConversao = null;
    },
    calcular() {
      this.resultadoConversao = (this.quantidadeEmReais / this.cotacaoDoDolar).toFixed(2);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
