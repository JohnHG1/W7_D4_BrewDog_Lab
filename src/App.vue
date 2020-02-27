<template>
  <div id="app">
    <h1>Beer List</h1>
    <div class="container">
      <beer-detail :beer='selectedBeer'></beer-detail>
      <beers-list :beers='beers'></beers-list>
    </div>
  </div>
</template>

<script>
import BeersList from './components/BeersList.vue';
import BeerDetail from './components/BeerDetail.vue';
import {eventBus} from './main.js'

export default {
  name: 'app',
  data() {
    return {
      beers: [],
      selectedBeer: null
    }
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
