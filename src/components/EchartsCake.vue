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
            text: "优秀表",
            subtext: "纯属虚构",
            left: "center",
          },
          tooltip: {
            trigger: "item",
          },
          legend: {
            orient: "vertical",
            left: "left",
          },
          // 数据库成绩数据重复太多，图展现不好，这里就采用的是固定的数据，为了展示较好的效果
          series: [
            {
              name: "总分",
              type: "pie",
              radius: "50%",
              data: [
                { value: 300, name: "王小帅" },
                { value: 425, name: "王小天" },
                { value: 580, name: "王小来" },
                { value: 484, name: "王小飞" },
                { value: 200, name: "王小虎" },
              ],
              emphasis: {
                itemStyle: {
                  shadowBlur: 10,
                  shadowOffsetX: 0,
                  shadowColor: "rgba(0, 0, 0, 0.5)",
                },
              },
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