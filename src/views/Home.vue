<template>
  <div class="home">
    <ms-carousel msg="Welcome to Your Vue.js App" />
    <ms-echarts msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import Carousel from "@/components/Carousel.vue";
import Echarts from "@/components/Echarts.vue";

export default {
  name: "Home",
  components: {
    msCarousel: Carousel,
    msEcharts: Echarts,
  },
};
</script>

