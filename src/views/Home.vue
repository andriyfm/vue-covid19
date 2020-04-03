<template>
  <div class="home">
    <CountryList />
  </div>
</template>

<script>
// @ is an alias to /src
import CountryList from "@/components/CountryList";

export default {
  name: "Home",
  components: { CountryList }
};
</script>
