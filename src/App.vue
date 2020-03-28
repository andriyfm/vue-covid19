<template>
  <div id="app">
    <AboutCovid />
  </div>
</template>

<script>
import AboutCovid from "./components/AboutCovid";

export default {
  name: "App",
  components: {
    AboutCovid
  }
};
</script>

<style>
#app {
  font-family: Operator Mono, monospace;
}
</style>
