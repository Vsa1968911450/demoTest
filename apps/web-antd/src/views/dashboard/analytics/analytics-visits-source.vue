<script lang="ts" setup>
import { onMounted, ref } from 'vue';

import {
EchartsUI, useEcharts, type EchartsUIType
} from '@vben/plugins/echarts';

const chartRef = ref<EchartsUIType>();
const { renderEcharts } = useEcharts(chartRef);

onMounted(() => {
  renderEcharts({
    legend: {
      bottom: '2%',
      left: 'center',
      show: false
    },
    title: {
      text: '70%',
      subtext: '入境确诊占比',
      left: 'center',
      top: '40%',
      textStyle: {
        fontSize: 12,
        color: '#2BCAFF',
        align: 'center'
      },
    },
    series: [
      {
        animationDelay() {
          return Math.random() * 100;
        },
        avoidLabelOverlap: false,
        color: ['#19FCDE', '#343A3C'],
        data: [
          { name: '入境确诊占比', value: 7 },
          { name: '未入境确诊占比', value: 3 },
        ],
        emphasis: {
          label: {
            fontSize: '12',
            fontWeight: 'bold',
            show: false,
          },
        },
        itemStyle: {
          borderRadius: 10,
          borderWidth: 2,
        },
        label: {
          position: 'center',
          show: false,
        },
        labelLine: {
          show: false,
        },
        name: '入境确诊占比',
        radius: ['50%', '40%'],
        type: 'pie',
      },
    ],
    tooltip: {
      trigger: 'item',
    },
  });
});
</script>

<template>
  <EchartsUI ref="chartRef" style="width: 200px; height: 200px;" />
</template>
