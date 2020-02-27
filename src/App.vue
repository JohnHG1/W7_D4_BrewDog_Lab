<template>
  <main>
    <div class="container">
      <h1>Beer List</h1>

    <div id="list">
      <beers-list :beers='beers'></beers-list>
    </div>

    <div id="detail">
      <beer-detail v-if="selectedBeer" :beer="selectedBeer"></beer-detail>
    </div>

    <div id="favourites">
      <h2>Favourite Beers</h2>
      <favourite-beers :beers="favouriteBeers"></favourite-beers>
    </div>
  </div>
  </main>
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
      selectedBeer: null,
    }
  },
  components: {
    "beers-list": BeersList,
    "beer-detail": BeerDetail,
    "favourite-beers": BeersList
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(data => this.beers = this.formatBeers(data))

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
  },

  computed: {
    favouriteBeers: function(){
      return this.beers.filter((beer) => {
        return beer.isFavourite;
      })
    }
  },
  methods: {
    formatBeers: function(beers){
      return beers.map((beer) => {
        beer['isFavourite'] = false;
        return beer;
      })
    }
  },
}
</script>


<style>



main {
  width: 100%;
  display: inline-flex;
  justify-content: space-between;
  align-content: center;
}
.container {
  width: 100%;
  display: flex;
  justify-content: space-between;
}
#list {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
#detail {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
  width: 65%;
}
#favourites {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
  width: 65%;
}


</style>
