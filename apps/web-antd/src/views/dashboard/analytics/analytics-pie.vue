<template>
  <div class="chart-container">
    <div class="chart" ref="chart"></div>
    <!-- 底座背景 -->
    <!-- <div class="bg"></div> -->
  </div>
</template>
 
<script>
import * as echarts from "echarts";
import "echarts-gl";
import { getPie3D, getParametricEquation } from './echarts'; //工具类js，页面路径自己修改

const color = ["#1BF3D8", "#3960EE", "#43B072", "#DFB636"];

export default {
  name: "chart",
  data () {
    return {
      optionData: [
        {
          name: "55岁以上",
          value: 176,
        },
        {
          name: "40-49岁",
          value: 288,
        },
        {
          name: "30-39岁",
          value: 88,
        },
        {
          name: "30岁以下",
          value: 78,
        },
      ],
      statusChart: null,
      option: {},
    };
  },
  created () {
    this.setLabel();
  },
  mounted () {
    this.initChart();

    //根据窗口变化自动调节图表大小
    const that = this;
    window.onresize = function () {
      that.changeSize();
    };
  },
  methods: {
    // 初始化label样式
    setLabel () {
      this.optionData.forEach((item, index) => {
        item.itemStyle = {
          color: color[index],
        };
        item.label = {
          normal: {
            show: true,
            color: color[index],
            position: 'right',
            offset: [0, 3],
            formatter: [
              "{d|{d}%}",
              "————",
              "{b|{b}}",
            ].join("\n"), // 用\n来换行
            rich: {
              b: {
                lineHeight: 25,
                align: "left",
                color: color[index],
              },
              c: {
                fontSize: 22,
                textShadowColor: "#1c90a6",
                textShadowOffsetX: 0,
                textShadowOffsetY: 2,
                textShadowBlur: 5,
                color: color[index],
              },
              d: {
                color: color[index],
                align: "left",
              },
            },
          },
        };
        item.labelLine = {
          show: false
          // normal: {
          //   length2: 30,
          //   lineStyle: {
          //     width: 1,
          //     color: color[index],
          //   },
          // },
        };
      });
    },
    // 图表初始化
    initChart () {
      this.statusChart = echarts.init(this.$refs.chart);
      // 传入数据生成 option, 构建3d饼状图, 参数工具文件已经备注的很详细
      this.option = getPie3D(this.optionData, 0.6, 180, 26, 18, 1);
      this.statusChart.setOption(this.option);
      // 是否需要label指引线，如果要就添加一个透明的2d饼状图并调整角度使得labelLine和3d的饼状图对齐，并再次setOption
      this.option.series.push({
        name: "年龄评价", //自己根据场景修改
        backgroundColor: "transparent",
          type: "pie",
          labelLine: {
            show: false,
          },
          startAngle: -40, // 起始角度，支持范围[0, 360]。
          clockwise: false, // 饼图的扇区是否是顺时针排布。上述这两项配置主要是为了对齐3d的样式
          radius: ["20%", "60%"],
          center: ["50%", "50%"],
          data: this.optionData,
          itemStyle: {
            opacity: 0, //这里必须是0，不然2d的图会覆盖在表面
          },
        });
      this.statusChart.setOption(this.option);
    },
    // 自适应宽高
    changeSize () {
      this.statusChart.resize();
    },
  },
};
</script>
 
<style lang='less' scoped>
.chart-container {
  // position: relative;
  width: 400px;
  height: 200px;

  .chart {
    z-index: 1;
  }

  .chart,
  .bg {
    width: 100%;
    height: 100%;
  }

  .bg {
    // position: absolute;
    // bottom: -10px;
    // left: 50%;
    // z-index: 0;
    height: calc(200 / 1080 * 100vh);
    width: calc(240 / 1920 * 100vw);
    background: no-repeat center;
    // background-image: url("~@/assets/imgs/piebg.png");
    background-size: 100% 100%;
    transform: translateX(-50%);
  }
}
</style>
