<template>
  <div class="home">
    <!-- 轮播图 -->
    <div class="cartogram">
      <ms-carousel msg="Welcome to Your Vue.js App" />
    </div>
    <!-- 数据图 -->
    <!-- 饼图 -->
    <div class="echartscake">
      <ms-echarts-cake msg="Welcome to Your Vue.js App" />
    </div>
    <!-- 折线图 -->
    <div class="echartsline">
      <ms-echarts-line msg="Welcome to Your Vue.js App" />
    </div>
    <!-- 返回键 -->
    <ms-backtop msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import Carousel from "@/components/Carousel.vue";
import EchartsCake from "@/components/EchartsCake.vue";
import EchartsLine from "@/components/EchartsLine.vue";
import Backtop from "@/components/Backtop.vue";

export default {
  name: "Home",
  components: {
    msCarousel: Carousel,
    msEchartsCake: EchartsCake,
    msEchartsLine: EchartsLine,
    msBacktop: Backtop,
  },
};
</script>
0
<style lang="less">
.home {
  width: 100%;
  height: 100%;
}
.echartscake {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  height: 50%;
}
.echartsline{
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  width: 100%;
  height: 50%;
}
</style>