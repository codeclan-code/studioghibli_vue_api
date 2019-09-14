<template lang="html">
  <div>
    <h1>Studio Ghibli Films</h1>
    <div class="main-container">
      <film-filter-form :films="films" />
    </div>
    <div class="filmDetail">
      <film-detail :film="selectedFilm"></film-detail>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'

import FilmDetail from './components/FilmDetail.vue'
import FilmsList from './components/FilmsList.vue'
import FilmFilterForm from './components/FilmFilterForm.vue'

export default {
  data(){
    return {
      films: [],
      selectedFilm: null ,
      selectedPeople: null   }
    },
    components: {
      "film-filter-form": FilmFilterForm,
      "films-list": FilmsList,
      "film-detail": FilmDetail
    },
    mounted(){
      fetch('https://ghibliapi.herokuapp.com/films')
      .then(res => res.json())
      .then(films => this.films = films)

      fetch('https://ghibliapi.herokuapp.com/people')
      .then(res => res.json())
      .then(people => this.people = people)

      eventBus.$on('film-selected', (film) => {
        this.selectedFilm = film
      }),
      eventBus.$on('people-selected', (people) => {
        this.selectedPeople = people
      })
    }
  }
  </script>

  <style lang="css" scoped>

  </style>
