<template>
  <div class="test-full-screen p-5">
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
          截止至:2024/10/18 23:50</span
        >
      </p>
    </div>
    <div class="middle-left-bg flex">
      <div
        class="middle-left-definiteDiagnosis"
        v-for="item in definiteDiagnosisList"
        :key="item.name"
      >
        <p class="middle-left-definiteDiagnosis-name">{{ item.name }}</p>
        <p class="middle-left-definiteDiagnosis-number">{{ item.number }}</p>
      </div>
    </div>
    <div class="middle-left-statics">
      <p class="middle-left-left-font">
        国内疫情<span class="middle-left-right-font">
          截止至:2024/10/18 23:50</span
        >
      </p>
    </div>
    <div class="middle-left-bg flex flex-wrap">
      <div
        class="middle-left-china"
        v-for="item in chinaDefiniteDiagnosisList"
        :key="item.name"
      >
        <p class="middle-left-china-name">{{ item.name }}</p>
        <p
          class="font-titles"
          :class="[
            item.name === '国内现有确诊' || item.name === '无症状'
              ? 'middle-left-china-numberYellow'
              : 'middle-left-china-number',
          ]"
        >
          {{ item.number }}
        </p>
        <p class="middle-left-china-compare">
          较昨日<span
            :class="[
              item.name === '国内现有确诊' || item.name === '无症状'
                ? 'middle-left-china-numberYellow'
                : 'middle-left-china-number',
            ]"
            v-if="item.isAdd"
            >+ {{ item.number }}</span
          >
          <span
            :class="[
              item.name === '国内现有确诊' || item.name === '无症状'
                ? 'middle-left-china-numberYellow'
                : 'middle-left-china-number',
            ]"
            v-else
            >- {{ item.number }}</span
          >
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
</template>

<script lang="ts" setup>
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
}
</style>
