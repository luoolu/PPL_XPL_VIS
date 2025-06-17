# PPL-XPL VIS

<p align="center">
  <img src="assets/ppl-xpl_highlight.gif" alt="PPL-XPL Highlight Demo GIF" />
</p>
<p align="center">
  <video controls autoplay loop muted width="800">
    <source src="assets/ppl-xpl_highlight.mp4" type="video/mp4">
    您的浏览器不支持视频播放，请 <a href="assets/ppl-xpl_highlight.mp4">点击这里观看</a>。
  </video>
</p>
<p align="center">
  <img src="assets/ppl-xpl-ins-vis.gif" alt="PPL-XPL Annotation Demo GIF" />
</p>
<p align="center">
  <video controls autoplay loop muted width="800">
    <source src="assets/PPL-XPL-INS-VIS.mp4" type="video/mp4">
    您的浏览器不支持视频播放，请 <a href="assets/PPL-XPL-INS-VIS.mp4">点击这里观看</a>。
  </video>
</p>

> **高性能、可交互的偏光／正交偏光（PPL/XPL）颗粒可视化工具**  
> 纯前端 HTML5 Canvas + JavaScript 实现，支持 LabelMe 标注与多帧 XPL 循环。

---

## ⛏️ 特性

- **多帧 XPL 支持**：一次性上传 6 张或更多角度的 XPL 图像，自动/手动循环显示。  
- **LabelMe JSON**：兼容 LabelMe 标注格式，多边形、矩形、圆形任意组合。  
- **高亮交互**：鼠标悬浮即时高亮、发光描边；“自动循环颗粒”按钮可一键遍历所有颗粒。  
- **局部暗化**：非高亮区域半透明暗化，突出目标颗粒。  
- **零依赖**：仅需 `index.html` + `assets/`，本地双击即可运行。

---

## 🚀 快速开始

1. 克隆仓库  
   ```bash
   git clone https://github.com/yourusername/PPL-XPL_VIS.git
   cd PPL-XPL_VIS
````

2. 本地预览

   * 直接双击打开 `index.html`（推荐 Chrome/Edge/Firefox）。
   * 或者用简单 HTTP 服务：

     ```bash
     python -m http.server 8080
     # 浏览器访问 http://localhost:8080/index.html
     ```

3. 上传文件

   * **PPL 图像**（单张）
   * **XPL 图像**（多选 6+ 张）
   * **LabelMe 标注 JSON**

   即可获得交互式可视化。

---

## ⚙️ 使用指南

1. **上传控件**

   * 点击或拖拽文件到控件区；
   * XPL 支持一次性多选。

2. **鼠标悬浮**

   * 在任意颗粒上移动，实时高亮并播放该区域的 XPL 帧循环。

3. **自动循环**

   * 点击“自动循环颗粒”按钮，依次高亮所有颗粒并循环对应 XPL；
   * 悬浮会立即打断自动模式。

4. **调节速度**

   * 拖动滑块实时调整 XPL 帧切换间隔（100–2000ms）。

---

## 🛠️ 开发者指南

* **结构说明**

  ```
  PPL-XPL_VIS/
  ├─ assets/
  │   ├─ ppl-xpl-highlight.gif
  │   └─ ppl-xpl-highlight.mp4
  └─ index.html
  ```

* **核心函数**

  * `toCanvasCoords(e)`：屏幕坐标 → Canvas 像素坐标，兼容视觉缩放。
  * `draw()`：PPL 渲染 → 全图暗化 → 区域打洞 → XPL 渲染 → 发光描边。
  * `restartFrameCycle()` & `startShapeCycle()`：分别管理 XPL 帧循环与颗粒循环。

* **本地调试**

  * 在 Chrome DevTools → Sources → “本地覆盖” 下编辑 `index.html` 即时预览。
  * CSS/JS 修改后刷新即可生效。

---

## 🎨 自定义与扩展

* **配色**：在 CSS 中调整 `.dark-mask` 或描边颜色。
* **标注格式**：扩展 JSON 解析逻辑以支持 COCO、LabelStudio 等。
* **插件化**：将渲染逻辑封装为 ES Module 或 React/Vue 组件。

---

## 💡 常见问题

* **Q**: XPL 不循环？

  * A：请确保至少上传 2 张 XPL；
  * A：滑块间隔不宜过短（1xx ms）或过长（2000 ms）。

* **Q**: JSON 未识别？

  * A：检查文件字段为 `shapes` 且每项含 `points` 数组。

* **Q**: 页面过暗？

  * A：未选中时不做暗化，仅在选中状态下覆盖半透明蒙版。

---

## 📄 许可证

本项目基于 **MIT License** 开源，详情见 [LICENSE](LICENSE)。
欢迎自由 Fork、Issue 与 PR！

---

<p align="center">_Powered by HTML5 Canvas & JavaScript · Geological Thin-Section Visualization_</p>

