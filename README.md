# WordPress Widgets

WordPress 小部件集合 — 可嵌入 WordPress 网站的小型 UI 组件。

## 项目概述

每个小部件都是独立的 HTML/CSS/JavaScript 文件，无需构建工具，直接嵌入即可使用。

## 小部件列表

### 1. 每日英语句子 (`daily_english_iciba.html`)

爱词霸每日英语句子展示小部件。

**功能特性：**
- 显示每日英语句子及配图
- 日期选择器查询历史句子
- JSONP 跨域请求
- 响应式卡片布局

**设计特点：**
- 深绿色渐变头部
- 毛玻璃效果日期徽章
- 悬停动画按钮
- 内容左侧装饰边框

**API 端点：** `https://sentence.iciba.com/index.php?c=dailysentence&m=getdetail`

## 开发规范

- **作用域 ID**: 所有 ID 使用唯一前缀（如 `dse-`），避免与 WordPress 主题冲突
- **IIFE 包装**: JavaScript 用 `(function(){ ... })();` 包装，避免全局污染
- **JSONP 调用**: 使用回调模式处理跨域 API 请求
- **CSS 自定义属性**: 使用 `var(--color-*)`、`var(--border-radius-*)` 继承主题样式
