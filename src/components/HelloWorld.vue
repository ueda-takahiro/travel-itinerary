<template>
  <div ref="componentRef" class="component-container" :class="{ 'fadeInUp': isVisible }">
    <h2>旅行の日程</h2>
    <table>
      <thead>
      <tr>
        <th>日付</th>
        <th>活動</th>
        <th>場所</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(item, index) in schedule" :key="index">
        <td>{{ item.date }}</td>
        <td>{{ item.activity }}</td>
        <td>{{ item.location }}</td>
        <td>
          <router-link to="/about">About</router-link>
        </td>

      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { ref } from 'vue';
import { useIntersectionObserver } from '@vueuse/core';

export default {
  setup() {
    const schedule = ref([
      { date: '2024-04-01', activity: '到着 & 宿泊', location: '京都' },
      { date: '2024-04-02', activity: '神社訪問', location: '伏見稲荷大社' },
      { date: '2024-04-03', activity: '文化体験', location: '清水寺' },
      // ここに他の日程を追加
    ]);
    const componentRef = ref(null);
    const isVisible = ref(false);

    useIntersectionObserver(
        componentRef,
        ([{ isIntersecting }], observerElement) => {
          isVisible.value = isIntersecting;
          if (isIntersecting) observerElement.unobserve(componentRef.value);
        },
        { threshold: 0.5 }
    );

    return {
      schedule,
      componentRef,
      isVisible,
    };
  },
};
</script>

<style scoped>
.component-container {
  opacity: 0;
}
/* テーブルのスタイル */
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
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
</style>
