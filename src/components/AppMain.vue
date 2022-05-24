<template>
  <section class="ms_container">
      <div 
      class="movie-card text-center"
      v-for="(element, index) in cardMovieList"
      :key="index"
      @mouseover="hoverOn"
      @mouseleave="hoverOff"
      >
        <img 
        :src="img + element.poster_path" 
        class="card-image"
        v-if="hover == false">
        <div class="card-hover" v-if="hover">
            <div>Titolo originale: {{ element.original_title }}</div>
            <div>
                Lingua: {{ element.original_language }}
                <img :src="isLanguage(element)" alt="">
            </div>
            <div>Titolo: {{ element.title }}</div>
            <div>Voto: {{ element.vote_average }}/10</div>
        </div>
      </div>
      <!-- <div 
      class="series-card text-center"
      v-for="(element, index) in cardSeriesList"
      :key="index"
      >
        <div>Titolo originale: {{ element.original_title }}</div>
        <div>
            Lingua: {{ element.original_language }}
            <img :src="isLanguage(element)" alt="">
        </div>
        <div>Titolo: {{ element.title }}</div>
        <div>Voto: {{ element.vote_average }}/10</div>
      </div> -->
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
            franciaFlag: require("../assets/img/francia-flag.jpg"),
            globalFlag: require("../assets/img/global.jpg"),
            img: "http://image.tmdb.org/t/p/w342/",
            hover: false
        };
    },
    props: {
        cardMovieList: Array,
        cardSeriesList: Array,
    },
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
            } else {
                return this.globalFlag;
            }
        },
        hoverOn() {
            this.hover = true
        },
        hoverOff() {
            this.hover = false
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
.movie-card,
.series-card {
    width: calc(100% / 4 - 20px);
    height: 400px;
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

    .card-image {
        width: 100%;
        height: 400px;
    } 
}



</style>