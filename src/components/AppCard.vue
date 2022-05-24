<template>
      <div 
      class="movie-card p-3"
      @mouseover="hoverOn"
      @mouseleave="hoverOff"
      >
        <img 
        :src="img + card.poster_path" 
        class="card-image"
        v-if="hover == false">
        <div class="card-hover" v-if="hover">
            <div>Titolo originale: {{ card.original_title }}</div>
            <div>
                Lingua: {{ card.original_language }}
                <img :src="isLanguage(card)" alt="">
            </div>
            <div>Titolo: {{ card.title }}</div>
            <div>Voto: {{ card.vote_average }}/10</div>
            <div>Overview: {{ card.overview }}</div>
        </div>
      </div>
</template>

<script>
export default {
    name: "AppCard",
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
        card: Object,
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
.movie-card {
    width: calc(100% / 4);
    height: 400px;
    margin: 1rem 0;
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
        border-radius: 0;
    } 
}

.movie-card:hover {
    border: 4px solid white;
}


</style>