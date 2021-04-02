<template>
  <div class="wrapper">
    <div
      class="carousel"
      :style="{ 'margin-left': '-' + 100 * currentSlideIndex + '%' }"
    >
      <carousel-item
        v-for="item in carousel_data"
        :key="item.id"
        :item_data="item"
      />
    </div>
    <button @click="prevSlide">Назад</button>
    <button @click="nextSlide">Впёред</button>
  </div>
</template>

<script>
import carouselItem from "./carousel-item";

export default {
  name: "carousel",
  data() {
    return {
      currentSlideIndex: 0,
    };
  },
  components: {
    carouselItem,
  },
  props: {
    carousel_data: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    prevSlide() {
      if (this.currentSlideIndex > 0) {
        this.currentSlideIndex--;
      }
    },
    nextSlide() {
      if (this.currentSlideIndex >= this.carousel_data.length - 1) {
        this.currentSlideIndex = 0;
      } else {
        this.currentSlideIndex++;
      }
    },
  },
  mounted() {
    if (this.interval > 0) {
      let vm = this;
      setInterval(function () {
        vm.nextSlide();
      }, vm.interval);
    }
  },
};
</script>

<style lang = "scss" scope>
.wrapper {
  max-width: 300px;
  overflow: hidden;
  margin: 0 auto;
}

.carousel {
  display: flex;
  transition: all ease 0.5s;
}
</style>