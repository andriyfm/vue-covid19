<template>
  <div id="app">
    <AboutCovid />
    <AllCases />
    <CountryList />
  </div>
</template>

<script>
import AboutCovid from "./components/AboutCovid";
import AllCases from "./components/AllCases";
import CountryList from "./components/CountryList";

export default {
  name: "App",
  components: {
    AboutCovid,
    AllCases,
    CountryList
  }
};
</script>

<style>
#app {
  font-family: Operator Mono, monospace;
}
</style>
