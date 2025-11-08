# Cherry Studio Claude Dynamic style
**使用[CherryStudio](https://github.com/CherryHQ/cherry-studio)知识库，对仿Claude样式主题进行了改进，添加圆角设置，优化背景配色，优化动态交互效果。 **  

**Utilizing the CherryStudio knowledge base, enhancements were made to the Claude-style theme: added rounded corner settings, optimized background color scheme, and improved dynamic interaction effects.**  


![image](https://github.com/user-attachments/assets/7bbeacdd-375b-4ee7-9b1a-b3ffd76d24e4)

![image](https://github.com/user-attachments/assets/4e4a8f37-586d-4cb7-a1f6-e95edf53be2a)

https://github.com/user-attachments/assets/99fc8bc6-2a4a-4fcf-88be-1fe0e4b958a9

### 参考：  
>吉伊卡哇[吉伊卡哇](https://cherry-ai.com/css)  
>忘了从哪里找的Claude风格  
>霞鹜文楷 GB 屏幕阅读版-[GitHub](https://github.com/lxgw/LxgwWenKai-Screen)  
>Maple Mono NL CN-[GitHub](https://github.com/subframe7536/maple-font)  
---

[原始聊天文档](https://github.com/bjl101501/CherryStudio-Claudestyle-dynamic/blob/main/chat.md)  
[零基础简易修改主题方法](https://github.com/bjl101501/CherryStudio-Claudestyle-dynamic/blob/main/dev.md)  

---
**当前适配：Cherry Studio **
### CSS  
```css
/* ======================== 全局主题变量定义 ======================== */
:root {
    --chat-background-white: #FDF9F3;
    --color-border: rgba(139, 115, 85, 0.12) !important;
}

/* 全局样式设置 - 设置基本字体、行高、字母间距和字体粗细 */
* {
    font-family: "霞鹜文楷 GB 屏幕阅读版", system-ui !important;
    line-height: 1.7 !important;
    letter-spacing: 0.018em !important;
    font-weight: 500;
}

/* 确保代码块内的文本使用正确字体 */
pre *, code *, kbd, samp, tt {
    font-family: "Maple Mono NL CN", monospace !important;
}

.markdown * code {
    color: rgb(203,64,66);
    font-family: "Maple Mono NL CN", monospace !important;
}

/* 浅色模式颜色定义 - 采用Claude的色调，背景色使用第二个CSS */
body[theme-mode=light] {
    --color-primary: #C96442 !important;
    --color-primary-soft: rgba(201, 100, 66, 0.6);
    --color-primary-mute: rgba(201, 100, 66, 0.2);
    --color-background: #FDF9F3;       /* 侧边栏背景色 - 使用第二个CSS的背景 */
    --color-background-mute: #F5F0E8;  /* 略深的背景色 - 使用第二个CSS */
    --color-background-soft: #F9F4EC;  /* 中浅色背景 - 使用第二个CSS */
    --navbar-background: #FDF9F3;      /* 导航栏背景色 - 使用第二个CSS */
    --chat-background: #FDF9F3;        /* 聊天区域总体背景 - 使用第二个CSS */
    --chat-background-white: #FDF9F3;  /* 聊天背景 - 使用第二个CSS */
    --chat-background-user: #F5F0E8;   /* 用户消息气泡背景色 - 使用第二个CSS */
    --chat-background-assistant: #FDF9F3; /* AI助手消息气泡背景色 - 使用第二个CSS */
    --color-text: #262624;             /* 文字颜色（深色） */
    --color-border: rgba(139, 115, 85, 0.15); /* 边框颜色 - 使用第二个CSS */
}

/* 深色模式颜色定义 - 融合Claude深色主题，背景色使用第二个CSS */
body[theme-mode=dark] {
    --color-primary: #C96442 !important;          /* 保持主色调一致 */
    --color-primary-soft: rgba(201, 100, 66, 0.6);
    --color-primary-mute: rgba(201, 100, 66, 0.2);
    --color-background: #1E1C1A;       /* Claude深色背景色 - 使用第二个CSS */
    --color-background-mute: #2A2722;  /* 略浅的背景色 - 使用第二个CSS */
    --color-background-soft: #141210;  /* 中等深色 - 使用第二个CSS */
    --navbar-background-mac: rgba(30, 28, 26, 0.85); /* Mac导航栏半透明背景 */
    --navbar-background: #262422;      /* 导航栏背景色 - 使用第二个CSS */
    --chat-background: #1E1C1A;        /* 聊天区域总体背景 - 使用第二个CSS */
    --chat-background-white: #1E1C1A;  /* 深色背景 - 使用第二个CSS */
    --chat-background-user: #141210;   /* 用户消息背景 - 使用第二个CSS */
    --chat-background-assistant: #1E1C1A; /* AI助手消息背景 - 使用第二个CSS */
    --color-border: rgba(200, 180, 150, 0.15); /* 边框颜色 - 使用第二个CSS */
    --chat-text-user: #e8e6de;         /* 用户消息文字颜色 */
    --color-text: #bdbcb8;             /* 全局文字颜色 */
}

/* Claude 样式的消息容器 - 添加动态效果和第二个CSS的倒角 */
.message-content-container {
    background: var(--chat-background-white) !important;
    margin: 8px 0 !important;
    padding: 10px 10px 0 10px !important;
    transition: transform 0.22s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s ease !important;
    border: 1px solid var(--color-border) !important;
    border-radius: 12px !important; /* 添加第二个CSS的倒角 */
    box-shadow: none !important;
    opacity: 0;
    animation: fadeIn 0.5s ease-out forwards;
}

body[theme-mode='dark'] .markdown {
    color:  var(--chat-text-user) !important;
}

.message-content-container:hover {
    transform: translateY(-2px); /* 悬停时轻微上移 */
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05) !important; /* 悬停时添加阴影 */
}

@keyframes fadeIn {
    to {
        opacity: 1;
    }
}

.message-user .message-content-container {
    background: var(--chat-background-user) !important;
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.03) !important;
    border: 1px solid var(--color-border) !important;
    border-radius: 12px !important; /* 添加第二个CSS的倒角 */
    transition: transform 0.22s cubic-bezier(0.34,1.56,0.64,1), box-shadow 0.3s ease !important;
}

.message-user .message-content-container:hover {
    transform: translateY(-2px); /* 悬停时轻微上移 */
    box-shadow: 0 12px 40px -10px rgba(0,0,0,0.05) !important;
}

/* 深色模式下的消息容器 */
body[theme-mode='dark'] .message-content-container {
    background: var(--chat-background-assistant) !important;
    box-shadow: none !important;
    border: 1px solid var(--color-border) !important;
    border-radius: 12px !important; /* 添加第二个CSS的倒角 */
}

body[theme-mode='dark'] .message-content-container:hover {
    box-shadow: 0 4px 12px rgba(255, 255, 255, 0.05) !important;
}

body[theme-mode='dark'] .message-user .message-content-container {
    background: var(--chat-background-user) !important;
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.3) !important;
    border: 1px solid var(--color-border) !important;
    border-radius: 12px !important; /* 添加第二个CSS的倒角 */
}

body[theme-mode='dark'] .message-user .message-content-container:hover {
    box-shadow: 0 12px 40px -10px rgba(255,255,255,0.05) !important;
}

/* 输入框样式 - 增强动态效果，添加第二个CSS的倒角 */
#inputbar {
    margin: 0px 10px 10px 10px;
    background: #FFFFFF !important; /* 纯白色输入框背景 */
    border: 1px solid var(--color-border) !important;
    border-radius: 16px !important; /* 使用第二个CSS的倒角值 */
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.03) !important;
    transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
}

#inputbar:hover {
    transform: scale(1.02); /* 悬停时缩放 */
    box-shadow: 0 12px 40px -10px rgba(255, 107, 107, 0.1); /* 增强阴影 */
    border: 1px solid rgba(0, 0, 0, 0.6) !important;
    border-color: var(--color-primary-mute); /* 边框颜色微变 */
}

#inputbar:focus-within {
    transform: scale(1.01); /* 焦点时略微缩放 */
    box-shadow: 0 8px 24px -8px rgba(201, 100, 66, 0.15); /* 焦点时阴影增强 */
    border: 1px solid rgba(0, 0, 0, 0.6) !important;
    border-color: var(--color-primary-soft); /* 边框颜色变化 */
}

body[theme-mode='dark'] #inputbar {
    background: #30302E !important; /* 暗色模式下的输入框背景 */
    border: 1px solid var(--color-border) !important;
    box-shadow: 0 8px 32px -12px rgba(0,0,0,0.3) !important;
}

body[theme-mode='dark'] #inputbar:hover {
    transform: scale(1.02);
    box-shadow: 0 12px 40px -10px rgba(255, 107, 107, 0.1);
    border: 1px solid rgba(255, 255, 255, 0.7) !important;
    border-color: var(--color-primary-mute);
}

body[theme-mode='dark'] #inputbar:focus-within {
    transform: scale(1.01);
    box-shadow: 0 8px 24px -8px rgba(201, 100, 66, 0.2);
    border: 1px solid rgba(255, 255, 255, 0.7) !important;
    border-color: var(--color-primary-soft);
}

/* Bug fixes */
.bubble * .message-action-button:hover {
    background-color: var(--color-background-mute); /* 使用背景色变量修复悬停效果 */
    transform: scale(1.1); /* 悬停时轻微放大 */
    transition: transform 0.2s ease, background-color 0.2s ease;
}
body[theme-mode='dark'] .bubble * .message-action-button:hover {
    background-color: var(--color-background-mute); /* 使用背景色变量修复悬停效果 */
    transform: scale(1.1); /* 悬停时轻微放大 */
    transition: transform 0.2s ease, background-color 0.2s ease;
}

/* ======================== Ant Design 组件样式调整 - 添加动态效果 ======================== */
/* 按钮样式 */
.ant-btn-primary {
    background-color: var(--color-primary) !important;
    border-color: var(--color-primary) !important;
    color: #f2f2f2 !important;
    transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.3s ease;
}

.ant-btn-primary:hover, .ant-btn-primary:focus {
    background-color: var(--color-primary) !important;
    border-color: var(--color-primary-soft) !important;
    color: #FFFFFF !important;
    transform: translateY(-1px); /* 悬停时轻微上移 */
    box-shadow: 0 4px 12px rgba(201, 100, 66, 0.3) !important; /* 悬停时阴影增强 */
}

.ant-btn-primary:active {
    transform: translateY(1px); /* 点击时下沉 */
    box-shadow: 0 2px 6px rgba(201, 100, 66, 0.2) !important;
}

.ant-btn-variant-outlined {
    color: var(--color-primary) !important;
    border-color: var(--color-primary) !important;
    transition: color 0.3s ease, border-color 0.3s ease, transform 0.2s ease;
}

.ant-btn-variant-outlined:hover, .ant-btn-variant-outlined:focus {
    color: var(--color-primary-hover) !important;
    border-color: var(--color-primary-hover) !important;
    transform: translateY(-1px); /* 悬停时轻微上移 */
}

/* 选项卡样式 */
.ant-tabs-tab {
    transition: color 0.3s ease, transform 0.2s ease;
}

.ant-tabs-tab:hover {
    color: var(--color-primary-soft) !important;
    transform: translateY(-1px); /* 悬停时轻微上移 */
}

.ant-tabs-tab.ant-tabs-tab-active .ant-tabs-tab-btn {
    color: var(--color-primary) !important;
}

/* 滑块样式 - 参考材料中的动态效果 */
:where(.css-r9lahv).ant-slider {
    transition: all 0.3s ease;
}

:where(.css-r9lahv).ant-slider:hover .ant-slider-track {
    background-color: var(--color-primary-soft) !important; /* 悬停时颜色变化 */
}

:where(.css-r9lahv).ant-slider .ant-slider-handle::after {
    box-shadow: 0 0 0 2px var(--color-primary) !important;
    transition: box-shadow 0.3s ease, transform 0.2s ease;
}

:where(.css-r9lahv).ant-slider .ant-slider-handle:hover::after,
:where(.css-r9lahv).ant-slider .ant-slider-handle:focus::after {
    box-shadow: 0 0 0 2.5px var(--color-primary-soft) !important;
    transform: scale(1.1); /* 悬停或焦点时放大 */
}
```
  

--- 
