<script lang="ts" setup>
import { onMounted, ref } from 'vue';

import {
EchartsUI, useEcharts, type EchartsUIType
} from '@vben/plugins/echarts';

const chartRef = ref<EchartsUIType>();
const { renderEcharts } = useEcharts(chartRef);

onMounted(() => {
  renderEcharts({
    tooltip: {
      trigger: 'axis',
      axisPointer: {
        type: 'shadow'
      }
    },
    legend: {},
    grid: {
      left: '3%',
      right: '4%',
      bottom: '3%',
      containLabel: true
    },
    xAxis: {
      type: 'value',
      boundaryGap: [0, 0.01],
      axisLabel: {
        formatter: '{value}万'
      },
    },
    yAxis: {
      type: 'category',

      data: ['美国', '英国', '土耳其', '印度', '俄罗斯', '菲律宾', '伊朗', '马来西亚']
    },
    series: [
      {
        // name: '2024',
        type: 'bar',
        data: [{
          value: 3.2,
          itemStyle: {
            color: '#219D9F'
          }
        }, {
          value: 2.1,
          itemStyle: {
            color: '#219D9F'
          }
        }, {
          value: 1.2,
          itemStyle: {
            color: '#219D9F'
          }
        }, {
          value: 3.3,
          itemStyle: {
            color: '#219D9F'
          }
        }, {
          value: 2.2,
          itemStyle: {
            color: '#219D9F'
          }
        }, {
          value: 1.1,
          itemStyle: {
            color: '#219D9F'
          }
        }, {
          value: 5.5,
          itemStyle: {
            color: '#F4BC75'
          }
        }, {
          value: 2.3,
          itemStyle: {
            color: '#F4BC75'
          }
        },],
        itemStyle: {
          color: function () {
            return ['#09111c', '#09121c', '#09131c']
          }
        }
      },
      // {
      //   name: '2012',
      //   type: 'bar',
      //   data: [19325, 23438, 31000, 121594, 134141, 681807]
      // }
    ]
  });
});
</script>

<template>
  <EchartsUI ref="chartRef" style="width: 400px; height: 400px;" />
</template>
