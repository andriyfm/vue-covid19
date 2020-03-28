<template>
  <section>
    <h3>
      Beberapa data kasus covid-19 berdasarkan negara:
      <select name="country" id="country" v-model="country">
        <option v-for="el in covidData" :key="el.countryInfo.iso2" :value="el">
          {{ el.country }}
        </option>
      </select>
    </h3>
    <vue-good-table :columns="columns" :rows="rows" />
  </section>
</template>

<script>
export default {
  name: "CountryData",
  data: () => ({
    country: "Indonesia",
    covidData: [],
    result: {},
    columns: [
      {
        label: "Country",
        field: "country"
      },
      {
        label: "Cases",
        field: "cases",
        type: "number"
      },
      {
        label: "Today Cases",
        field: "todayCases",
        type: "number"
      },
      {
        label: "Deaths",
        field: "deaths",
        type: "number"
      },
      {
        label: "Today Deaths",
        field: "todayDeaths",
        type: "number"
      },
      {
        label: "Recovered",
        field: "recovered",
        type: "number"
      },
      {
        label: "Active",
        field: "active",
        type: "number"
      },
      {
        label: "Critical",
        field: "critical",
        type: "number"
      },
      {
        label: "Cases/1M",
        field: "casesPerOneMillion",
        type: "number"
      },
      {
        label: "Deaths/1M",
        field: "deathsPerOneMillion",
        type: "number"
      }
    ],
    rows: [
      {
        country: "...",
        cases: 0,
        todayCases: 0,
        deaths: 0,
        todayDeaths: 0,
        recovered: 0,
        active: 0,
        critical: 0,
        casesPerOneMillion: 0,
        deathsPerOneMillion: 0
      }
    ]
  }),
  created() {
    this.fetchCovidData();
  },
  watch: {
    country(value) {
      this.result = value;
      this.rows = [value];
    }
  },
  methods: {
    async fetchCovidData() {
      const endpoint = "https://corona.lmao.ninja/countries?sort=country";
      const { data } = await this.$axios.get(endpoint);
      this.covidData = data.reverse();
    }
  }
};
</script>

<style></style>
