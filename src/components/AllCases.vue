<template>
  <section>
    <h3>{{ heading }}</h3>
    <ul>
      <li v-for="(value, key) in cases" :key="key">{{ key }}: {{ value }}</li>
    </ul>
  </section>
</template>

<script>
export default {
  data: () => ({ heading: "Get all NovelCovid Cases", cases: [] }),
  mounted() {
    this.fetchAll();
  },
  methods: {
    fetchAll: async function() {
      const { data } = await this.axios.get("https://corona.lmao.ninja/all");
      this.cases = data;
    }
  }
};
</script>

<style></style>
