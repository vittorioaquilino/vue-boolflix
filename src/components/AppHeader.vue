<template>
  <section class="ms_header d-flex px-4">
      <div class="ms_header-nav d-flex">
        <div class="ms_title fw-bold">boolflix</div>
        <ul class="header-menu">
            <li>Home</li>
            <li>Serie TV</li>
            <li>Film</li>
            <li>Originali Boolflix</li>
            <li>La mia lista</li>
        </ul>
      </div>
      <div class="ms_header-search">
         <input 
         type="text" 
         placeholder="cerca un film o una serie TV"
         class="px-4 text-center"
         v-model="searchWord">
        <button class="px-4" @click="$emit('searchEvents', searchWord)">cerca</button>
      </div>
  </section>
</template>

<script>
export default {
    name: "AppHeader",
    data() {
        return {
            searchWord: "",
        }
    },
}
</script>

<style lang="scss" scoped>
@import "../style/variables.scss";

.ms_header {
    justify-content: space-between;
    align-items: center;
    height: 100px;
    background-color: black;

    .ms_title {
        color: $brand-title-color;
        text-transform: uppercase;
        font-size: 1.5rem;
    }

    .ms_header-nav {
        align-items: center;

        .header-menu {
            list-style: none;

            li {
                display: inline-block;
                padding: 0 1rem;
                color: white;
                font-size: .8rem;
            }
        }
    }
    .ms_header-search {
        
        input {
            margin: 0 .7rem;  
            width: 300px;
            border: none;
        }

        button {
            border: none;
            cursor: pointer;
        }
    }
}
</style>