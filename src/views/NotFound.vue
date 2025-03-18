<template>
  <div class="not-found">
    <el-result
      icon="warning"
      title="404"
      sub-title="抱歉，您访问的页面不存在"
      class="result-card"
    >
      <template #icon>
        <div class="custom-icon">
          <span class="number">4</span>
          <el-icon class="rotating"><Warning /></el-icon>
          <span class="number">4</span>
        </div>
      </template>
      <template #extra>
        <div class="action-buttons">
          <el-button type="primary" :icon="Back" @click="router.back()">返回上一页</el-button>
          <el-button type="success" :icon="HomeFilled" @click="router.push('/')">返回首页</el-button>
        </div>
        <p class="tip-text">您可以尝试以下操作：</p>
        <ul class="tips-list">
          <li>检查输入的网址是否正确</li>
          <li>点击返回按钮回到上一页</li>
          <li>返回首页重新开始</li>
        </ul>
      </template>
    </el-result>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { Back, HomeFilled, Warning } from '@element-plus/icons-vue'

const router = useRouter()
</script>

<style scoped lang="scss">
.not-found {
  min-height: calc(100vh - 60px); // 减去导航栏高度
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px;
  background: linear-gradient(135deg, #f5f7fa 0%, #e4e7eb 100%);

  .result-card {
    background: rgba(255, 255, 255, 0.9);
    border-radius: 16px;
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(5px);
    padding: 40px;
    transition: transform 0.3s ease;

    &:hover {
      transform: translateY(-5px);
    }
  }

  .custom-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-bottom: 24px;

    .number {
      font-size: 64px;
      font-weight: bold;
      color: var(--el-color-primary);
      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
    }

    .rotating {
      font-size: 48px;
      color: var(--el-color-warning);
      animation: rotate 3s infinite linear;
    }
  }

  .action-buttons {
    display: flex;
    gap: 16px;
    justify-content: center;
    margin-bottom: 24px;
  }

  .tip-text {
    color: var(--el-text-color-secondary);
    font-size: 16px;
    margin-bottom: 12px;
  }

  .tips-list {
    list-style: none;
    padding: 0;
    margin: 0;
    text-align: center;
    color: var(--el-text-color-secondary);

    li {
      margin: 8px 0;
      font-size: 14px;
      opacity: 0.8;
      transition: opacity 0.3s ease;

      &:hover {
        opacity: 1;
      }
    }
  }
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style> 