<template>
    <div id="app">
        <!-- header -->
        <AppHeader @searchEvents="filterResearch($event)"/>
        <!-- /header -->
        <!-- main -->
        <AppMain :cardMovieList="searchMovies" :cardSeriesList="searchSeries"/>
        <!-- /main -->
    </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
    
  },
  data() {
    return {
      searchMovies: [],
      searchSeries: [],
    }
  },
  methods: {
    filterResearch(searchWord) {
      axios.get("https://api.themoviedb.org/3/search/movie?api_key=2446d8ad240c37a38739ddeb5eba1083&query=" + searchWord) 
      .then((resp) => {
        this.searchMovies = resp.data.results;
      });
      axios.get("https://api.themoviedb.org/3/search/tv?api_key=2446d8ad240c37a38739ddeb5eba1083&query=" + searchWord)
      .then((resp) => {
        this.searchSeries = resp.data.results;
      });
    }
  } 
}

</script>

<style lang="scss">
@import "./style/common.scss";

</style>
