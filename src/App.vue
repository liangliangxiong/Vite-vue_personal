<template>
  <div class="app">
    <el-menu
      mode="horizontal"
      router
      class="nav-menu"
    >
      <el-menu-item index="/">
        <el-icon><HomeFilled /></el-icon>
        首页
      </el-menu-item>
      <el-menu-item index="/blog">
        <el-icon><Document /></el-icon>
        博客文章
      </el-menu-item>
      <el-menu-item index="/projects">
        <el-icon><Goods /></el-icon>
        项目经验
      </el-menu-item>
      <el-menu-item index="/about">
        <el-icon><InfoFilled /></el-icon>
        关于我
      </el-menu-item>
    </el-menu>

    <router-view></router-view>
  </div>
</template>

<script setup>
import { HomeFilled, Document, Goods, InfoFilled } from '@element-plus/icons-vue'
</script>

<style scoped lang="scss">
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;

  .nav-menu {
    padding: 0 10%;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
}
</style>
