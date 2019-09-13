<template lang="html">
  <div>
    <h1>Studio Ghibli Films</h1>
    <div class="main-container">
      <film-filter-form :films="films" />
    </div>
    <div class="filmDetail">
      <!-- <films-list :films="films"></films-list> -->
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

    body {

      font-family: sans-serif;
    }
    h1 {
      text-align: center;
      color: #333;
      font-family: sans-serif;
    }
    .main-container {
      display: flex;
      justify-content: space-between;
      width: 80%;
      margin: 0 auto;
      border:1px solid red;
    }
    .filmDetail {
      margin-left:10%;
    }

  </style>
