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
            <div>
                <span>Titolo originale:</span> 
                {{ cardOriginalTitle }}
            </div>
            <div>
                <span>Lingua:</span>
                {{ card.original_language }}
                <img :src="isLanguage(card)" alt="">
            </div>
            <div>
                <span>Titolo:</span> 
                {{ cardTitle }} 
            </div>
            <div>
                <span>Voto:</span> 
                <span
                 v-for="( index) in convertVote(card.vote_average)"
                :key="index"
                class="star">
                    <i class="fa-solid fa-star"></i>
                </span>
                <span
                v-for="( index) in 5 - convertVote(card.vote_average)"
                :key="index + 10"
                class="star">
                    <i class="fa-regular fa-star"></i>
                </span>
            </div>
            <div>
                <span>Overview:</span> 
                {{ card.overview }}
            </div>
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
    computed: {
        cardTitle() {
            return this.card.title ? this.card.title : this.card.name;
        },
        cardOriginalTitle() {
            return this.card.original_title ? this.card.original_title : this.card.original_name;
        }
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
        },
        convertVote(vote) {
            const convertedVote = vote / 2;
            const roundedVote = Math.ceil(convertedVote);
            return roundedVote;
        },
    }
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.movie-card {
    width: calc(100% / 4);
    height: 400px;
    margin: 1rem 0;
    color: white;
    font-size: .8rem;
    overflow-y: scroll;

    img {
        width: 25px;
        height: 15px;
    }

    .card-image {
        width: 100%;
        height: 400px;
        border-radius: 0;
    } 

    span {
        font-weight: bold;
        margin-right: .2rem;
    }
}

.movie-card:hover {
    border: 4px solid white;
}

.star i {
    color: $brand-star-color;
}


</style>