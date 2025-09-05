<template>
  <div id="app">
    <h2>image</h2>
    <InputComp />
    <h2>any</h2>
    <InputComp :is-income-cert="true"/>
  </div>
</template>

<script>
import InputComp from "./components/InputComp.vue";
export default {
  name: "App",
  components: {
    InputComp,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
