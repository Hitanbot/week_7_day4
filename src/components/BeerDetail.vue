<template lang="html">

  <div>
  <div v-if='beer'>
    <h3>{{beer.name}}</h3>
    <p>Description: {{beer.description}}</p>
    <p>First brewed in: {{beer.first_brewed}}</p>

    </div>
  </div>
</template>

<script>


export default {
  name: 'beer-detail',
  props: ['beer']
}

</script>

<style lang="css" scoped>
</style>
