<template>
  <div id="app">
    <div ref="chart" style="width: 100%; height: 376px"></div>
  </div>
</template>

<script>
export default {
  name: "App",
  mounted() {
    this.getEchartData();
  },
  methods: {
    getEchartData() {
      const chart = this.$refs.chart;
      if (chart) {
        const myChart = this.$myecharts.init(chart);
        const option = {
          title: {
            text: "折线图堆叠",
          },
          tooltip: {
            trigger: "axis",
          },
          legend: {
            data: ["数学", "语文", "英语"],
          },
          grid: {
            left: "3%",
            right: "4%",
            bottom: "3%",
            containLabel: true,
          },
          toolbox: {
            feature: {
              saveAsImage: {},
            },
          },
          xAxis: {
            type: "category",
            boundaryGap: false,
            data: ["周一", "周二", "周三", "周四", "周五", "周六", "周日"],
          },
          yAxis: {
            type: "value",
          },
          series: [
            {
              name: "数学",
              type: "line",
              stack: "总量",
              data: [120, 132, 101, 134, 90, 230, 210],
            },
            {
              name: "语文",
              type: "line",
              stack: "总量",
              data: [220, 182, 191, 234, 290, 330, 310],
            },
            {
              name: "英语",
              type: "line",
              stack: "总量",
              data: [150, 232, 201, 154, 190, 330, 410],
            },
          ],
        };
        myChart.setOption(option);
        window.addEventListener("resize", function () {
          myChart.resize();
        });
      }
      this.$on("hook:destroyed", () => {
        window.removeEventListener("resize", function () {
          myChart.resize();
        });
      });
    },
  },
};
</script>
<style>
</style>