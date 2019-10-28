<template lang="html">
  <div v-if="film" id="filmDetail">
    <div id="detailWrapper">

      <h2>{{film.name}}</h2>
        <p><span>Description:</span>: {{film.description}}</p>
        <p><span>Director:</span>: {{film.director}}</p>
        <p><span>Release Date:</span>: {{film.release_date}}</p>

    </div>
  </div>

</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'film-detail',
  data(){
    return{
      film: null
    }
  },
  mounted(){
    eventBus.$on('film-selected', (film) => {
      this.film = film
    })
  }
}
</script>

<style lang="css" scoped>
</style>
