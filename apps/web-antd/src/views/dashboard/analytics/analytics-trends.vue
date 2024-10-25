<script lang="ts" setup>
import { onMounted, ref } from 'vue';

import {
EchartsUI, useEcharts, type EchartsUIType
} from '@vben/plugins/echarts';

const chartRef = ref<EchartsUIType>();
const { renderEcharts } = useEcharts(chartRef);

onMounted(() => {
  renderEcharts({
    grid: {
      bottom: 0,
      containLabel: true,
      left: '1%',
      right: '1%',
      top: '2%',
    },
    series: [
      {
        areaStyle: {},
        data: [31, 22, 32, 44, 25, 46, 37, 38, 29, 40, 51],
        itemStyle: {
          color: '#0D484A',
        },
        smooth: true,
        type: 'line',
      },
      {
        areaStyle: {},
        data: [21, 22, 31, 24, 25, 36, 27, 8, 29, 10, 31],
        itemStyle: {
          color: '#0E2D46',
        },
        smooth: true,
        type: 'line',
      },
      {
        areaStyle: {},
        data: [12, 12, 21, 14, 22, 6, 27, 8, 29, 10, 31],
        itemStyle: {
          color: '#212E35',
        },
        smooth: true,
        type: 'line',
      },
      {
        areaStyle: {},
        data: [3, 3, 4, 11, 2, 6, 10, 8, 29, 10, 11],
        itemStyle: {
          color: '#8D9094',
        },
        smooth: false,
        type: 'line',
      },
    ],
    tooltip: {
      axisPointer: {
        lineStyle: {
          color: '#019680',
          width: 1,
        },
      },
      trigger: 'axis',
    },
    xAxis: {
      axisTick: {
        show: false,
      },
      boundaryGap: false,
      data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月'],
      splitLine: {
        lineStyle: {
          type: 'solid',
          width: 1,
        },
        show: true,
      },
      type: 'category',
    },
    yAxis: [
      {
        axisTick: {
          show: false,
        },
        splitArea: {
          show: true,
        },
        type: 'value',
      },
    ],
  });
});
</script>

<template>
  <EchartsUI ref="chartRef" style="width: 480px; height: 200px;" />
</template>
