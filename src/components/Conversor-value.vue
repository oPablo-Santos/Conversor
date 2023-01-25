<template>
  <div class="conversor">
    <h2>{{ moedaA }} para {{ moedaB }}</h2>
    <input type="text" v-bind:placeholder="moedaA" v-model="moedaA_value" />
    <input type="button" value="Converter" v-on:click="converter" />
    <h2>{{ moedaB_value }}</h2>
  </div>
</template>

<script>
export default {
  name: "conversor-value",
  props: ["moedaA", "moedaB"],
  data() {
    return {
      moedaA_value: "",
      moedaB_value: 0,
    };
  },
  methods: {
    converter() {
      var de_para = this.moedaA + "_" + this.moedaB;

      var url = "https://currency-converter5.p.rapidapi.com/currency/convert?format=json&from=AUD&to=CAD&amount=1";

      var options = {
        method: "GET",
        headers: {
          "X-RapidAPI-Key": "y",
          "X-RapidAPI-Host": "x",
        },
      };

      fetch(url, options)
        .then((res) => {
          return res.json();
        })
        .then((json) => {
          var cotacao = json[de_para];
          this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2);
        });
    },
  },
};
</script>

<style></style>
