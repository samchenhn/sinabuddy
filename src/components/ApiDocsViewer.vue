<script setup lang="ts">
import { ref, onMounted } from "vue";
import { ElCard, ElTabs, ElTabPane, ElLink } from "element-plus";

interface DocFile {
  name: string;
  path: string;
}

const docFiles = ref<DocFile[]>([]);
const activeTab = ref("");

// 获取文档文件列表
const loadDocFiles = () => {
  // 这里我们手动列出已知的文档文件
  docFiles.value = [
    { name: "README", path: "/server-docs/README.md" },
    { name: "快速开始", path: "/server-docs/quick-start.md" },
    { name: "认证模块", path: "/server-docs/auth-module-summary.md" },
    { name: "配置说明", path: "/server-docs/configuration.md" },
    { name: "部署指南", path: "/server-docs/deployment.md" },
    { name: "日志使用", path: "/server-docs/logger-usage.md" },
    { name: "测试报告", path: "/server-docs/test-and-sync-report.md" },
  ];

  if (docFiles.value.length > 0) {
    activeTab.value = docFiles.value[0].path;
  }
};

onMounted(() => {
  loadDocFiles();
});
</script>

<template>
  <el-card class="docs-viewer-card">
    <template #header>
      <div class="card-header">
        <span>API 文档阅读器</span>
      </div>
    </template>

    <el-tabs v-model="activeTab" type="border-card">
      <el-tab-pane
        v-for="doc in docFiles"
        :key="doc.path"
        :label="doc.name"
        :name="doc.path"
      >
        <div class="doc-content">
          <p>文档路径: {{ doc.path }}</p>
          <el-link :href="doc.path" target="_blank" type="primary">
            在新窗口中打开文档
          </el-link>
          <iframe
            v-if="activeTab === doc.path"
            :src="doc.path"
            class="doc-iframe"
            frameborder="0"
          ></iframe>
        </div>
      </el-tab-pane>
    </el-tabs>
  </el-card>
</template>

<style scoped>
.docs-viewer-card {
  margin: 20px;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.doc-content {
  padding: 20px 0;
}

.doc-iframe {
  width: 100%;
  height: 600px;
  border: 1px solid #ebeef5;
  border-radius: 4px;
}
</style>
