<template>
  <div class="image-container">
    <h2>{{ title }}</h2>
    <img :src="imageUrl" :alt="altText" /> <!-- v-bind for src and alt -->
  </div>
</template>

<script>
export default {
  props: {
    imageUrl: {
      type: String,
      required: true,
    },
    altText: {
      type: String,
      default: 'Image',
    },
  },

};
</script>

<style>
.image-container {
    display:flex;
    justify-content: center;
    align-items: center;
    padding: 0px;
    margin: 0px;
}

img {
  width: 100%;
  height: auto;
  max-height: 250px;
}
@media (min-width: 800px) {
  img {
    max-width: 100%;
    max-height: 250px;
    background-color: black;
  }
}
</style>
