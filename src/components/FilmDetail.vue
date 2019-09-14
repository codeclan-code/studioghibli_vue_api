<template lang="html">
  <div v-if="film" id="filmDetail">
    <div id="detailWrapper">
      <h2>{{film.title}}</h2>
      <div id="flexWrapper">
        <div id="left">
          <p><span>Release Date</span>: {{film.release_date}}</p>
          <p><span>Director</span>: {{film.director}}</p>
          <p><span>Producer</span>: {{film.producer}}</p>
          <p><span>Release Date</span>: {{film.release_date}}</p>
          <p><span v-bind:class= "film.rt_score < 50 ? 'red' : 'green'">RT Score (%): </span><span>{{ film.rt_score }}</span></p>
          <p><span>Description</span>: </p>
          <p class="description">{{film.description}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

import { eventBus } from '../main.js'

export default {
  name: 'film-detail',
  props: ['film']
}
</script>

<style lang="css" scoped>
.red{
  color:red;
}
.green {
  color:green;
}
#filmDetail {
  box-sizing: border-box;
  height: auto;
  xwidth: 75%;
  background: #ECF5FD;
  color: #222;
  padding: 10px;
  border: 1px solid #ccc;
  margin: 0 auto;
  margin-bottom:10px;
  border-radius:15px;
}

p span {
  font-weight: bold;
}

p.description {
  line-height: 120%;
}

h2 {
  font-size :200%;
}

</style>
