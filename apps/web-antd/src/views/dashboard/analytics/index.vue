<template>
  <div class="test-full-screen p-5 flex">
    <div>
      <!-- 左侧 -->
      <div class="top-left-titles">
        <!-- 左侧图片 -->
        <img class="top-left-img" src="../../../accets/test/a.png" alt="" />
        <div>
          <p class="top-left-desc">CONVID-19</p>
          <p class="top-left-subtitle">这是一个副标题内容</p>
        </div>
      </div>
      <!-- 左侧中间统计数据 -->
      <div class="middle-left-statics">
        <p class="middle-left-left-font">
          新增人数数量<span class="middle-left-right-font">
            截止至:2024/10/18 23:50</span>
        </p>
      </div>
      <div class="middle-left-bg flex">
        <div class="middle-left-definiteDiagnosis" v-for="item in definiteDiagnosisList" :key="item.name">
          <p class="middle-left-definiteDiagnosis-name">{{ item.name }}</p>
          <p class="middle-left-definiteDiagnosis-number">{{ item.number }}</p>
        </div>
      </div>
      <div class="middle-left-statics">
        <p class="middle-left-left-font">
          国内疫情<span class="middle-left-right-font">
            截止至:2024/10/18 23:50</span>
        </p>
      </div>
      <div class="middle-left-bg flex flex-wrap">
        <div class="middle-left-china" v-for="item in chinaDefiniteDiagnosisList" :key="item.name">
          <p class="middle-left-china-name">{{ item.name }}</p>
          <p class="font-titles" :class="[
            item.name === '国内现有确诊' || item.name === '无症状'
              ? 'middle-left-china-numberYellow'
              : 'middle-left-china-number',
          ]">
            {{ item.number }}
          </p>
          <p class="middle-left-china-compare">
            较昨日<span :class="[
              item.name === '国内现有确诊' || item.name === '无症状'
                ? 'middle-left-china-numberYellow'
                : 'middle-left-china-number']" v-if="item.isAdd">+ {{ item.number }}</span>
            <span :class="[
              item.name === '国内现有确诊' || item.name === '无症状'
                ? 'middle-left-china-numberYellow'
                : 'middle-left-china-number']" v-else>- {{ item.number }}</span>
          </p>
        </div>
      </div>
      <!-- 左下角 -->
      <div class="middle-left-statics">
        <p class="middle-left-left-font">实时播报</p>
        <div class="middle-bottom-bg">
          <div class="middle-bottom-news" v-for="item in list" :key="item.title">
            <p class="middle-bottom-news-time">{{ item.time }}</p>
            <p class="middle-bottom-news-title">{{ item.title }}</p>
            <a-tooltip placement="top">
              <template #title>
                <span>{{ item.desc }}</span>
              </template>
              <p class="middle-bottom-news-desc">{{ item.desc }}</p>
            </a-tooltip>
          </div>
        </div>
      </div>
    </div>
    <!-- 中 -->
    <div class="middle-bg">
      <div class="middle-top-bg">
        <Tabs centered="true" v-model:activeKey="activeKey" :tabBarStyle="{ borderBottom: 'unset' }">
          <TabPane key="1" tab="数据统计"></TabPane>
          <TabPane key="2" tab="应急资源"></TabPane>
          <TabPane key="3" tab="数据检测"></TabPane>
        </Tabs>
      </div>
      <div class="flex">
        <div>
          <!-- 入境防疫信息 -->
          <div class="middle-statics">
            <p class="middle-left-font">
              入境防疫信息<span class="middle-right-font">
                截止至:2024/10/18 23:50</span>
            </p>
            <div class="middle-bg flex">
              <AnalyticsVisitsSource />
              <div class="flex ana-bg">
                <div class="middle-top-desc-bg">
                  <img class="img-width" src="../../../accets/test/blue.png" alt="">
                  <div>
                    <p class="ml-1 middle-title-font">入境总人数</p>
                    <p class="middle-font">Number of diagnosis</p>
                    <p class="middle-bottom-title">6450</p>
                  </div>
                </div>
                <div class="middle-top-desc-bg">
                  <img class="img-width" src="../../../accets/test/red.png" alt="">
                  <div>
                    <p class="ml-1 middle-title-font">入境确诊人数</p>
                    <p class="middle-font">Number of diagnosis</p>
                    <p class="middle-bottom-title">6350</p>
                  </div>
                </div>
                <div class="middle-bottom-desc-bg">
                  <div>
                    <p class="ml-1 middle-title-font">245</p>
                    <p class="middle-font">入境核酸点</p>
                  </div>
                </div>
                <div class="middle-bottom-desc-bg">
                  <div>
                    <p class="ml-1 middle-title-font">45</p>
                    <p class="middle-font">发热隔离点</p>
                  </div>
                </div>
                <div class="middle-bottom-desc-bg">
                  <div>
                    <p class="ml-1 middle-title-font">5</p>
                    <p class="middle-font">高危隔离点</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div>
          <!-- 入境人员趋势 -->
          <div class="middle-statics">
            <p class="middle-left-font">
              入境人员趋势<span class="middle-right-font">
                截止至:2024/10/18 23:50</span>
            </p>
            <div class="middle-bg flex">
              <AnalyticsTrends class="mt-3" />
            </div>
          </div>
        </div>

      </div>
    </div>
    <!-- 右 -->
    <div class="right-bg">
      <div class="flex">
        <img class="right-img" src="../../../accets/test/rain.png" alt="">
        <p class="right-top-title">14:53:45</p>
        <div class="ml-5">
          <p class="right-top-des">Date</p>
          <p>2024.10.24</p>
        </div>
      </div>
      <div class="right-statics">
        <p class="right-font">
          新增国家TOP10<span class="right-font-desc">
            截止至:2024/10/18 23:50</span>
        </p>
      </div>
      <div class="right-middle-bg">
        <AnalyticsNation />
      </div>
      <div class="right-statics mt-4">
        <p class="right-font">
          年龄分布
        </p>
      </div>
      <div class="right-bottom-bg">
        <AnalyticsPie />
        <p class="right-font-pos">100</p>
        <div class="flex flex-wrap">
          <div class="right-bottom-width" v-for="item in yearList">
            <div class="flex">
              <div>
                <p class="ml-4 mt-4"> <span class="square"
                    :class="item.name === '55岁以上' ? 'green' : item.name === '40-49岁' ? 'blue' : item.name === '30-39岁' ? 'old-green' : 'orange'"></span>
                  <span class="ml-2 mt-4"> {{
                    item.name }}</span>
                </p>
                <p class="ml-8">{{ item.percent }}</p>
              </div>
              <analyticsBotPie :count="item.value" :name="item.name" :color="item.color" />
            </div>

          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { TabPane, Tabs } from 'ant-design-vue';

import AnalyticsTrends from './analytics-trends.vue';

import AnalyticsNation from './analytics-nation.vue';


import AnalyticsPie from './analytics-pie.vue';

import { ref } from 'vue';

import analyticsBotPie from './analytics-bot-pie.vue';

import AnalyticsVisitsSource from './analytics-visits-source.vue';

interface definiteDiagnosisListType {
  name: String;
  number: Number;
}
interface chinaDefiniteDiagnosisListType {
  name: String;
  number: Number;
  isAdd: Boolean;
  addNum: Number;
}
interface newList {
  time: String;
  title: String;
  desc: String;
}
interface yearListType {
  name: string,
  value: number,
  percent: string,
  color: any
}
const yearList: yearListType[] = [
  {
    name: "55岁以上",
    value: 10,
    percent: '10%',
    color: ['#1BF3D8', '#0E665F'],
  },
  {
    name: "40-49岁",
    value: 20,
    percent: '20%',
    color: ['#3960EE', '#192752'],
  },
  {
    name: "30-39岁",
    value: 30,
    percent: '30%',
    color: ['#43B072', '#173D2B'],
  },
  {
    name: "30岁以下",
    value: 40,
    percent: '40%',
    color: ['#DFB636', '#4E451D'],
  },
];
const definiteDiagnosisList: definiteDiagnosisListType[] = [
  { name: '国内新增确诊', number: 1234 },
  { name: '国外新增确诊', number: 1234 },
];
const chinaDefiniteDiagnosisList: chinaDefiniteDiagnosisListType[] = [
  { name: '国内现有确诊', number: 2632, isAdd: true, addNum: 12 },
  { name: '无症状', number: 1234, isAdd: true, addNum: 12 },
  { name: '现有疑似', number: 1234, isAdd: true, addNum: 12 },
  { name: '累计确诊', number: 1234, isAdd: true, addNum: 12 },
  { name: '境外输入', number: 1234, isAdd: true, addNum: 12 },
  { name: '现有重症', number: 1234, isAdd: true, addNum: 12 },
];
const list: newList[] = [
  {
    time: '2024/10/22 18:51',
    title: '香港新增新冠肺炎',
    desc: '香港特区政府卫生署卫生防护中心21日公布，截至当日零时，香港新增一例新增新冠肺炎案例',
  },
  {
    time: '2024/10/22 18:51',
    title: '疫情形势越发严峻,越南政府紧急求援',
    desc: '据悉，此前越南政府制定了防疫政策，计划于9月15日前控制胡明市的疫情局势，...',
  },
];
const activeKey = ref('1');
</script>
<style lang="scss">
.test-full-screen {
  width: 1920px;
  height: 1080px;
  background: url('../../../accets/test/wind.png');

  .top-left-titles {
    display: flex;
    width: 321px;
    height: 63px;
    margin-left: 18px;
  }

  .top-left-img {
    width: 46px;
    height: 54px;
  }

  .top-left-desc {
    font-size: 30px;
    line-height: 30px;
  }

  .top-left-subtitle {
    margin-top: 3px;
    font-size: 20px;
    line-height: 20px;
  }

  .middle-left-statics {
    width: 410px;
    height: 44px;
    margin-top: 30px;
    margin-left: 18px;
    background: url('../../../accets/test/picback.png');
    background-position: center center;
    background-size: cover;
    background-repeat: no-repeat;
    border: 1px solid #000;
    border-bottom: 1px solid #017e6e;
  }

  .middle-left-left-font {
    margin-top: 10px;
    margin-left: 40px;
    font-size: 16px;
  }

  .middle-left-right-font {
    margin-left: 105px;
    font-size: 14px;
    color: #828587;
  }

  .middle-left-bg {
    width: 410px;
    margin-left: 18px;
    background-color: #09131c;
  }

  .middle-bottom-bg {
    width: 410px;
    height: 280px;
    margin-top: 10px;
    background-color: #09131c;
  }

  .middle-left-definiteDiagnosis {
    width: 197px;
    margin-left: 18px;
  }

  .middle-bottom-news {
    margin-top: 10px;
  }

  .middle-left-definiteDiagnosis-name {
    margin-top: 10px;
    font-size: 16px;
  }

  .middle-left-definiteDiagnosis-number {
    margin-top: 10px;
    margin-bottom: 10px;
    font-size: 26px;
    color: #19fcde;
  }

  .middle-left-china {
    width: 120px;
  }

  .middle-left-china:nth-child(3n + 1) {
    margin-left: 18px;
  }

  .middle-left-china-name {
    margin-top: 14px;
    font-size: 16px;
  }

  .font-titles {
    font-size: 26px;
  }

  .font-desc {
    font-size: 22px;
  }

  .middle-left-china-number {
    margin-top: 10px;
    color: #19fcde;
  }

  .middle-left-china-numberYellow {
    margin-top: 10px;
    color: #e7a04b;
  }

  .middle-left-china-compare {
    margin-top: 10px;
    margin-bottom: 10px;
    font-size: 16px;
  }

  .middle-bottom-news-time {
    margin-top: 15px;
    margin-left: 18px;
    font-size: 18px;
  }

  .middle-bottom-news-title {
    width: 410px;
    margin-top: 10px;
    margin-left: 18px;
    font-size: 22px;
    line-height: 22px;
    background: url('../../../accets/test/back.png') no-repeat;
    background-size: 400px;
  }

  .middle-bottom-news-desc {
    margin-top: 10px;
    margin-bottom: 13px;
    margin-left: 18px;
    font-size: 16px;
    color: #828587;
  }

  .middle-bg {
    .middle-top-bg {
      background-image: url('../../../accets/test/ball.png');
      height: 640px;
      width: 1000px;
      background-position: center center;
      background-size: cover;
      background-repeat: no-repeat;
      margin-left: 20px;
    }

    .middle-statics {
      width: 490px;
      height: 44px;
      margin-top: 30px;
      margin-left: 18px;
      background: url('../../../accets/test/picback.png');
      background-position: center center;
      background-size: cover;
      background-repeat: no-repeat;
      border: 1px solid #000;
      border-bottom: 1px solid #017e6e;
    }

    .middle-left-font {
      margin-top: 10px;
      margin-left: 40px;
      font-size: 16px;
    }

    .middle-bg {
      width: 490px;
      background-color: #09131c;
      height: 220px;
      margin-top: 10px;
    }

    .img-width {
      width: 16px;
      height: 30px;
      margin-top: 22px;
    }

    .middle-font {
      font-size: 12px;
      color: #828587;
    }

    .middle-title-font {
      font-size: 12px;
      margin-left: 3px;
      margin-top: 20px;
    }

    .middle-bottom-title {
      font-size: 28px;
      color: #19FCDE;
    }

    .ana-bg {
      height: 100px;
      width: 300px;
      flex-wrap: wrap;
    }

    .ana-bottom-bg {
      height: 80px;
    }

    .middle-top-desc-bg {
      width: 120px;
      display: flex;
    }

    .middle-bottom-desc-bg {
      width: 80px;
      margin-left: 10px;
    }

    .ant-tabs-nav {
      justify-content: center;
      align-items: center;
      display: flex;
    }

    .middle-right-font {
      margin-left: 165px;
      font-size: 14px;
      color: #828587;
    }
  }

  .right-bg {
    .right-img {
      width: 60px;
      height: 30px;
      margin-top: 10px;
      margin-left: 140px;
    }

    .right-top-title {
      color: white;
      font-size: 28px;
      margin-left: 20px;
    }

    .right-statics {
      width: 400px;
      height: 44px;
      margin-left: 28px;
      background: url('../../../accets/test/picback.png');
      background-position: center center;
      background-size: cover;
      background-repeat: no-repeat;
      border: 1px solid #000;
      border-bottom: 1px solid #017e6e;
    }

    .right-top-des {
      color: #828587;
    }

    .right-font {
      margin-left: 40px;
      margin-top: 14px;
    }

    .right-font-desc {
      margin-left: 100px;
      color: #828587;
    }

    .right-middle-bg {
      width: 400px;
      height: 390px;
      margin-left: 28px;
      background-color: #09131c;
    }
    .right-bottom-bg{
      width: 400px;
      height: 400px;
      margin-left: 28px;
      background-color: #09131c;
    }
    .right-font-pos {
      position: absolute;
      left: 1675px;
      top: 643px;
      font-size: 20px;
      z-index: 999;
    }

    .right-bottom-width {
      width: 200px;
    }

    .square {
      display: inline-block;
      width: 10px;
      height: 10px;
    }

    .green {
      background-color: #1BF3D8;
    }

    .blue {
      background-color: #3960EE;
    }

    .old-green {
      background-color: #43B072;
    }

    .orange {
      background-color: #DFB636;
    }
  }

  .ant-tabs .ant-tabs-tab.ant-tabs-tab-active .ant-tabs-tab-btn {
    color: white;
  }

  .ant-tabs .ant-tabs-tab-btn {
    color: #828587;
  }

  .ant-tabs-ink-bar {
    background-color: #14706C
  }
  .ant-tabs-top > .ant-tabs-nav::before {
    border-bottom: none;
  }
}
</style>
