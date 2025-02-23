<template>
  <div class="news">
    <div class="news-header">
      <h1>博客文章</h1>
      <p>技术分享与心得体会</p>
    </div>
    
    <div class="news-content">
      <el-row :gutter="20">
        <el-col :span="8" v-for="(item, index) in newsList" :key="index">
          <el-card class="news-card" :body-style="{ padding: '0px' }">
            <div class="news-image">
              <el-image 
                :src="item.image" 
                fit="cover"
                style="height: 200px; width: 100%"
              >
                <template #error>
                  <div class="image-slot">
                    <el-icon><Picture /></el-icon>
                  </div>
                </template>
              </el-image>
            </div>
            <div class="news-info">
              <h3>{{ item.title }}</h3>
              <p class="news-date">{{ item.date }}</p>
              <p class="news-desc">{{ item.description }}</p>
              <el-button text>阅读更多</el-button>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script setup>
import { Picture } from '@element-plus/icons-vue'

const newsList = [
  {
    title: 'Vue3组件开发最佳实践',
    date: '2024-02-20',
    description: '分享Vue3组件开发中的经验和技巧，包括组件设计、性能优化等方面的心得',
    image: '/images/hero_iphone16_avail__euwzls69btea_mediumtall_2x.jpg'
  },
  {
    title: 'Node.js性能调优指南',
    date: '2024-02-18',
    description: '探讨Node.js应用性能优化的方法，包括内存管理、异步操作等关键点',
    image: '/images/hero_iphone16_avail__euwzls69btea_mediumtall_2x.jpg'
  },
  {
    title: '前端工程化实践总结',
    date: '2024-02-15',
    description: '分享在前端工程化方面的实践经验，包括构建工具、自动化测试等话题',
    image: '/images/hero_iphone16_avail__euwzls69btea_mediumtall_2x.jpg'
  }
]
</script>

<style scoped lang="scss">
.news {
  .news-header {
    padding: 80px 10%;
    background: linear-gradient(to right, #f8f9fa, #e9ecef);
    border-radius: 0 0 50px 50px;
    margin-bottom: 40px;
    text-align: center;

    h1 {
      font-size: 42px;
      color: #2c3e50;
      margin-bottom: 15px;
      font-weight: 700;
      letter-spacing: -1px;
    }

    p {
      font-size: 20px;
      color: #666;
      margin-bottom: 35px;
      line-height: 1.6;
    }
  }

  .news-content {
    padding: 60px 10%;

    .news-card {
      border-radius: 15px;
      overflow: hidden;
      transition: all 0.3s ease;
      border: none;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);
      margin-bottom: 30px;

      &:hover {
        transform: translateY(-10px);
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
      }

      .news-info {
        padding: 20px;

        h3 {
          margin: 0 0 10px;
          font-size: 20px;
          color: #2c3e50;
        }

        .news-date {
          color: #999;
          font-size: 14px;
          margin-bottom: 10px;
        }

        .news-desc {
          color: #666;
          margin-bottom: 15px;
          line-height: 1.6;
        }
      }
    }
  }
}
</style>