# CLAUDE.md

本文档为 Claude Code (claude.ai/code) 在此代码库中工作提供指导。

## 项目概述

WordPress 小部件集合 — 可嵌入 WordPress 网站的小型 UI 组件。每个小部件都是独立的 HTML/CSS/JavaScript 文件。

## 架构

- **小部件结构**: 每个小部件是独立的 HTML 文件，包含内联 CSS 和 JavaScript
- **样式**: 使用 CSS 自定义属性（如 `var(--color-background-primary)`、`var(--border-radius-lg)`）继承 WordPress 主题样式
- **数据获取**: 通过 JSONP 回调从外部 API 获取数据，避免 CORS 问题
- **无需构建**: 小部件是纯 HTML/CSS/JS — 无需编译或打包

## 现有小部件

### `daily_english/daily_english.html`
显示爱词霸 (iciba.com) 的每日英语句子。功能：
- 日期选择器查询历史句子
- JSONP 回调模式处理跨域请求
- 响应式卡片布局，包含图片和文本内容
- SEO 优化：完整的 meta 标签、Open Graph、Twitter Card、结构化数据
- 动态页面标题：获取句子后自动更新为句子前 20 字
- 无障碍支持：ARIA 标签、语义化 HTML
- API 端点：`https://sentence.iciba.com/index.php?c=dailysentence&m=getdetail`

### `daily_english/embed_guide.html`
iframe 嵌入教程页面，指导用户如何在 WordPress 中嵌入每日英语句子。功能：
- 快速开始的代码示例
- 详细的 WordPress 添加步骤
- 效果预览
- 尺寸调整对照表
- FAQ 常见问题（Schema.org FAQPage 结构化数据）
- HowTo 结构化数据（教程步骤）

## 开发规范

- **JSONP 调用 API**: 使用回调模式（`callback=icibaCb_&timestamp`）请求外部 API
- **作用域 ID**: 所有 ID 使用唯一前缀（如 `dse-` 表示 Daily English），避免与 WordPress 主题冲突
- **IIFE 包装**: JavaScript 用 `(function(){ ... })();` 包装，避免全局作用域污染
- **SEO 优化**: 每个页面应包含完整的 meta 标签、结构化数据、语义化 HTML
- **无障碍**: 使用 ARIA 标签、alt 属性、语义化标签（main、article、header、footer）
- **iframe 嵌入**: 小部件设计为可通过 iframe 嵌入，推荐尺寸 280x300
