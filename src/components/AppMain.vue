<template>
    <section class="container">
        <h2 class="py-3 text-uppercase">Film</h2>
        <div class="ms_container">
            <AppCard
            v-for="(element, index) in cardMovieList"
            :key="index"
            :card="element"
            />
        </div>
        <h2 class="py-3 text-uppercase">Serie TV</h2>
        <div class="ms_container">
            <AppCard
            v-for="(element, index) in cardSeriesList"
            :key="index"
            :card="element" 
            />
        </div>
  </section>
</template>

<script>
import AppCard from "./AppCard.vue";
export default {
    name: "AppMain",
    components: {
        AppCard,
    },
    props: {
        cardMovieList: Array,
        cardSeriesList: Array,
    },
}
</script>

<style lang="scss" scoped>
@import "../style/common.scss";
@import "../style/variables.scss";

.ms_container {
    width: 95%;
    margin: 2rem auto;
    display: flex;
    flex-wrap: wrap;
}

h2 {
    color: white;
}


</style>