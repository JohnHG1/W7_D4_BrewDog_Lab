<template lang="html">
  <div>
    <input v-model="beer.isFavourite" type="checkbox" >
    <li @click="handleClick">{{beer.name}}</li>
</div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-component',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('beer-selected', this.beer);
    }
  }
}
</script>

<style lang="css" scoped>



li {
    border: 1.7px dotted;
    border-radius: 4em;
    /* width: 100%; */
    margin: 1em 1.6em 1em 1.6em;
    list-style: none;
    background-color: grey;
    padding: 0.5em 0.5em;
    font-size: 1.1em;
    text-align: center;
    font-weight: bold;
    cursor: pointer;
  }

  li:hover {
    background-color: gold;
  }




</style>
