<template>
  <div>
    <h2>ばあちゃんの夢をかなえる旅</h2>
    <table ref="table1Ref" class="table component-container" :class="{ 'fadeInUp': isVisible1, 'fadeOut': !isVisible1 }">
      <thead>
      <tr>
        <th colspan="4" class="text-center header-title">
          <span>2024/3/18</span>
          <h3 class="m-0">博多</h3>
        </th>
      </tr>
      <tr class="pc-only">
        <th class="text-center">日付</th>
        <th class="text-center">活動</th>
        <th class="text-center">場所</th>
        <th class="text-center">地図</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(item, index) in schedule1" :key="index">
        <td data-label="日付">{{ item.time }}</td>
        <td data-label="活動">{{ item.activity }}</td>
        <td data-label="場所">{{ item.location }}</td>
        <td data-label="地図">
          <div v-if="item.location_link">
            <a target="_blank" :href="item.location_link">
              {{ item.location }}
            </a>
          </div>
          <div v-else>
            {{ item.location }}
          </div>
        </td>
      </tr>
      </tbody>
    </table>

    <table ref="table2Ref" class="table component-container" :class="{ 'fadeInUp': isVisible2, 'fadeOut': !isVisible2 }">
      <thead>
      <tr>
        <th colspan="4" class="text-center header-title">
          <span>2024/3/19</span>
          <h3 class="m-0">ハウステンボス</h3>
        </th>
      </tr>
      <tr class="pc-only">
        <th class="text-center">日付</th>
        <th class="text-center">活動</th>
        <th class="text-center">場所</th>
        <th class="text-center">地図</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(item, index) in schedule2" :key="index">
        <td data-label="日付">{{ item.time }}</td>
        <td data-label="活動">{{ item.activity }}</td>
        <td data-label="場所">{{ item.location }}</td>
        <td data-label="地図">
          <div v-if="item.location_link">
            <a target="_blank" :href="item.location_link">
              {{ item.location }}
            </a>
          </div>
          <div v-else>
            {{ item.location }}
          </div>

        </td>
      </tr>
      </tbody>
    </table>
    <table ref="table3Ref" class="table component-container" :class="{ 'fadeInUp': isVisible3, 'fadeOut': !isVisible3 }">
      <thead>
      <tr>
        <th colspan="4" class="text-center header-title">
          <span>2024/3/20</span>
          <h3 class="m-0">長崎</h3>
        </th>
      </tr>
      <tr class="pc-only">
        <th class="text-center">日付</th>
        <th class="text-center">活動</th>
        <th class="text-center">場所</th>
        <th class="text-center">地図</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(item, index) in schedule3" :key="index">
        <td data-label="日付">{{ item.time }}</td>
        <td data-label="活動">{{ item.activity }}</td>
        <td data-label="場所">{{ item.location }}</td>
        <td data-label="地図">
          <div v-if="item.location_link">
            <a target="_blank" :href="item.location_link">
              {{ item.location }}
            </a>
          </div>
          <div v-else>
            {{ item.location }}
          </div>
        </td>
      </tr>
      </tbody>
    </table>
    <div class="">
      <h3>ラーメン特集</h3>
      <a v-for="(link, index) in mens" :key="index" target="_blank" :href="link" style="display: block">
        {{ link }}
      </a><br>
    </div>
  </div>
</template>

<script setup>
import {ref} from 'vue';
import {useIntersectionObserver} from '@vueuse/core';

const schedule1 = ref([
  {time: '〜16:00', activity: '到着 ＆ 各自チェックイン済ませて荷物置く', location: '変なホテル', location_link: 'https://maps.app.goo.gl/n6dbDXjJ2MmkCp3x8'},
  {time: '17:30', activity: '貴大　博多空港にレンタカー取りに行く', location: '博多空港 国内線口', location_link: 'https://maps.app.goo.gl/xtngiRNRpEXtRegT7'},
  {time: '17:50', activity: '貴大　コンパ止める', location: 'Dパーキング　福岡市須崎町第3', location_link: 'https://www.google.com/maps?q=%E3%80%92812-0028+%E7%A6%8F%E5%B2%A1%E7%9C%8C%E7%A6%8F%E5%B2%A1%E5%B8%82%E5%8D%9A%E5%A4%9A%E5%8C%BA%E9%A0%88%E5%B4%8E%E7%94%BA%EF%BC%93%E2%88%92%EF%BC%92%EF%BC%95+D%E3%83%91%E3%83%BC%E3%82%AD%E3%83%B3%E3%82%B0+%E7%A6%8F%E5%B2%A1%E5%B8%82%E9%A0%88%E5%B4%8E%E7%94%BA%E7%AC%AC%EF%BC%93&ftid=0x3541914e0c2f55cb:0xa3037bbb0f04a47a&entry=gps&lucs=,94209859,47071704,47069508,47084304,94208457,94206605&g_ep=CAISDTYuMTAxLjMuNDE1NjAYACCs3wEqNiw5NDIwOTg1OSw0NzA3MTcwNCw0NzA2OTUwOCw0NzA4NDMwNCw5NDIwODQ1Nyw5NDIwNjYwNUICSlA%3D&g_st=ia'},
  {time: '〜18:00', activity: '自由行動', location: ''},
  {time: '18:00', activity: 'ディナー　もつ鍋　楽天地？', location: '天神 アクロス福岡', location_link:'https://www.google.com/maps?ll=33.591471,130.402349&z=17&t=m&hl=ja&gl=US&mapclient=apiv3&cid=6724116355710339721', link: 'https://tabelog.com/fukuoka/A4001/A400103/40056554/'},
  {time: '20:00', activity: '自由行動 & たいちゃんと博多美人探しの旅', location: ''},
  {time: '備考', activity: '鳥が食べたい', location: '鳥刺し', location_link: 'http://ryushow.jp/food/alacarte.html'},
]);

const schedule2 = ref([
  {time: '〜9:30', activity: 'モーニング', location: ''},
  {time: '9:45', activity: '出発', location: '糸島、伊万里、佐世保経由'},
  {time: '10:30〜11:30', activity: '寄り道 有田焼　道の駅など', location: '伊万里', location_link: 'https://maps.app.goo.gl/72DG7h21JbkWwGp68'},
  {time: '12:30', activity: 'ランチ　伊万里牛？', location: '伊万里', location_link: 'https://maps.app.goo.gl/Zc19UBLtYFKyvRwQ7'},
  {time: '13:30', activity: 'ハウステボス到着', location: 'ハウステンボス', location_link: 'https://maps.app.goo.gl/ptTznrkm1kbgArnJA'},
  {time: '', activity: 'ディナー　ちゃんぽん？', location: '佐世保かハウステンボス内', location_link: 'https://maps.app.goo.gl/qUFwgJTSLjSYWsB1A'},
]);

const schedule3 = ref([
  {time: '〜10:00', activity: 'モーニング', location: ''},
  {time: '11:00', activity: 'グラバー園 & 天主堂 ＆ 眼鏡橋', location:'グラバー園', location_link: 'https://maps.app.goo.gl/BEnrup1aC6teNkM87'},
  {time: '12:00', activity: 'ランチ　中華街？'},
  {time: '〜16:30', activity: '自由行動'},
  {time: '〜18:30', activity: '福岡空港到着'},
]);

const mens = [
  'https://maps.app.goo.gl/MViDbgddah6Fco4Q6',
  'https://maps.app.goo.gl/9AHdZBgPMEgbueFL8',
  'https://maps.app.goo.gl/23QDsYqt6uhHM6LW7',
  'https://maps.app.goo.gl/bZ93ga2FVfTDvs4i7',
  'https://maps.app.goo.gl/TJoqcsDCHPJjwxMK7',
  'https://maps.app.goo.gl/KMnFfhhJQS1aLZ8L6'
]

const table1Ref = ref(null);
const table2Ref = ref(null);
const table3Ref = ref(null);
const isVisible1 = ref(false);
const isVisible2 = ref(false);
const isVisible3 = ref(false);

useIntersectionObserver(
    table1Ref,
    ([{isIntersecting}]) => {
      isVisible1.value = isIntersecting;
    },
);
useIntersectionObserver(
    table2Ref,
    ([{isIntersecting}]) => {
      isVisible2.value = isIntersecting;
    },
);
useIntersectionObserver(
    table3Ref,
    ([{isIntersecting}]) => {
      isVisible3.value = isIntersecting;
    },
);
</script>

<style>
body {
  background: #eee5db;
}
</style>
<style scoped>
.component-container {
  opacity: 0;
  width: 100%;
}

.header-title  {
  background-color: #fa0;
}
.text-center {
  text-align: center;
}
/* テーブルのスタイル */
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
  background-color: #faf8f5;
}

th, td {
  text-align: left;
  padding: 8px;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #f0f0f0;
}

tr:hover {
  background-color: #f5f5f5;
}

.m-0 {
  margin: 0;
}
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fadeInUp {
  animation-name: fadeInUp;
  animation-duration: 1s;
  animation-fill-mode: both;
}

.fadeOut {
  animation-name: fadeOut;
  animation-duration: 1s;
  animation-fill-mode: both;
}

@keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
    transform: translateY(20px);
  }
}

/* レスポンシブデザインのスタイル */
@media (max-width: 768px) {
  .table, .table thead, .table tbody, .table th, .table td, .table tr {
    display: block;
  }

  .table thead tr.pc-only {
    position: absolute;
    top: -9999px;
    left: -9999px;
  }

  .table tr { border: 1px solid #ccc; }

  .table td {
    border: none;
    border-bottom: 1px solid #eee;
    position: relative;
    padding-left: 30%;
    min-height: 24px;
    text-align: left;
  }

  .table td:before {
    content: attr(data-label);
    position: absolute;
    left: 0;
    padding-left: 15px;
    font-weight: bold;
    text-align: left;
  }
}

</style>
