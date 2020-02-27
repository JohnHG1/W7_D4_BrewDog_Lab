<template lang="html">
  <li @click="handleClick">{{beer.name}}</li>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-component',
  props: ['beer'],
  methods: {
    handleClick(){
      eventBus.$emit('beer-selected',this.beer);
    }
  }
}
</script>

<style lang="css" scoped>


  li {
    border: 1.2px dotted;
    border-radius: 6em;
    width: 40%;
    margin: 1em 3em 1em 4em;
    list-style: none;
    background-color: lightgreen;
    padding: 0.5em 0em;
    font-size: 1.2em;
    cursor: pointer;
  }

  li:hover {
    background-color: gold;
  }


</style>
