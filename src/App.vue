<template lang="html">
  <div id="app">
    <h1>STUDIO GHIBLI FILMS</h1>
      <film-filter-form :filmData="filmData" />
      <film-detail />
  </div>

</template>

<script>

import {eventBus} from "@/main.js"
import FilmFilterForm from './components/FilmFilterForm.vue'
import FilmDetail from './components/FilmDetail.vue'

export default {
  name: "app",
  components: {
    "film-filter-form": FilmFilterForm,
    "film-detail": FilmDetail
  },
  data(){
    return{
      filmData: null,
      filmTitle: null,
      filmReleaseDate: null,
    }
  },
  mounted(){
    fetch("https://ghibliapi.herokuapp.com/films")
    .then(response => response.json())
    .then(json => {
      this.filmData = json
      this.filmTitle = json.title
      this.filmReleaseDate = json.release_date
    })
  }
};
methods: {

};
</script>

<style lang="css">
body {
  background-color: salmon;
}
#app {
  font-family: 'timesnewroman';
  text-align: center;
  background-color: salmon;
}
</style>
