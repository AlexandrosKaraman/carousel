<template>
  <div class="carouselItem">
    <img :src="require('../assets/img/' + item_data.img)" />
  </div>
</template>

<script>
export default {
  name: "carouselItem",
  props: {
    item_data: {
      type: Object,
      default: () => {},
    },
  },
};
</script>

<style>
</style>