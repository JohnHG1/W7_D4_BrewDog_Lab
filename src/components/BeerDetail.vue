<template lang="html">
  <div class="beer-detail"v-if="beer">
    <h3>{{beer.name}}</h3>
    <p><b>Desc:</b> {{beer.description}}</p>
      <p><b>Abv:</b> {{beer.abv}}</p>
        <img :src="beer.image_url" alt="">
  </div>
</template>

<script>
export default {
  name: 'beer-detail',
  props: ['beer']
}
</script>

<style lang="css" scoped>

div {
    max-width: 33%;
  }
  img {
    max-height: 25%;
    max-width: 25%;
  }

</style>
