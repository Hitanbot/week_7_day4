<template lang="html">
  <div>
    <select @change=onChange() v-model="selectedBeer">
      <option v-for="(beer, index) in beers" :value="beer" :key="index">{{beer.name}}</option>
    </select>
  </div>

</template>

<script>
import { eventBus } from '../main.js';


export default {
  name: 'beers-select',
  props: ['beers','beer'],



  methods: {

  onChange(){
      eventBus.$emit('beer-selected', this.selectedBeer)

  }

  }


}
</script>
