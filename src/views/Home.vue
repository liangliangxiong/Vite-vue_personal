<template>
  <div class="home">
    <!-- 个人信息展示区 -->
    <div class="profile-section">
      <el-row :gutter="40">
        <el-col :span="8">
          <div class="profile-image">
            <el-avatar :size="200" src="https://www.apple.com.cn/home/heroes/iphone-16/images/hero_iphone16_avail__euwzls69btea_mediumtall_2x.jpg" />
          </div>
        </el-col>
        <el-col :span="16">
          <div class="profile-info">
            <h1>徐博亮</h1>
            <h2>全栈开发工程师</h2>
            <p>热爱编程，专注于Web开发，追求技术创新与卓越</p>
            <div class="profile-actions">
              <el-button type="primary" @click="downloadResume">下载简历</el-button>
              <el-button @click="scrollToContact">联系我</el-button>
            </div>
          </div>
        </el-col>
      </el-row>
    </div>

    <!-- 轮播图部分 -->
    <el-carousel height="500px">
      <el-carousel-item v-for="item in carouselItems" :key="item.id">
        <div class="carousel-content">
          <h2>{{ item.title }}</h2>
          <p>{{ item.subtitle }}</p>
        </div>
      </el-carousel-item>
    </el-carousel>

    <!-- 个人技能概览部分 -->
    <div class="business-overview">
      <h2 class="section-title">专业技能</h2>
      <el-row :gutter="20">
        <el-col :span="8" v-for="(item, index) in skillItems" :key="index">
          <el-card class="business-card">
            <el-icon size="40px" class="mb-2">
              <component :is="item.icon"></component>
            </el-icon>
            <h3>{{ item.title }}</h3>
            <p>{{ item.description }}</p>
          </el-card>
        </el-col>
      </el-row>
    </div>
    <!-- 精选项目预览 -->
    <div class="featured-projects">
      <h2 class="section-title">精选项目</h2>
      <el-row :gutter="20">
        <el-col :span="8" v-for="project in featuredProjects" :key="project.id">
          <el-card class="project-card" :body-style="{ padding: '0px' }">
            <img :src="project.image" class="project-image">
            <div class="project-info">
              <h3>{{ project.title }}</h3>
              <p>{{ project.description }}</p>
              <el-button type="text" @click="viewProject(project.id)">查看详情</el-button>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </div>

    <!-- 联系方式 -->
    <div class="contact-section" id="contact">
      <h2 class="section-title">联系方式</h2>
      <el-row :gutter="20" justify="center">
        <el-col :span="6" v-for="contact in contactInfo" :key="contact.type">
          <el-card class="contact-card">
            <el-icon size="40px"><component :is="contact.icon" /></el-icon>
            <h3>{{ contact.title }}</h3>
            <p>{{ contact.value }}</p>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script setup>
import { Monitor, Connection, TrendCharts, Message, Location, Link } from '@element-plus/icons-vue'

const carouselItems = [
  {
    id: 1,
    title: '前端开发工程师',
    subtitle: '专注于创建优秀的用户体验'
  },
  {
    id: 2,
    title: '全栈开发者',
    subtitle: '掌握前后端技术栈'
  },
  {
    id: 3,
    title: '技术创新者',
    subtitle: '持续学习，不断进步'
  }
]

const skillItems = [
  {
    icon: 'Monitor',
    title: '前端开发',
    description: '精通HTML、CSS、JavaScript，熟练使用Vue.js、React等主流框架'
  },
  {
    icon: 'Connection',
    title: '后端开发',
    description: 'Node.js、Python开发经验，熟悉数据库设计和API开发'
  },
  {
    icon: 'TrendCharts',
    title: '项目管理',
    description: '具备项目规划、团队协作和敏捷开发经验'
  }
]

const featuredProjects = [
  {
    id: 1,
    title: '电商平台',
    description: '基于Vue3的现代电商平台',
    image: 'https://www.apple.com.cn/home/heroes/iphone-16/images/hero_iphone16_avail__euwzls69btea_mediumtall_2x.jpg'
  },
  {
    id: 2,
    title: '在线教育系统',
    description: '全栈在线教育解决方案',
    image: 'https://www.apple.com.cn/home/heroes/iphone-16/images/hero_iphone16_avail__euwzls69btea_mediumtall_2x.jpg'
  },
  {
    id: 3,
    title: '社交媒体APP',
    description: '移动端社交应用开发',
    image: 'https://www.apple.com.cn/home/heroes/iphone-16/images/hero_iphone16_avail__euwzls69btea_mediumtall_2x.jpg'
  }
]

const contactInfo = [
  {
    type: 'email',
    icon: 'Message',
    title: '邮箱',
    value: 'example@email.com'
  },
  {
    type: 'location',
    icon: 'Location',
    title: '所在地',
    value: '深圳'
  },
  {
    type: 'github',
    icon: 'Link',
    title: 'GitHub',
    value: 'github.com/yourname'
  }
]

const downloadResume = () => {
  // 实现简历下载逻辑
  console.log('下载简历')
}

const scrollToContact = () => {
  document.getElementById('contact').scrollIntoView({ behavior: 'smooth' })
}

const viewProject = (id) => {
  console.log('查看项目', id)
}
</script>

<style scoped lang="scss">
.home {
  .profile-section {
    padding: 80px 10%;
    background: linear-gradient(to right, #f8f9fa, #e9ecef);
    border-radius: 0 0 50px 50px;
    margin-bottom: 40px;

    .profile-image {
      display: flex;
      justify-content: center;
      align-items: center;

      .el-avatar {
        border: 4px solid white;
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        transition: transform 0.3s ease;

        &:hover {
          transform: scale(1.05);
        }
      }
    }

    .profile-info {
      h1 {
        font-size: 48px;
        margin-bottom: 15px;
        color: #2c3e50;
        font-weight: 700;
        letter-spacing: -1px;
      }

      h2 {
        font-size: 28px;
        color: #3498db;
        margin-bottom: 25px;
        font-weight: 600;
      }

      p {
        font-size: 20px;
        color: #666;
        margin-bottom: 35px;
        line-height: 1.6;
      }

      .profile-actions {
        display: flex;
        gap: 20px;

        .el-button {
          padding: 12px 30px;
          font-size: 16px;
          border-radius: 25px;
          transition: all 0.3s ease;

          &:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
          }
        }
      }
    }
  }

  .el-carousel {
    margin: 0 auto 60px;
    max-width: 1400px;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);

    .carousel-content {
      height: 100%;
      background: linear-gradient(135deg, #2c3e50, #3498db);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      color: white;
      text-align: center;
      padding: 0 20px;

      h2 {
        font-size: 54px;
        margin-bottom: 25px;
        font-weight: 700;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
      }

      p {
        font-size: 28px;
        max-width: 800px;
        line-height: 1.4;
        text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
      }
    }
  }

  .business-overview {
    padding: 60px 10%;
    background-color: #f8f9fa;
    border-radius: 50px;
    margin: 0 20px 60px;

    .section-title {
      text-align: center;
      font-size: 42px;
      margin-bottom: 50px;
      color: #2c3e50;
      font-weight: 700;
    }

    .business-card {
      text-align: center;
      padding: 40px 30px;
      border-radius: 20px;
      transition: all 0.3s ease;
      height: 100%;
      border: none;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);

      &:hover {
        transform: translateY(-10px);
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
      }

      .el-icon {
        font-size: 48px;
        color: #3498db;
        margin-bottom: 25px;
      }

      h3 {
        font-size: 24px;
        margin: 20px 0;
        color: #2c3e50;
        font-weight: 600;
      }

      p {
        color: #666;
        line-height: 1.6;
        font-size: 16px;
      }
    }
  }

  .featured-projects {
    padding: 60px 10%;
    background-color: white;

    .section-title {
      text-align: center;
      font-size: 42px;
      margin-bottom: 50px;
      color: #2c3e50;
      font-weight: 700;
    }

    .project-card {
      border-radius: 15px;
      overflow: hidden;
      transition: all 0.3s ease;
      border: none;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);

      &:hover {
        transform: translateY(-10px);
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
      }

      .project-image {
        width: 100%;
        height: 240px;
        object-fit: cover;
        transition: transform 0.3s ease;

        &:hover {
          transform: scale(1.05);
        }
      }

      .project-info {
        padding: 25px;

        h3 {
          font-size: 22px;
          margin: 0 0 15px;
          color: #2c3e50;
          font-weight: 600;
        }

        p {
          color: #666;
          margin-bottom: 20px;
          line-height: 1.6;
        }

        .el-button {
          font-size: 16px;
          padding: 8px 0;
          transition: all 0.3s ease;

          &:hover {
            color: #3498db;
            transform: translateX(5px);
          }
        }
      }
    }
  }

  .contact-section {
    padding: 80px 10%;
    background: linear-gradient(to right, #f8f9fa, #e9ecef);
    border-radius: 50px 50px 0 0;

    .section-title {
      text-align: center;
      font-size: 42px;
      margin-bottom: 50px;
      color: #2c3e50;
      font-weight: 700;
    }

    .contact-card {
      text-align: center;
      padding: 40px 30px;
      border-radius: 20px;
      transition: all 0.3s ease;
      border: none;
      background-color: white;
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);

      &:hover {
        transform: translateY(-10px);
        box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
      }

      .el-icon {
        font-size: 48px;
        color: #3498db;
        margin-bottom: 20px;
      }

      h3 {
        font-size: 22px;
        margin: 15px 0 10px;
        color: #2c3e50;
        font-weight: 600;
      }

      p {
        color: #666;
        font-size: 16px;
      }
    }
  }
}
</style>