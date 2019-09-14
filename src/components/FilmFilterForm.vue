<template lang="html">
  <div class="searchForm">
    <form v-on:submit.prevent>
      <div class="inputSearch">
        <input type="text" v-model="search" placeholder="search for a film..." v-on:keyup="searchForFilm">
      </div>
      <div class="selectSearch">
        <select v-on:change="handleSelect" v-model="selectedFilm">
          <option disabled value="Select a film" selected>Select a film...</option>
          <option v-for="film in films" :value="film">{{film.title}}</option>
        </select>
      </div>
    </form>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: "film-filter-form",
  data(){
    return {
      "search": "",
      "selectedFilm": {},
    }
  },
  props: ["films"],
  methods: {
    searchForFilm(){
      let foundFilm = this.films.find((film) => {
        return film.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedFilm = foundFilm

      eventBus.$emit('film-selected', this.selectedFilm)
    },
    handleSelect(){
      this.search = ""
      eventBus.$emit('film-selected', this.selectedFilm)
    }
  }
}
</script>

<style lang="css" scoped>
.searchForm{
  margin: 0 auto;
  margin-bottom:5px;
  text-align: center;
}
.inputSearch {
  margin:10px;
}
.selectSearch {
  margin:10px;
}
select, input[type="text"]
{
  font-size: 16px;
}
</style>
