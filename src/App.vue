<template>
  <div id="app">
    <ConversorValue moeda-a="USD" moeda-b="BRL" />

  </div>
</template>

<script>
import ConversorValue from "./components/Conversor-value.vue";

export default {
  name: "App",
  components: {
    ConversorValue
  },
};
</script>

<style>

</style>
