<template lang="html">
  <div>
    <ul>
      <list-component v-for="(beer, index) in beers" :beer="beer"
      :key="index"></list-component>
    </ul>
  </div>

</template>

<script>
import ListComponent from './ListComponent.vue';

export default {
  name: 'beers-list',
  props: ['beers'],
  components: {
    "list-component": ListComponent
  }
}
</script>

<style lang="css" scoped>
</style>
