````markdown
# PPL-XPL VIS

[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](#license)  
![ppl-xpl highlight demo](assets/ppl-xpl-highlight.gif)

高性能、可交互的偏光／正交偏光（PPL/XPL）颗粒可视化工具，为岩心薄片分析、地质科研和教学场景量身打造。使用现代 Web 技术，支持多帧 XPL 角度循环、LabelMe JSON 标注、拖拽式文件上传及自动／手动高亮切换。

---

## 目录

- [⛏️ 特性](#️-特性)  
- [🚀 快速开始](#-快速开始)  
- [⚙️ 使用指南](#️-使用指南)  
- [🛠️ 开发者指南](#️-开发者指南)  
- [🎨 自定义与扩展](#-自定义与扩展)  
- [💡 常见问题](#-常见问题)  
- [📄 许可证](#-许可证)  

---

## ⛏️ 特性

- **多帧 XPL 支持**：一次性上传 6 张或更多角度的 XPL 图像，自动/手动循环显示。  
- **LabelMe JSON**：兼容 LabelMe 标注格式，自动解析多边形、矩形、圆形标注。  
- **高亮交互**：鼠标悬浮时即时高亮选区，自动循环按钮可遍历所有颗粒。  
- **区域暗化**：非高亮区域自动半透明暗化，突出显示目标颗粒。  
- **发光轮廓**：高亮区域描边并添加太空蓝发光效果。  
- **拖拽上传**：拖拽或点击选择本地文件，无需服务端依赖。  
- **零依赖纯前端**：仅需 `index.html` 及 `assets` 文件夹，即可本地打开。  

---

## 🚀 快速开始

1. 克隆仓库  
   ```bash
   git clone https://github.com/yourusername/PPL_XPL_VIS.git
   cd PPL_XPL_VIS
````

2. 预览 Demo

   * **浏览器打开**
     双击或右键在本地打开 `index.html`，推荐使用最新版本的 Chrome/Edge/Firefox。
   * **本地 HTTP 服务**

     ```bash
     # Python 3.x
     python -m http.server 8080
     # 然后访问 http://localhost:8080/index.html
     ```

3. 拖拽或选择以下文件：

   * **PPL 图像**（单张）
   * **XPL 图像**（可多选 6 张或更多）
   * **LabelMe 标注 JSON**

   成功后，页面将展示交互式可视化。

---

## ⚙️ 使用指南

1. **上传文件**
   ![upload-demo](assets/ppl-xpl-highlight.mp4)

   * 点击或拖拽文件到控件区；
   * 支持同时多选 XPL 图片。

2. **鼠标悬浮**

   * 将鼠标移入任意颗粒区域，即可即时高亮该颗粒并播放该区域的 XPL 帧循环。

3. **自动循环**

   * 单击 “自动循环颗粒” 按钮，依次高亮每个颗粒并播放对应 XPL。
   * 可随时鼠标悬浮打断自动模式，恢复手动高亮。

4. **调节速度**

   * 使用速度滑块实时调整 XPL 帧间隔。

---

## 🛠️ 开发者指南

* **项目结构**

  ```text
  PPL_XPL_VIS/
  ├─ assets/
  │   ├─ ppl-xpl-highlight.gif
  │   └─ ppl-xpl-highlight.mp4
  └─ index.html
  ```

* **核心逻辑**

  * `toCanvasCoords(e)`：坐标映射，确保 `ctx.isPointInPath()` 命中精准。
  * `draw()`：PPL 渲染 → 整图暗化 → 区域打洞 → XPL 渲染 → 发光描边。
  * `restartFrameCycle()` & `startShapeCycle()`：分别负责 XPL 帧循环与颗粒循环。

* **本地调试**

  1. 修改 `index.html` 交互或样式；
  2. 刷新浏览器即可查看效果；
  3. 推荐在 Chrome DevTools 中开启“启用本地覆盖”快速编辑并保存。

---

## 🎨 自定义与扩展

* **配色**：可在 CSS 中调整蒙版 `rgba(0,0,0,0.5)` 或描边 `deepskyblue`。
* **多通道叠加**：在 `draw()` 中插入自定义 WebGL/Canvas 滤镜，实现更多视觉效果。
* **标注格式**：扩展 JSON 解析，支持 COCO、LabelStudio 等多种标注。
* **插件化**：将渲染逻辑封装为 ES Module 或 React/Vue 组件，轻松集成到大型前端项目。

---

## 💡 常见问题

* **Q**: XPL 图片未循环？
  **A**: 请确保已同时上传至少 2 张 XPL 图片，并在选区内悬浮或启用自动循环。

* **Q**: 标注 JSON 无法识别？
  **A**: 检查 JSON 是否为 LabelMe 格式，或数组字段名为 `shapes`。

* **Q**: 页面过暗？
  **A**: 暗化仅在选中时生效，未选中时保持 PPL 原图亮度。

---

## 📄 许可证

本项目采用 [MIT License](LICENSE) 开源，欢迎自由使用、修改与分发。

---

> *Powered by HTML5 Canvas & JavaScript · Geological Thin-Section Visualization*

```
```
