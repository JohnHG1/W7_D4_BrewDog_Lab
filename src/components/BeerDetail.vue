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

img {
  /* width: inherit; */
  width: 3em;
  position: center;
}

.beer-detail {
  text-align:inherit;
  border: 1.2px dotted;
  border-radius: 2em;
  width: 60%;
  position:inherit;
  right: 4;
  padding: 1.2em 1em 1.1em 1em;
  background-color: grey;
  font-size: 1.2em;
  margin-right: 1em;
  font-weight: bold;
}

h3 {
  font-size: 1.5em;
  text-decoration: underline;
  padding-bottom: 0.3em;
}

/*
div {
    max-width: 33%;
  }
  img {
    max-height: 25%;
    max-width: 25%;
  } */

</style>
