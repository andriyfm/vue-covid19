<template>
  <section>
    <h3>{{ heading }}</h3>
    <p v-if="cases.length === 0">Loading...</p>
    <ul v-else>
      <li v-for="(value, key) in cases" :key="key">
        {{ key }}: {{ value | numFormat }}
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  data: () => ({
    heading: "Total kasus Virus Covid-19 diseluruh dunia",
    cases: []
  }),
  mounted() {
    this.fetchAll();
  },
  methods: {
    async fetchAll() {
      const { data } = await this.axios.get("https://corona.lmao.ninja/all");
      this.cases = data;
    }
  }
};
</script>

<style></style>
