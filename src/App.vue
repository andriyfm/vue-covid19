<template>
  <div id="app">
    <AboutCovid />
    <AllCases />
    <CountryData />
    <CountryList />
  </div>
</template>

<script>
import AboutCovid from "./components/AboutCovid";
import AllCases from "./components/AllCases";
import CountryList from "./components/CountryList";
import CountryData from "./components/CountryData";

export default {
  name: "App",
  components: {
    AboutCovid,
    AllCases,
    CountryList,
    CountryData
  }
};
</script>

<style>
#app {
  font-family: Operator Mono, monospace;
}
</style>
