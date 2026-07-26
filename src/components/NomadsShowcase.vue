<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">实践与课堂报告实战模板库</h2>
        <p class="showcase-subtitle">精选高校社会实践、实验实训与毕业实习报告场景，点击“一键套用”快速生成</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个报告模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次应用</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { prompt: string; reportType?: string; majorGroup?: string }): void;
}>();

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  reportType?: string;
  majorGroup?: string;
  usageCount: string;
}

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'baogao-1',
    tag: '社会实践',
    title: '乡村振兴数字电商赋能调研报告',
    prompt: '暑期赴山区农村开展特色农产品直播电商调研，围绕农户意愿、物流痛点、品牌包装及后续帮扶对策撰写 3000 字社会实践报告。',
    reportType: '社会实践与调研报告',
    majorGroup: '人文社科类',
    usageCount: '48.9k'
  },
  {
    id: 'baogao-2',
    tag: '专业实训',
    title: '软件工程 Web 全栈项目开发实训总结',
    prompt: '为期两周的基于 Vue 与 Node.js 电商平台开发实训，记录数据库设计、API 调试、团队 Git 协同及遇到的异步 BUG 解决心得。',
    reportType: '专业实训与实验报告',
    majorGroup: '理工农医类',
    usageCount: '41.3k'
  },
  {
    id: 'baogao-3',
    tag: '毕业实习',
    title: '互联网公司产品运营岗位实习报告',
    prompt: '在科技公司担任产品运营实习生 3 个月，总结用户增长活动策划、数据分析指标跟踪、跨部门沟通及自我能力提升感悟。',
    reportType: '毕业实习与岗位总结',
    majorGroup: '经济管理类',
    usageCount: '53.6k'
  },
  {
    id: 'baogao-4',
    tag: '工科实验',
    title: '电子信息工程电路仿真与焊接测试',
    prompt: '基于 Proteus 的简易示波器电路设计与 PCB 焊接调试实验报告，记录波形失真原因分析及仪器使用体会。',
    reportType: '专业实训与实验报告',
    majorGroup: '理工农医类',
    usageCount: '29.7k'
  },
  {
    id: 'baogao-5',
    tag: '教育实习',
    title: '中学语文课堂教学与班主任实习总结',
    prompt: '赴县城中学开展为期一学期的教育实习，总结教案编写、课堂试讲互动、后进生心理辅导及教育理念升华。',
    reportType: '毕业实习与岗位总结',
    majorGroup: '师范教育类',
    usageCount: '36.1k'
  },
  {
    id: 'baogao-6',
    tag: '学术研讨',
    title: '人工智能前沿算法课程研讨与读书心得',
    prompt: '阅读大语言模型 Transformer 架构经典论文后，撰写 2000 字研讨课汇报，剖析注意力机制与未来 AGIC 发展趋势。',
    reportType: '课堂学术研讨与心得',
    majorGroup: '理工农医类',
    usageCount: '32.4k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    reportType: item.reportType,
    majorGroup: item.majorGroup
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
