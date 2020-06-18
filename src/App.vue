<template>
  <div>

  <h1>Brewdog Beers</h1>
    <div class="main-container">
      <beers-select :beers='beers'></beers-select>
      <beer-detail :beer='selectedBeer'></beer-detail>
      <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites">Add Beer to Favorites</button>
      <h2>Favorites</h2>
      <beers-list :beers='favouriteBeers'></beers-list>
    </div>
  </div>
</template>

<script>
import BeersSelect from './components/BeersSelect.vue';
import BeerDetail from './components/BeerDetail.vue';
import BeersList from './components/BeersList.vue';
import { eventBus } from './main.js';

export default {
  name: 'App',
  data(){
  return {
    beers: [],
    selectedBeer: null,
    favouriteBeers: []
    };
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
    this.selectedBeer = beer;
    console.log(beer)
  })
  },
  methods:{
  addToFavourites: function(){
        this.favouriteBeers.push(this.selectedBeer)
      }
    },
  components: {
    'beers-select': BeersSelect,
    'beer-detail': BeerDetail,
    'beers-list': BeersList
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
