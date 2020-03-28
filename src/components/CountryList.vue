<template>
  <section>
    <h3>Beberapa data dari tiap negara yang terjangkit virus covid-19</h3>
    <vue-good-table
      :columns="columns"
      :rows="rows"
      :fixed-header="true"
      max-height="500px"
      :line-numbers="true"
      :row-style-class="rowStyleClassFn"
      :pagination-options="{
        enabled: true,
        mode: 'records',
        perPage: 10,
        position: 'bottom',
        perPageDropdown: [10, 50, 100],
        dropdownAllowAll: false,
        setCurrentPage: 2,
        nextLabel: 'next',
        prevLabel: 'prev',
        rowsPerPageLabel: 'Rows per page',
        ofLabel: 'of',
        pageLabel: 'page', // for 'pages' mode
        allLabel: 'All'
      }"
    />
  </section>
</template>

<script>
export default {
  name: "CountryList",
  data: () => ({
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
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const endpoint = "https://corona.lmao.ninja/countries?sort=country";
      const { data } = await this.$axios.get(endpoint);
      this.rows = data.reverse();
    },
    rowStyleClassFn(row) {
      return row.cases > 100000 ? "top-cases" : "";
    }
  }
};
</script>

<style>
.top-cases {
  background-color: #fbebeb;
}
</style>
