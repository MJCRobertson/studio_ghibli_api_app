<template lang="html">
  <form v-on:submit.prevent>
    <input type="text" v-model="search" placeholder="search for a film" v-on:keyup="searchForFilm">
    <select v-on:change="handleSelect" v-model="selectedFilm">
      <option disabled value="">Select A Film</option>
      <option v-for="film in filmData" :value="film">{{film.title}}</option>
    </select>
  </form>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: "film-filter-form",
  data(){
    return{
      "search": "",
      "selectedFilm": {}
    }
  },
  props: ["filmData"],
  methods: {
    searchForFilm(){
      let foundFilm = this.filmData.find((film) => {
    return film.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1
  })
  this.selectedFilm = foundFilm

  eventBus.$emit('film-selected', this.selectedFilm)
},
handleSelect(){
  this.search = ''
  eventBus.$emit('film-selected', this.selectedFilm)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
