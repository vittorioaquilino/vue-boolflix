<template>
  <section class="ms_container">
      <div 
      class="movie-card text-center"
      v-for="(element, index) in cardList"
      :key="index"
      >
        <div>Titolo originale: {{ element.original_title }}</div>
        <div>
            Lingua: {{ element.original_language }}
            <img :src="isLanguage(element)" alt="">
        </div>
        <div>Titolo: {{ element.title }}</div>
        <div>Voto: {{ element.vote_average }}/10</div>
      </div>
  </section>
</template>

<script>
export default {
    name: "AppMain",
    data() {
        return {
            italiaFlag: require("../assets/img/italia-flag.jpg"),
            inghilterraFlag: require("../assets/img/inghilterra-flag.jpg"),
            germaniaFlag: require("../assets/img/germania-flag.jpg"),
            franciaFlag: require("../assets/img/francia-flag.jpg")
        };
    },
    props: ["cardList"],
    methods: {
        isLanguage(element) {
            if (element.original_language === "it") {
                return this.italiaFlag;
            } else if (element.original_language === "en") {
                return this.inghilterraFlag;
            } else if (element.original_language === "de") {
                return this.germaniaFlag;
            } else if (element.original_language === "fr") {
                return this.franciaFlag;
            }
        }
    }
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
    border-radius: 5px;
    color: white;
    font-size: .8rem;

    img {
        width: 15px;
        height: 15px;
        border-radius: 5px;
    }
}


</style>