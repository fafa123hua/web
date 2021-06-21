<template>
  <div class="home">
    <!-- 轮播图 -->
    <div class="cartogram">
      <ms-carousel msg="Welcome to Your Vue.js App" />
    </div>
    <!-- 数据图 -->
    <div class="echarts">
      <ms-echarts msg="Welcome to Your Vue.js App" />
    </div>
    <!-- 返回键 -->
    <ms-backtop msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import Carousel from "@/components/Carousel.vue";
import Echarts from "@/components/Echarts.vue";
import Backtop from "@/components/Backtop.vue";

export default {
  name: "Home",
  components: {
    msCarousel: Carousel,
    msEcharts: Echarts,
    msBacktop: Backtop,
  },
};
</script>

<style lang="less">
.home {
  width: 100%;
  height: 100%;
}
.echarts {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  height: 50%;
}
</style>