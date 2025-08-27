# Sinabuddy 订单管理系统

> 基于 BuildAdmin 框架的 Vue3 + TypeScript 订单管理解决方案

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### 代码检查

```bash
npm run lint
npm run lint-fix        # 自动修复
npm run typecheck       # TypeScript类型检查
```

## 📚 核心功能

### 🎨 UI组件

- **表格组件** - 功能强大的数据表格，支持排序、筛选、分页
- **表单组件** - 丰富的表单控件，支持验证和自定义
- **图表组件** - 基于ECharts的数据可视化
- **布局组件** - 灵活的页面布局系统

### 🔐 权限管理

- **角色权限** - 基于角色的访问控制
- **路由权限** - 动态路由加载
- **按钮权限** - 细粒度权限控制

### 🌍 国际化

- **多语言支持** - 中文/英文切换
- **动态加载** - 按需加载语言包
- **组件国际化** - Element Plus组件自动适配

## ⚙️ 配置说明

### 环境变量

- `.env.development` - 开发环境配置
- `.env.production` - 生产环境配置

### API配置

在环境变量文件中修改API地址：

```env
# 开发环境
VITE_AXIOS_BASE_URL = 'http://localhost:3000'

# 生产环境
VITE_AXIOS_BASE_URL = 'https://your-api-domain.com'
```

## 🔌 集成指南

### 后端API集成

1. 修改 `src/api/` 目录下的接口定义
2. 更新环境变量中的API地址
3. 根据后端接口调整数据结构

### 自定义主题

1. 修改 `src/styles/` 目录下的样式文件
2. 配置Element Plus主题变量
3. 添加自定义CSS样式

### 添加新页面

1. 在 `src/views/` 创建页面组件
2. 在 `src/router/` 添加路由配置
3. 更新导航菜单配置

## 📖 开发指南

### 组件开发

```vue
<template>
  <div class="my-component">
    <el-button @click="handleClick">{{ $t("common.confirm") }}</el-button>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import { useI18n } from "vue-i18n";

const { t } = useI18n();

const handleClick = () => {
  console.log("Button clicked");
};
</script>
```

### API调用

```typescript
import { http } from "@/utils/http";

interface User {
  id: number;
  name: string;
  email: string;
}

export const getUserList = (): Promise<User[]> => {
  return http.get("/api/users");
};
```

### 状态管理

```typescript
import { defineStore } from "pinia";

export const useUserStore = defineStore("user", {
  state: () => ({
    userInfo: null as User | null,
    token: "",
  }),

  actions: {
    setUserInfo(user: User) {
      this.userInfo = user;
    },
  },
});
```

## 🚀 部署指南

### 静态部署

1. 构建项目: `npm run build`
2. 将 `dist/` 目录部署到Web服务器
3. 配置服务器支持SPA路由

### Docker部署

```dockerfile
FROM nginx:alpine
COPY dist/ /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 80
```

## 🤝 贡献指南

1. Fork 项目
2. 创建功能分支: `git checkout -b feature/amazing-feature`
3. 提交变更: `git commit -m 'Add amazing feature'`
4. 推送分支: `git push origin feature/amazing-feature`
5. 创建Pull Request

## 📄 许可证

本项目基于 [Apache 2.0](LICENSE) 许可证开源。

## 🙏 致谢

- [BuildAdmin](https://github.com/build-admin/buildadmin) - 原始项目
- [Vue.js](https://vuejs.org/) - 渐进式框架
- [Element Plus](https://element-plus.org/) - Vue 3 组件库
- [Vite](https://vitejs.dev/) - 构建工具

## 📞 技术支持

- 📧 邮箱: support@buildadmin.com
- 💬 QQ群: 687903819
- 📖 文档: https://doc.buildadmin.com/
- 🐛 Issues: https://github.com/build-admin/buildadmin/issues

---

⭐ 如果这个项目对您有帮助，请给它一个Star!