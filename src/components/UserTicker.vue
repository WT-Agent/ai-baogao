<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[报告生成完成]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 137****9021 完成了乡村振兴社会实践调研报告生成' },
  { text: '用户 176****3892 完成了计算机网络专业课程实训总结' },
  { text: '用户 188****1029 完成了企业人力资源岗位毕业实习总结报告' },
  { text: '用户 132****6671 完成了环境工程水质检测实验分析报告' },
  { text: '用户 155****4928 完成了心理学学术研讨会读书心得汇报' },
]);
</script>
