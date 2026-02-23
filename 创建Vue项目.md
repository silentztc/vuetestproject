# 创建Vue3项目完整指南

## 一、创建项目

### 第1步：使用Vite创建Vue3项目

Vite是新一代前端构建工具，比webpack快很多！

```bash
# 使用npm创建
npm create vite@latest my-vue-app

# 或使用pnpm（更快）
pnpm create vite my-vue-app

# 或使用yarn
yarn create vite my-vue-app
```

### 第2步：选择配置

运行上面命令后，会出现一系列选项：

```
? Select a framework: › Vue          # 选择Vue
? Select a variant: › TypeScript     # 选择TypeScript（推荐）或JavaScript
```

**推荐选择：**
- **Vue + TypeScript**（大型项目，团队开发）
- **Vue + JavaScript**（小项目，快速开发）

### 第3步：进入项目安装依赖

```bash
# 进入项目文件夹
cd my-vue-app

# 安装依赖
npm install
# 或
pnpm install
# 或
yarn install
```

### 第4步：启动项目

```bash
# 启动开发服务器
npm run dev

# 启动后会看到：
# ➜  Local:   http://localhost:5173/
```

打开浏览器访问 `http://localhost:5173/`，看到Vue logo就成功了！

---

## 二、安装常用依赖

### 2.1 Vue Router（路由管理）

```bash
npm install vue-router@4
```

### 2.2 Pinia（状态管理，替代Vuex）

```bash
npm install pinia
```

### 2.3 Axios（网络请求）

```bash
npm install axios
```

### 2.4 Element Plus（UI组件库）

```bash
npm install element-plus
# 自动导入插件（推荐）
npm install -D unplugin-vue-components unplugin-auto-import
```

### 2.5 其他常用库

```bash
# Sass/Less样式预处理器
npm install -D sass
# 或
npm install -D less

# 日期处理
npm install dayjs

# 工具库
npm install lodash-es
```

---

## 三、项目目录结构

### 推荐的目录结构

```
my-vue-app/
├── public/                    # 静态资源（不会被打包）
│   └── favicon.ico           # 网站图标
│
├── src/                      # 源代码目录
│   ├── api/                  # 接口请求
│   │   ├── index.js         # axios配置
│   │   ├── user.js          # 用户相关接口
│   │   └── product.js       # 产品相关接口
│   │
│   ├── assets/              # 静态资源（会被打包）
│   │   ├── images/          # 图片
│   │   ├── styles/          # 样式
│   │   │   ├── index.scss   # 全局样式
│   │   │   ├── variables.scss # 样式变量
│   │   │   └── reset.scss   # 重置样式
│   │   └── icons/           # 图标
│   │
│   ├── components/          # 公共组件
│   │   ├── Header.vue       # 头部组件
│   │   ├── Footer.vue       # 底部组件
│   │   └── Loading.vue      # 加载组件
│   │
│   ├── composables/         # 组合式函数（Vue3特有）
│   │   ├── useUser.js       # 用户相关逻辑
│   │   └── useDialog.js     # 弹窗逻辑
│   │
│   ├── layout/              # 布局组件
│   │   ├── DefaultLayout.vue # 默认布局
│   │   └── AdminLayout.vue  # 后台布局
│   │
│   ├── plugins/             # 插件配置
│   │   ├── element-plus.js  # Element Plus配置
│   │   └── axios.js         # Axios配置
│   │
│   ├── router/              # 路由配置
│   │   ├── index.js         # 路由主文件
│   │   └── routes.js        # 路由配置
│   │
│   ├── store/               # Pinia状态管理
│   │   ├── index.js         # store入口
│   │   ├── user.js          # 用户store
│   │   └── app.js           # 应用store
│   │
│   ├── utils/               # 工具函数
│   │   ├── request.js       # 请求封装
│   │   ├── storage.js       # 本地存储封装
│   │   ├── auth.js          # 权限相关
│   │   └── format.js        # 格式化工具
│   │
│   ├── views/               # 页面组件
│   │   ├── Home/            # 首页
│   │   │   └── index.vue
│   │   ├── About/           # 关于页
│   │   │   └── index.vue
│   │   ├── User/            # 用户相关页面
│   │   │   ├── Login.vue    # 登录页
│   │   │   ├── Register.vue # 注册页
│   │   │   └── Profile.vue  # 个人中心
│   │   └── NotFound.vue     # 404页面
│   │
│   ├── App.vue              # 根组件
│   ├── main.js              # 入口文件
│   └── env.d.ts             # TypeScript环境声明
│
├── .env                     # 所有环境共用的环境变量
├── .env.development         # 开发环境变量
├── .env.production          # 生产环境变量
├── .gitignore              # Git忽略文件
├── .prettierrc             # Prettier代码格式化配置
├── .eslintrc.cjs           # ESLint代码检查配置
├── index.html              # HTML模板
├── package.json            # 项目配置
├── vite.config.js          # Vite配置
└── README.md               # 项目说明
```

### 目录说明

| 目录/文件 | 说明 | 示例 |
|----------|------|------|
| `public/` | 静态资源，不会被打包，直接复制 | favicon.ico、robots.txt |
| `src/assets/` | 静态资源，会被打包优化 | 图片、样式、字体 |
| `src/components/` | 可复用的公共组件 | Button、Dialog、Table |
| `src/views/` | 页面级组件 | 首页、登录页、详情页 |
| `src/router/` | 路由配置 | 定义页面路径 |
| `src/store/` | 状态管理 | 全局数据存储 |
| `src/api/` | 接口请求 | 调用后端API |
| `src/utils/` | 工具函数 | 公共方法 |

---

## 四、环境变量配置

### 为什么需要环境变量？

不同环境（开发、测试、生产）的配置不一样，比如：
- 开发环境：API地址是 `http://localhost:3000`
- 生产环境：API地址是 `https://api.example.com`

使用环境变量可以自动切换配置。

### 4.1 创建环境变量文件

在项目根目录创建三个文件：

#### .env（所有环境共用）
```bash
# 应用名称
VITE_APP_TITLE=我的Vue应用

# 是否启用mock数据
VITE_USE_MOCK=false
```

#### .env.development（开发环境）
```bash
# 开发环境

# API基础路径
VITE_API_BASE_URL=http://localhost:3000

# 是否开启调试模式
VITE_DEBUG=true

# 上传地址
VITE_UPLOAD_URL=http://localhost:3000/upload
```

#### .env.production（生产环境）
```bash
# 生产环境

# API基础路径
VITE_API_BASE_URL=https://api.example.com

# 是否开启调试模式
VITE_DEBUG=false

# 上传地址
VITE_UPLOAD_URL=https://api.example.com/upload
```

### 4.2 在代码中使用环境变量

**注意：Vite项目中的环境变量必须以 `VITE_` 开头！**

```javascript
// 获取环境变量
console.log(import.meta.env.VITE_API_BASE_URL)
console.log(import.meta.env.VITE_APP_TITLE)

// 判断当前环境
console.log(import.meta.env.MODE)  // 'development' 或 'production'
console.log(import.meta.env.DEV)   // 是否是开发环境（true/false）
console.log(import.meta.env.PROD)  // 是否是生产环境（true/false）
```

### 4.3 实际使用示例

**在axios配置中使用：**

```javascript
// src/utils/request.js
import axios from 'axios'

const request = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,  // 自动根据环境切换
  timeout: 10000
})

export default request
```

**在组件中使用：**

```vue
<script setup>
// 获取应用标题
const appTitle = import.meta.env.VITE_APP_TITLE
console.log('应用名称:', appTitle)
</script>
```

---

## 五、Git忽略文件配置

### .gitignore文件内容

```bash
# 依赖目录
node_modules/

# 构建产物
dist/
dist-ssr/
*.local

# 编辑器配置
.vscode/*
!.vscode/extensions.json
.idea/
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?

# 日志文件
logs/
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

# 操作系统文件
.DS_Store
Thumbs.db

# 环境变量（敏感信息）
.env.local
.env.*.local

# 测试覆盖率
coverage/
*.lcov
.nyc_output

# 临时文件
*.tmp
*.temp
.cache/

# TypeScript缓存
*.tsbuildinfo
```

### 忽略规则说明

| 规则 | 说明 | 原因 |
|------|------|------|
| `node_modules/` | 依赖包目录 | 文件太多，不需要提交，用package.json管理 |
| `dist/` | 打包后的文件 | 自动生成的，不需要提交 |
| `.env.local` | 本地环境变量 | 包含敏感信息（密码、密钥） |
| `.DS_Store` | Mac系统文件 | 操作系统自动生成，无用 |
| `.vscode/` | VS Code配置 | 编辑器个人配置，不统一提交 |

---

## 六、代码格式化配置

### 6.1 安装Prettier

```bash
npm install -D prettier
```

### 6.2 创建.prettierrc配置文件

在项目根目录创建 `.prettierrc` 文件：

```json
{
  "semi": false,
  "singleQuote": true,
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "trailingComma": "none",
  "bracketSpacing": true,
  "arrowParens": "avoid",
  "endOfLine": "lf",
  "vueIndentScriptAndStyle": false
}
```

### 配置项详解

| 配置项 | 值 | 说明 |
|--------|-----|------|
| `semi` | `false` | 不使用分号 |
| `singleQuote` | `true` | 使用单引号而不是双引号 |
| `printWidth` | `100` | 每行最多100个字符 |
| `tabWidth` | `2` | 缩进2个空格 |
| `useTabs` | `false` | 使用空格而不是Tab |
| `trailingComma` | `"none"` | 不使用尾随逗号 |
| `bracketSpacing` | `true` | 对象花括号内加空格：`{ foo: bar }` |
| `arrowParens` | `"avoid"` | 箭头函数单参数不加括号：`x => x` |
| `endOfLine` | `"lf"` | 换行符使用LF（Linux/Mac风格） |
| `vueIndentScriptAndStyle` | `false` | Vue文件中script和style标签不缩进 |

### 6.3 创建.prettierignore（忽略文件）

```bash
# 不需要格式化的文件
node_modules/
dist/
*.min.js
*.min.css
```

### 6.4 在package.json添加格式化命令

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "format": "prettier --write \"src/**/*.{js,vue,ts,css,scss,json,md}\"",
    "format:check": "prettier --check \"src/**/*.{js,vue,ts,css,scss,json,md}\""
  }
}
```

### 6.5 使用方法

```bash
# 格式化所有代码
npm run format

# 检查代码格式（不修改）
npm run format:check
```

---

## 七、ESLint代码检查配置

### 7.1 安装ESLint

```bash
npm install -D eslint eslint-plugin-vue
```

### 7.2 创建.eslintrc.cjs配置文件

```javascript
module.exports = {
  env: {
    browser: true,
    es2021: true,
    node: true
  },
  extends: [
    'eslint:recommended',
    'plugin:vue/vue3-recommended'
  ],
  parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module'
  },
  rules: {
    // 关闭一些严格的规则
    'vue/multi-word-component-names': 'off',
    'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off'
  }
}
```

### 7.3 在package.json添加检查命令

```json
{
  "scripts": {
    "lint": "eslint src --ext .vue,.js,.jsx,.cjs,.mjs --fix"
  }
}
```

### 7.4 使用方法

```bash
# 检查并自动修复代码
npm run lint
```

---

## 八、配置Vite

### vite.config.js完整配置

```javascript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import path from 'path'

// 自动导入Element Plus（可选）
import AutoImport from 'unplugin-auto-import/vite'
import Components from 'unplugin-vue-components/vite'
import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'

export default defineConfig({
  plugins: [
    vue(),
    // Element Plus自动导入
    AutoImport({
      resolvers: [ElementPlusResolver()]
    }),
    Components({
      resolvers: [ElementPlusResolver()]
    })
  ],

  // 路径别名
  resolve: {
    alias: {
      '@': path.resolve(__dirname, 'src'),
      '@components': path.resolve(__dirname, 'src/components'),
      '@views': path.resolve(__dirname, 'src/views'),
      '@api': path.resolve(__dirname, 'src/api'),
      '@utils': path.resolve(__dirname, 'src/utils'),
      '@store': path.resolve(__dirname, 'src/store'),
      '@assets': path.resolve(__dirname, 'src/assets')
    }
  },

  // 开发服务器配置
  server: {
    port: 5173,        // 端口号
    open: true,        // 自动打开浏览器
    cors: true,        // 允许跨域

    // 代理配置（解决跨域）
    proxy: {
      '/api': {
        target: 'http://localhost:3000',  // 后端服务器地址
        changeOrigin: true,
        rewrite: path => path.replace(/^\/api/, '')
      }
    }
  },

  // 构建配置
  build: {
    outDir: 'dist',           // 打包输出目录
    assetsDir: 'assets',      // 静态资源目录
    sourcemap: false,         // 不生成sourcemap
    minify: 'terser',         // 压缩方式
    chunkSizeWarningLimit: 1000,  // chunk大小警告限制（kb）

    // 代码分割
    rollupOptions: {
      output: {
        manualChunks: {
          'vue-vendor': ['vue', 'vue-router', 'pinia'],
          'element-plus': ['element-plus']
        }
      }
    }
  }
})
```

### 配置说明

**路径别名：** 可以用 `@` 代替 `src/`，方便导入

```javascript
// 不用别名
import Header from '../../components/Header.vue'

// 使用别名
import Header from '@/components/Header.vue'
```

**代理配置：** 解决开发时的跨域问题

```javascript
// 请求会自动转发
axios.get('/api/user')
// → 实际请求：http://localhost:3000/user
```

---

## 九、配置路由（Vue Router）

### 9.1 创建router/index.js

```javascript
import { createRouter, createWebHistory } from 'vue-router'

const routes = [
  {
    path: '/',
    name: 'Home',
    component: () => import('@/views/Home/index.vue')
  },
  {
    path: '/about',
    name: 'About',
    component: () => import('@/views/About/index.vue')
  },
  {
    path: '/login',
    name: 'Login',
    component: () => import('@/views/User/Login.vue')
  },
  {
    path: '/:pathMatch(.*)*',
    name: 'NotFound',
    component: () => import('@/views/NotFound.vue')
  }
]

const router = createRouter({
  history: createWebHistory(),
  routes
})

export default router
```

### 9.2 在main.js中使用

```javascript
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'

const app = createApp(App)
app.use(router)
app.mount('#app')
```

---

## 十、配置状态管理（Pinia）

### 10.1 创建store/index.js

```javascript
import { createPinia } from 'pinia'

const pinia = createPinia()

export default pinia
```

### 10.2 创建store/user.js

```javascript
import { defineStore } from 'pinia'
import { ref } from 'vue'

export const useUserStore = defineStore('user', () => {
  // 状态
  const userInfo = ref(null)
  const token = ref('')

  // 方法
  const setUserInfo = (info) => {
    userInfo.value = info
  }

  const setToken = (newToken) => {
    token.value = newToken
  }

  const logout = () => {
    userInfo.value = null
    token.value = ''
  }

  return {
    userInfo,
    token,
    setUserInfo,
    setToken,
    logout
  }
})
```

### 10.3 在main.js中使用

```javascript
import { createApp } from 'vue'
import App from './App.vue'
import pinia from './store'

const app = createApp(App)
app.use(pinia)
app.mount('#app')
```

### 10.4 在组件中使用

```vue
<script setup>
import { useUserStore } from '@/store/user'

const userStore = useUserStore()

// 获取状态
console.log(userStore.userInfo)

// 调用方法
userStore.setUserInfo({ name: '张三', age: 25 })
</script>
```

---

## 十一、封装Axios请求

### 创建utils/request.js

```javascript
import axios from 'axios'
import { ElMessage } from 'element-plus'

// 创建axios实例
const request = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,  // 从环境变量获取
  timeout: 10000  // 请求超时时间
})

// 请求拦截器
request.interceptors.request.use(
  config => {
    // 添加token
    const token = localStorage.getItem('token')
    if (token) {
      config.headers.Authorization = `Bearer ${token}`
    }
    return config
  },
  error => {
    console.error('请求错误:', error)
    return Promise.reject(error)
  }
)

// 响应拦截器
request.interceptors.response.use(
  response => {
    const { data, code, message } = response.data

    // 根据业务code做处理
    if (code === 200) {
      return data
    } else {
      ElMessage.error(message || '请求失败')
      return Promise.reject(new Error(message))
    }
  },
  error => {
    // 处理HTTP错误
    if (error.response) {
      switch (error.response.status) {
        case 401:
          ElMessage.error('未授权，请重新登录')
          // 跳转到登录页
          break
        case 404:
          ElMessage.error('请求的资源不存在')
          break
        case 500:
          ElMessage.error('服务器错误')
          break
        default:
          ElMessage.error(error.response.data.message || '请求失败')
      }
    } else {
      ElMessage.error('网络错误，请检查网络连接')
    }
    return Promise.reject(error)
  }
)

export default request
```

---

## 十二、完整的main.js示例

```javascript
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'
import pinia from './store'

// 样式
import '@/assets/styles/index.scss'

// 创建应用
const app = createApp(App)

// 使用插件
app.use(router)
app.use(pinia)

// 挂载
app.mount('#app')
```

---

## 十三、package.json完整示例

```json
{
  "name": "my-vue-app",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "build:test": "vite build --mode test",
    "build:prod": "vite build --mode production",
    "preview": "vite preview",
    "lint": "eslint src --ext .vue,.js,.jsx,.cjs,.mjs --fix",
    "format": "prettier --write \"src/**/*.{js,vue,ts,css,scss,json,md}\"",
    "format:check": "prettier --check \"src/**/*.{js,vue,ts,css,scss,json,md}\""
  },
  "dependencies": {
    "vue": "^3.4.0",
    "vue-router": "^4.2.0",
    "pinia": "^2.1.0",
    "axios": "^1.6.0",
    "element-plus": "^2.5.0",
    "dayjs": "^1.11.0",
    "lodash-es": "^4.17.0"
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^5.0.0",
    "vite": "^5.0.0",
    "sass": "^1.69.0",
    "eslint": "^8.55.0",
    "eslint-plugin-vue": "^9.19.0",
    "prettier": "^3.1.0",
    "unplugin-auto-import": "^0.17.0",
    "unplugin-vue-components": "^0.26.0"
  }
}
```

---

## 十四、常用命令总结

```bash
# 开发
npm run dev              # 启动开发服务器

# 构建
npm run build            # 打包生产环境
npm run build:test       # 打包测试环境
npm run preview          # 预览打包结果

# 代码检查
npm run lint             # ESLint检查并修复
npm run format           # Prettier格式化代码
npm run format:check     # 检查代码格式

# 依赖管理
npm install              # 安装所有依赖
npm install 包名          # 安装新依赖
npm install -D 包名       # 安装开发依赖
npm update               # 更新依赖
```

---

## 十五、VS Code推荐插件

在项目根目录创建 `.vscode/extensions.json`：

```json
{
  "recommendations": [
    "Vue.volar",                    // Vue3语法支持
    "dbaeumer.vscode-eslint",       // ESLint
    "esbenp.prettier-vscode",       // Prettier
    "bradlc.vscode-tailwindcss",    // Tailwind CSS
    "antfu.iconify",                // 图标预览
    "lokalise.i18n-ally"            // 国际化
  ]
}
```

---

## 十六、项目初始化完整流程

```bash
# 1. 创建项目
npm create vite@latest my-vue-app
cd my-vue-app

# 2. 安装依赖
npm install

# 3. 安装常用库
npm install vue-router@4 pinia axios element-plus
npm install -D sass prettier eslint eslint-plugin-vue
npm install -D unplugin-auto-import unplugin-vue-components

# 4. 创建目录结构
mkdir -p src/{api,assets/{images,styles,icons},components,composables,layout,plugins,router,store,utils,views}

# 5. 创建配置文件
touch .env .env.development .env.production
touch .prettierrc .prettierignore
touch .eslintrc.cjs

# 6. 初始化Git
git init
git add .
git commit -m "feat: 初始化项目"
git push  推送远程代码仓库

# 7. 启动项目
npm run dev
```

---

## 十七、常见问题

### Q1：Vite和Vue CLI有什么区别？

| 特性 | Vite | Vue CLI (webpack) |
|------|------|-------------------|
| 启动速度 | 极快（秒启动） | 慢（需要打包） |
| 热更新 | 极快 | 较慢 |
| 构建工具 | Rollup | Webpack |
| 配置 | 简单 | 复杂 |
| 推荐度 | 新项目首选 | 旧项目维护 |

### Q2：为什么环境变量要以VITE_开头？

Vite的安全机制，防止意外暴露敏感信息。只有`VITE_`开头的变量才会暴露给客户端代码。

### Q3：项目打包后文件很大怎么办？

```javascript
// 在vite.config.js中配置代码分割
build: {
  rollupOptions: {
    output: {
      manualChunks: {
        'vue-vendor': ['vue', 'vue-router', 'pinia'],
        'ui-vendor': ['element-plus']
      }
    }
  }
}
```

### Q4：开发时遇到跨域怎么办？

在 `vite.config.js` 配置代理：
```javascript
server: {
  proxy: {
    '/api': {
      target: 'http://localhost:3000',
      changeOrigin: true
    }
  }
}
```

---

## 总结

创建一个Vue3项目的核心步骤：

1. **创建项目**：`npm create vite@latest`
2. **安装依赖**：router、pinia、axios、UI库
3. **配置环境变量**：`.env.*` 文件
4. **配置Git**：`.gitignore` 忽略文件
5. **配置代码规范**：Prettier + ESLint
6. **配置Vite**：别名、代理、构建优化
7. **搭建目录结构**：按功能模块划分
8. **封装公共模块**：请求、路由、状态管理

按照这个流程，你就能快速搭建一个规范的Vue3项目了！
