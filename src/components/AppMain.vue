<template>
  <section class="ms_container">
      <div 
      class="movie-card text-center"
      v-for="(element, index) in cardList"
      :key="index"
      >
        <p>Titolo originale: {{ element.original_title }}</p>
        <p>Lingua: {{ element.original_language }}</p>
        <p>Titolo: {{ element.title }}</p>
        <p>Voto: {{ element.vote_average }}</p>
      </div>
  </section>
</template>

<script>
export default {
    name: "AppMain",
    props: ["cardList"],
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.ms_container {
    width: 80%;
    margin: 2rem auto;
    display: flex;
    flex-wrap: wrap;
}
.movie-card {
    width: calc(100% / 4 - 20px);
    margin: 10px;
    border: 2px solid $brand-title-color;
    color: white;
    font-size: .8rem;
}

</style>