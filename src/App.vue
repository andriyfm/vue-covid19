<template>
  <div id="app">
    <AboutCovid />
    <AllCases />
  </div>
</template>

<script>
import AboutCovid from "./components/AboutCovid";
import AllCases from "./components/AllCases";

export default {
  name: "App",
  components: {
    AboutCovid,
    AllCases
  }
};
</script>

<style>
#app {
  font-family: Operator Mono, monospace;
}
</style>
