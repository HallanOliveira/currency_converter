<template>
  <q-page class="q-pa-md">
    <div class="text-h5 text-center">Conversor de Moedas</div>
    <q-input
      outlined
      placeholder="Digite o valor"
      v-model="text"
      class="q-pa-md"
    />
    <q-select
      class="q-pa-md"
      outlined
      v-model="base"
      :options="options"
      label="Moeda base"
    />
    <div class="text-center text-h6">para</div>
    <q-select
      class="q-pa-md"
      outlined
      v-model="final"
      :options="options"
      label="Moeda final"
    />
    <div class="q-pa-md">
      <q-btn color="primary" label="Converter" @click="getPrice()" />
    </div>
    <div class="q-pa-md">{{ result }}</div>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "PageIndex",
  data() {
    return {
      currency_base: "",
      options: ["teste1", "teste2", "teste3", "teste4"],
      result: "",
      base: "",
      final: "",
    };
  },
  mounted() {
    this.getCurrencyOptions();
  },
  methods: {
    getPrice() {
      fetch("https://economia.awesomeapi.com.br/last/USD-BRL").then(
        (response) => console.log(response)
      );
    },
    getCurrencyOptions() {
      fetch("https://economia.awesomeapi.com.br/json/all").then((response) =>
        console.log(response)
      );
    },
  },
});
</script>
