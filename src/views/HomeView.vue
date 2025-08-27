<script setup lang="ts">
import TheWelcome from "../components/TheWelcome.vue";
import { ElButton, ElAlert, ElCard, ElLink } from "element-plus";
</script>

<template>
  <main>
    <el-button type="primary">Element Plus Button</el-button>
    <el-alert title="Success Alert" type="success" show-icon />
    <el-card class="box-card">
      <template #header>
        <div class="card-header">
          <span>Card name</span>
          <el-button class="button" text>Operation button</el-button>
        </div>
      </template>
      <div v-for="o in 4" :key="o" class="text item">
        {{ "List item " + o }}
      </div>
    </el-card>

    <el-card class="box-card">
      <template #header>
        <div class="card-header">
          <span>API 文档</span>
        </div>
      </template>
      <p>API 文档已通过符号链接共享到项目中，您可以：</p>
      <el-link href="/server-docs/README.md" target="_blank" type="primary">
        直接查看 README 文档
      </el-link>
      <p style="margin-top: 10px">或在新窗口中打开以下地址：</p>
      <code>/server-docs/README.md</code>
    </el-card>

    <TheWelcome />
  </main>
</template>

<style scoped>
.box-card {
  margin-top: 20px;
}
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.text {
  font-size: 14px;
}
.item {
  margin-bottom: 18px;
}
</style>
