## 🎨 主题代码 (Theme Code)

将以下所有 CSS 代码复制到 Cherry Studio 的自定义样式文件中即可生效。

```css
/* --- Liuli-Theme v1.0 --- */
/* A clear and elegant theme for Cherry Studio, featuring glassmorphism and subtle blues. */

/*** 全局字体与基础设定 ***/
body {
  font-family: "LXGW WenKai", 'MiSans Normal', Product Sans, Noto Sans SC, system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif !important;
  font-weight: 600;
  line-height: 1.5 !important;
  letter-spacing: 0.015em !important;
}

[class^="CodeBlockWrapper"], [class^="cm"] {
  * { font-family: Maple Mono NF CN Medium !important; }
}

/*** 1. 核心视觉变量 (可在此处轻松自定义主题) ***/
:root {
  /* -- 布局 -- */
  --assistants-width: 200px !important; /* 左侧边栏宽度 */

  /* -- 圆角 -- */
  --radius-large: 20px; /* 用于气泡和输入框 */
  --radius-medium: 12px; /* 用于内部元素，如代码块 */

  /* -- 过渡动画 -- */
  --transition-fast: all 0.2s ease-out;

  /* -- 主题色 (亮色模式) -- */
  --theme-bg-primary: #f7f7f8;      /* 主要背景色 */
  --theme-bg-secondary: #ffffff;   /* 气泡背景 */
  --theme-text-primary: #1f1f1f;     /* 主要文字颜色 */
  --theme-text-secondary: #6b6b6b;   /* 次要文字颜色 */
  --theme-border-color: #e5e5e5;      /* 边框颜色 */
  --theme-accent-color: #4a72ff;     /* 强调色 (链接、图标等) */
  --theme-shadow-color: rgba(0, 0, 0, 0.05); /* 阴影颜色 */

  /* -- 主题色 (暗色模式变量，稍后在 dark 模式下覆盖) -- */
  --dark-bg-primary: #1e1e1e;
  --dark-bg-secondary: #2a2a2a;
  --dark-bg-user: #2a2c3a;
  --dark-text-primary: #e5e5e5;
  --dark-text-secondary: #9e9e9e;
  --dark-border-color: rgba(255, 255, 255, 0.1);
  --dark-accent-color: #6b8fff;
  --dark-shadow-color: rgba(0, 0, 0, 0.25);
}


/*** 2. 消息气泡美化 ***/
.message-content-container {
  background-color: var(--theme-bg-secondary) !important;
  border: 1px solid var(--theme-border-color) !important;
  border-radius: var(--radius-large) !important;
  box-shadow: 0 4px 12px var(--theme-shadow-color) !important; /* 更柔和的阴影 */
  margin: 12px 0 !important; /* 稍微拉开间距 */
  padding: 40px 48px  24px 48px !important; /* 调整内边距 */
  transition: var(--transition-fast) !important;
  overflow: hidden; /* 防止内部元素溢出圆角 */
}

/* 用户发送的气泡，使用不同的背景色以区分 */
.message-user .message-content-container {
  background-color: var(--theme-bg-user) !important;
  box-shadow: 0 2px 8px var(--theme-shadow-color) !important; /* 用户的阴影可以更轻微 */
}

/* 鼠标悬停在气泡上时，有一个轻微的上浮效果 */
.message-content-container:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px var(--theme-shadow-color) !important;
}


/*** 3. 输入框美化 (毛玻璃效果增强) ***/
#inputbar {
  background: rgba(255, 255, 255, 0.6) !important; /* 降低不透明度，让模糊更明显 */
  backdrop-filter: blur(16px) saturate(1.2) !important; /* 增强模糊和饱和度 */
  border: 1px solid rgba(255, 255, 255, 0.2) !important; /* 使用半透明白色作为边框，更有玻璃感 */
  border-radius: var(--radius-large) !important;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1) !important;
  margin: 16px !important; /* 调整外边距 */
  padding: 8px; /* 给内部图标留出空间 */
}


/*** 4. 暗色模式 (Dark Mode) 样式覆盖 ***/
body[theme-mode='dark'] {
  /* 在这里，把亮色模式的变量值，替换为暗色模式的专属值 */
  --theme-bg-primary: var(--dark-bg-primary);
  --theme-bg-secondary: var(--dark-bg-secondary);
  --theme-bg-user: var(--dark-bg-user);
  --theme-text-primary: var(--dark-text-primary);
  --theme-text-secondary: var(--dark-text-secondary);
  --theme-border-color: var(--dark-border-color);
  --theme-accent-color: var(--dark-accent-color);
  --theme-shadow-color: var(--dark-shadow-color);
  
  /* 同时覆盖文字颜色 */
  --color-text: var(--dark-text-primary) !important;
  --chat-text-user: var(--dark-text-primary) !important;
}

/* 针对暗色模式下的输入框进行微调 */
body[theme-mode='dark'] #inputbar {
  background: rgba(42, 42, 42, 0.6) !important;
  border-color: rgba(255, 255, 255, 0.1) !important;
  box-shadow: 0 8px 32px var(--dark-shadow-color) !important;
}
