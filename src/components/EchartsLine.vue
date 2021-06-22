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
            text: "分数折线图",
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
            data: ["2016上半年", "2016下半年", "2017上半年",],
          },
          yAxis: {
            type: "value",
          },
          series: [
            {
              name: "数学",
              type: "line",
              stack: "平均",
              data: [120, 132, 101,],
            },
            {
              name: "语文",
              type: "line",
              stack: "平均",
              data: [110, 122, 191,],
            },
            {
              name: "英语",
              type: "line",
              stack: "平均",
              data: [130, 132, 101,],
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