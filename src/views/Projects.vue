<template>
  <div class="products">
    <div class="products-header">
      <h1>项目经验</h1>
      <p>技术实践与项目案例</p>
    </div>

    <div class="products-content">
      <el-row :gutter="30">
        <el-col :span="8" v-for="(project, index) in projects" :key="index">
          <el-card class="project-card" :body-style="{ padding: '0px' }">
            <div class="project-image">
              <el-image 
                :src="project.image" 
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
            <div class="project-info">
              <h3>{{ project.name }}</h3>
              <p class="project-desc">{{ project.description }}</p>
              <div class="project-features">
                <el-tag 
                  v-for="(tech, idx) in project.technologies" 
                  :key="idx"
                  class="feature-tag"
                  type="info"
                  effect="plain"
                >
                  {{ tech }}
                </el-tag>
              </div>
              <el-button type="primary" plain>查看详情</el-button>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script setup>
import { Picture } from '@element-plus/icons-vue'

const projects = [
  {
    name: '电商平台重构',
    description: '使用Vue3和Element Plus重构电商平台前端，提升了性能和用户体验',
    image: 'https://via.placeholder.com/400x200',
    technologies: ['Vue3', 'Element Plus', 'Vite']
  },
  {
    name: '在线教育系统',
    description: '开发在线教育平台的后端API和管理系统，支持课程管理和用户学习',
    image: 'https://via.placeholder.com/400x200',
    technologies: ['Node.js', 'Express', 'MongoDB']
  },
  {
    name: '社交媒体APP',
    description: '负责社交媒体APP的全栈开发，实现实时聊天和动态发布等功能',
    image: 'https://via.placeholder.com/400x200',
    technologies: ['React Native', 'Socket.io', 'AWS']
  }
]
</script>

<style scoped lang="scss">
.products {
  .products-header {
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

  .products-content {
    padding: 60px 10%;

    .project-card {
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

      .project-info {
        padding: 20px;

        h3 {
          margin: 0 0 15px;
          font-size: 20px;
          color: #2c3e50;
        }

        .project-desc {
          color: #666;
          margin-bottom: 20px;
          line-height: 1.6;
        }

        .project-features {
          margin-bottom: 20px;
          
          .feature-tag {
            margin-right: 8px;
            margin-bottom: 8px;
          }
        }
      }
    }
  }
}
</style>