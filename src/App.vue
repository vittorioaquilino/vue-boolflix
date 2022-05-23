<template>
    <div id="app">
        <AppHeader @searchEvents="filterResearch($event)"/>
    </div>
</template>

<script>
import AppHeader from "./components/AppHeader.vue";

export default {
  name: 'App',
  components: {
    AppHeader,
    
  },
  methods: {
    filterResearch(searchWord) {
       console.log(searchWord);
    }
  }
}
</script>

<style lang="scss">
@import "./style/common.scss";

</style>
