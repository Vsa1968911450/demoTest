<script lang="ts" setup>
import { onMounted, ref } from 'vue';

import {
EchartsUI, useEcharts, type EchartsUIType
} from '@vben/plugins/echarts';
const props = defineProps({
  count: {
    type: Number,
    default: 0
  },
  name: {
    type: String,
    default: ''
  },
  color:{
    type: Array,
    default: []
  }
});
const chartRef = ref<EchartsUIType>();
const { renderEcharts } = useEcharts(chartRef);
console.log(props.color);

onMounted(() => {
  renderEcharts({
    legend: {
      bottom: '2%',
      left: 'center',
      show: false
    },
    title: {
      text: props.count,
      left: 'center',
      top: '38%',
      textStyle: {
        fontSize: 12,
        align: 'center'
      },
    },
    series: [
      {
        animationDelay() {
          return Math.random() * 100;
        },
        avoidLabelOverlap: false,
        color: props.color,
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
  <EchartsUI ref="chartRef" style="width: 80px; height: 80px;" />
</template>
