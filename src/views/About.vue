<template>
  <div class="about">
    <div class="about-header">
      <h1>关于我</h1>
      <p>热爱技术，追求创新</p>
    </div>

    <div class="about-content">
      <el-row :gutter="40">
        <el-col :span="12">
          <div class="company-intro">
            <h2>个人简介</h2>
            <p>一名充满热情的全栈开发工程师，拥有多年的Web开发经验。专注于创建高质量的用户体验，同时具备扎实的后端开发能力。</p>
            <el-divider />
            <h3>教育背景</h3>
            <p>计算机科学与技术学士学位</p>
            <h3>工作经历</h3>
            <p>拥有5年以上的开发经验，曾在多家互联网公司担任开发工程师职位</p>
          </div>
        </el-col>
        <el-col :span="12">
          <div class="company-values">
            <el-card v-for="(value, index) in values" :key="index" class="value-card">
              <template #header>
                <div class="value-header">
                  <el-icon size="24"><component :is="value.icon" /></el-icon>
                  <h3>{{ value.title }}</h3>
                </div>
              </template>
              <p>{{ value.description }}</p>
            </el-card>
          </div>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script setup>
import { Star, Aim, Connection } from '@element-plus/icons-vue'

const values = [
  {
    icon: 'Star',
    title: '技术追求',
    description: '持续学习新技术，追求代码质量和性能优化'
  },
  {
    icon: 'Aim',
    title: '目标导向',
    description: '注重项目成果，善于解决复杂问题'
  },
  {
    icon: 'Connection',
    title: '团队协作',
    description: '具备良好的沟通能力，乐于分享和协作'
  }
]
</script>

<style scoped lang="scss">
.about {
  .about-header {
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

  .about-content {
    padding: 60px 10%;
    
    .company-intro {
      background-color: white;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);
      transition: all 0.3s ease;

      &:hover {
        transform: translateY(-10px);
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
      }

      h2 {
        font-size: 28px;
        color: #2c3e50;
        margin-bottom: 20px;
        font-weight: 600;
      }

      h3 {
        font-size: 22px;
        color: #2c3e50;
        margin: 20px 0 10px;
        font-weight: 600;
      }

      p {
        color: #666;
        line-height: 1.8;
        margin-bottom: 20px;
        font-size: 16px;
      }
    }

    .company-values {
      .value-card {
        margin-bottom: 20px;
        transition: transform 0.3s;

        &:hover {
          transform: translateY(-5px);
        }

        .value-header {
          display: flex;
          align-items: center;
          gap: 10px;

          h3 {
            margin: 0;
            font-size: 18px;
            color: #2c3e50;
          }
        }

        p {
          color: #666;
          line-height: 1.6;
        }
      }
    }
  }
}
</style>