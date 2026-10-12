# 📖 电子阅读器 (E-Reader)

一个使用 Vue 3 + Vite 构建的轻量级电子阅读器示例，支持书架展示、搜索筛选与阅读视图。

## ✨ 功能

- 📚 书架展示（书籍封面、标题、作者、阅读进度）
- 🔍 实时搜索（按书名/作者）
- 📖 阅读页面（点击书籍进入）
- 🎨 简洁的纸质风格 UI

## 🛠 技术栈

- Vue 3 (Composition API)
- Vite 5
- 原生 CSS（无 UI 框架）

## 🚀 本地开发

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build
```

开发服务器默认运行在 `http://localhost:5173/`。

## 📁 项目结构

```
电子阅读器/
├── public/          # 静态资源
├── src/
│   ├── App.vue      # 主组件（书架 + 阅读视图）
│   ├── main.js      # 入口
│   └── style.css    # 全局样式
├── index.html
├── vite.config.js
└── package.json
```

## 📝 后续计划

- [ ] 添加章节分页与翻页
- [ ] 字体大小/主题切换
- [ ] 书签与笔记
- [ ] 本地存储阅读进度
- [ ] 支持导入 EPUB/TXT

## 📄 许可证

MIT