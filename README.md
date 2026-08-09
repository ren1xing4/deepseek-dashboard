# 🐋 DeepSeek API 消费仪表盘

一个移动端优先的 DeepSeek API 消费可视化仪表盘，可安装到小米手机主屏幕作为小插件使用。

## ✨ 功能

- 💰 **余额展示** — 环形进度条 + 大字体余额显示
- 📊 **消费趋势** — 7天/30天/全部 折线图
- 🤖 **模型用量** — 各模型的 Token 和费用分布
- 📋 **历史记录** — 自动记录每次余额快照
- ✏️ **手动记录** — 支持手动录入 API 用量
- 🔄 **自动刷新** — 每小时自动获取余额
- 📱 **PWA 安装** — 可添加到手机主屏幕
- 🌙 **深色主题** — OLED 屏幕友好
- 🔒 **隐私安全** — API Key 仅存储在浏览器本地

## 🚀 部署方法

### 方法一：GitHub Pages（推荐，免费）

1. 在 GitHub 新建仓库，把这 3 个文件上传到仓库根目录
2. 进入仓库 Settings → Pages → Source 选 `main` 分支 → Save
3. 等待几分钟，获得 `https://你的用户名.github.io/仓库名` 地址
4. 在小米手机 Chrome 浏览器打开该地址
5. 点击浏览器菜单 → **「添加到主屏幕」**

### 方法二：本地预览

```bash
# 进入项目目录
cd deepseek-dashboard

# Python 方式（推荐）
python -m http.server 8080

# Node.js 方式
npx serve .

# 然后在手机浏览器打开 http://你的电脑IP:8080
```

> ⚠️ 注意：必须通过 HTTP 服务器访问（不能直接双击 HTML），否则无法调用 DeepSeek API。

### 方法三：Vercel / Netlify（免费）

直接拖拽项目文件夹到 [Vercel](https://vercel.com) 或 [Netlify](https://netlify.com) 即可部署。

## 📱 安装到小米手机

1. 在手机 Chrome 浏览器打开部署后的网址
2. 等待页面加载完成
3. 点击地址栏右侧的「⋮」→ **「添加到主屏幕」**
4. 确认添加，桌面就会出现 🐋 DeepSeek 图标
5. 点击图标即可像 App 一样使用

> 💡 **提示**：安装为 PWA 后，体验类似原生 App，有独立窗口，无需打开浏览器。

## ⚙️ 使用说明

### 首次使用

1. 点击右上角 ⚙️ 进入设置
2. 输入你的 DeepSeek API Key（从 [platform.deepseek.com](https://platform.deepseek.com) 获取）
3. 点击保存，仪表盘会自动获取余额

### 查看消费

- **余额卡片**：环形进度条显示已消耗比例（相对于首次记录的初始余额）
- **今日/本周/本月**：点击可切换趋势图时间范围
- **消费趋势图**：折线图展示余额变化
- **模型分布**：手动记录各模型用量后显示

### 手动记录用量

在「手动记录用量」区域：
1. 选择模型（deepseek-chat / deepseek-reasoner）
2. 输入消耗的 Token 数
3. 输入对应费用（¥）
4. 点击「记录」

### 自动刷新

在设置中开启「自动刷新」后，每小时自动获取一次余额。

## 🔑 获取 API Key

1. 访问 [platform.deepseek.com](https://platform.deepseek.com)
2. 注册/登录账号
3. 进入「API Keys」页面
4. 创建新的 API Key
5. 复制并粘贴到仪表盘设置中

## 📊 DeepSeek 定价参考

| 模型 | 输入 (¥/1M tokens) | 输出 (¥/1M tokens) |
|------|---------------------|---------------------|
| deepseek-chat | 1 | 2 |
| deepseek-reasoner | 4 | 16 |

*定价可能在仪表盘设置中自定义修改*

## 🛠 技术栈

- 纯 HTML/CSS/JS，无框架依赖
- Chart.js 图表库（CDN 加载）
- PWA（Service Worker + Manifest）
- localStorage 数据持久化

## ⚠️ 注意事项

- API Key **仅保存在浏览器本地**，不会上传到任何服务器
- 消费趋势依赖于多次刷新产生的余额快照，首次使用需要积累数据
- 模型用量分布需要手动记录，DeepSeek 暂未提供按模型分拆的用量 API
- 余额查询调用的是 DeepSeek 官方 API：`GET https://api.deepseek.com/user/balance`
