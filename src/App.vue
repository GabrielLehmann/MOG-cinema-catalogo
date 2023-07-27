<template>
  <div id="app">
    <catalogo />
  </div>
</template>

<script>
import catalogo from "./components/catalogo.vue";

export default {
  name: "App",
  components: {
    catalogo,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
