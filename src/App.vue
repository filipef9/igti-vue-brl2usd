<template>
  <header class="bg-primary py-1 pl-4">
    <h2>Reais para Dólares</h2>
  </header>

  <main class="flex flex-column align-items-center">
    <div class="mt-5">
      <i class="pi pi-dollar text-6xl font-bold"></i>
    </div>

    <div class="p-float-label mt-5">
      <InputText
        id="quantidadeEmReais"
        type="text"
        v-model="quantidadeEmReais"
      />
      <label for="quantidadeEmReais">Quantidade em Reais</label>
    </div>

    <div class="p-float-label mt-5">
      <InputText id="cotacaoEmDolar" type="text" v-model="cotacaoDoDolar" />
      <label for="cotacaoEmDolar">Cotação do Dólar</label>
    </div>

    <div class="mt-5">
      <Button label="Limpar" @click="limpar" class="mr-1" />
      <Button label="Calcular" @click="calcular" class="ml-1" />
    </div>

    <div v-show="resultadoConversao" class="mt-5">
      <p>
        Com <strong>{{ quantidadeEmReais }}</strong> reais é possível comprar
        <strong>{{ resultadoConversao }}</strong> dólares a <strong>{{ cotacaoDoDolar }}</strong> cada
      </p>
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
      this.resultadoConversao = (
        this.quantidadeEmReais / this.cotacaoDoDolar
      ).toFixed(2);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
