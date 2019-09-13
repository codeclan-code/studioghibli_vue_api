<template lang="html">
  <li v-on:click="handleClick">{{film.title}}</li>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: 'list-component',
  props: ['film'],
  methods: {
    handleClick(){
      eventBus.$emit('film-selected', this.film)
    }
  }
}
</script>

<style lang="css" scoped>
li {
  /* list-style-type: none; */
  display: block;
  background: #fff;
  font-size: 16px;
  margin: 5px 0;
  padding: 5px;
  cursor: pointer;
  color: #555;
  transition: 0.1s all ease-in;
  border-radius: 3px;
  color:red;
  width:auto;
  font-family: sans-serif;
}

li:hover {
  background: #dbe8ff;
  color: #222;
}
</style>
