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
          <p>{{film.description}}</p>
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
  /* box-sizing: border-box;
  height: auto;
  width: 75%;
  background: #eee;
  color: #222;
  padding: 10px;
  border: 1px solid #ccc; */
      margin: 0 auto;
}

#detailWrapper {
  /* box-sizing: border-box;
  background: #fff;
  padding: 10px;
  height: 100%;
  border-radius: 3px; */
    margin: 0 auto;
    border: 1px solid green;
    padding:10px;
    margin:10px;
}

#flexWrapper {
  display: flex;
  justify-content: space-between;
}

#left, #right {
  width: 95%;
}

#right img {
  width: 100%;
}

#left p:first-child {
  margin-top: 0;
}

h2 {
  margin: 10px 0 20px;
  padding: 0;
}

p span {
  font-weight: bold;
}

div {

  font-family: sans-serif;
}

</style>
