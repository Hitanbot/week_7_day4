<template lang="html">
  <div >
    <li >{{beer.name}}</li>
    <button v-on:click="removeFromFavourites">Remove Favorite</button>
  </div>

</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'list-item',
  props: ['beer'],
  methods: {
    removeFromFavourites(){
      eventBus.$emit('beer', this.beer)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
