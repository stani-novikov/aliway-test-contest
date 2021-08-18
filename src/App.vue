<template>
  <div id="app">
    <Influences-controls
        :activeSortingParam="activeSortingParam"
        :isSortByIncrease="isByIncrease"
        @sortTable="sortTable"
    />
    <influences-table :influencers="influencers" />
  </div>
</template>

<script>
import InfluencesTable from "./components/InfluencesTable";
import FieldService from "./FieldService";
import InfluencesControls from "./components/InfluencesControls";

export default {
  name: 'App',
  components: {
    InfluencesControls,
    InfluencesTable,
  },
  data() {
    return {
      influencers: [],
      activeSortingParam: null,
      isByIncrease: false,
    }
  },
  methods: {
    sortTable(eventData) {
      this.activeSortingParam = eventData.sortParam;
      this.isByIncrease = !this.isByIncrease

      if (this.isByIncrease) {
        this.influencers.sort((a, b) => {
          return b[eventData.sortParam] - a[eventData.sortParam]
        })
      } else {
        this.influencers.sort((a, b) => {
          return a[eventData.sortParam] - b[eventData.sortParam]
        })
      }
    }
  },
  async created() {
    const fieldService = new FieldService();
    const influencers = await fieldService.getInfluencers();
    this.influencers = influencers;
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
