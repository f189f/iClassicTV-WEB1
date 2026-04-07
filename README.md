# **📺 iClassicTV**

**iClassicTV** 是一款专为怀旧党和老旧 iOS 设备（如运行 iOS 6 的 iPhone 4 / 4s / iPad）打造的 **纯原生、零依赖、单文件** IPTV / M3U 直播源网页播放器。

它不仅仅是一个播放器，更是一次对那个充满**拟物化 (Skeuomorphism)** 时代精美 UI 的致敬。

## **✨ 核心特性**

* **🕰️ 极致的拟物化 UI:** 纯手工 CSS 还原了 iOS 6 标志性的蓝灰渐变导航栏、金属高光按钮、带内阴影的立体徽章 (Badge)、圆角 Table View 以及标志性的“尖角后退按钮”。  
* **📦 极限单文件 (Single-File):** 所有的 HTML、CSS 和 ES5 JavaScript 均打包在唯一的一个 index.html 文件中。无需 npm，无需构建工具（Webpack/Vite），**下载即用，离线可用**。  
* **🚀 零依赖 & 古董级兼容:** 不依赖任何第三方框架（没有 Vue/React，也没有 Video.js）。采用严格的 ES5 语法，原生利用 iOS 内置的 QuickTime HLS (.m3u8) 解码能力，完美流畅运行在十年前的老设备上。  
* **📺 智能 M3U 解析:**  
  * 支持从网络 URL 远程拉取或手动粘贴 M3U 内容。  
  * 自动提取 group-title 实现**频道二级分组**。  
  * 自动提取 tvg-logo 显示频道图标，自带断网容错内联 SVG 占位图。  
  * **🔥 同名多源智能合并:** 自动将同名频道的多个备用源合并，在播放页通过原生 iOS 3D 滚轮 (\<select\>) 进行无缝切源。  
* **✨ 丝滑的原生交互:**  
  * 引入自定义硬件加速 (-webkit-transform) 路由动画，实现符合空间直觉的左右视差滑动。  
  * 内置极简版 FastClick 逻辑，彻底终结早期 WebKit 臭名昭著的 **300ms 点击延迟**。  
* **📱 桌面 Web App 支持:** 完美适配 apple-mobile-web-app-capable，支持通过 Safari “添加到主屏幕” 获得全屏沉浸式体验。

## **🚀 快速开始**

### **方式一：直接运行 (本地/离线)**

由于项目是极其纯粹的单文件，你可以直接将仓库中的 index.html 下载到电脑或手机中，使用浏览器双击打开即可使用。

### **方式二：部署到服务器 (推荐)**

为了在真实的 iOS 老设备上顺畅访问并保存到桌面，建议通过 HTTP 访问：

1. 将 index.html 放入任何静态 Web 服务器（Nginx, Apache, GitHub Pages, Vercel 或本地 NAS）。  
2. 在 Safari 中输入网址访问。

### **💡 如何获得原生 App 体验？**

1. 在 iOS Safari 中打开本应用。  
2. 点击浏览器底部的 **分享 \[↑\]** 按钮。  
3. 选择 **“添加到主屏幕 (Add to Home Screen)”**。  
4. 回到桌面，点击那枚带有经典玻璃高光的图标，享受无地址栏的全屏原生体验！

## **📝 支持的 M3U 格式要求**

解析器极度宽容，但为了获得最佳的分组和多源合并体验，建议 M3U 源遵循以下包含 group-title 和 tvg-logo 的规范：

```m3u
#EXTM3U
#EXTINF:-1 tvg-logo="[https://example.com/cctv1.png](https://example.com/cctv1.png)" group-title="央视频道",CCTV-1 综合
[http://example.com/cctv1_line1.m3u8](http://example.com/cctv1_line1.m3u8)
#EXTINF:-1 tvg-logo="[https://example.com/cctv1.png](https://example.com/cctv1.png)" group-title="央视频道",CCTV-1 综合
[http://example.com/cctv1_line2.m3u8](http://example.com/cctv1_line2.m3u8)
#EXTINF:-1 group-title="卫视频道",湖南卫视
[http://example.com/hntv.m3u8](http://example.com/hntv.m3u8)
```

*(注：上述列表中两个 CCTV-1 会被自动合并为一个频道，并在播放页提供 2 个线路供选择)*

## **🛠 开发与修改**

代码完全开源且结构清晰。若需修改样式或逻辑，直接使用任何文本编辑器打开 index.html 即可。

* **CSS 部分:** 使用了大量的 \-webkit-linear-gradient 和 box-shadow: inset 来模拟 3D 质感。  
* **JS 部分:** 采用闭包和 DOM1 级事件保持向后兼容性。路由系统通过监听 className 配合 CSS3 动画实现。

## **🤝 贡献与反馈**

非常欢迎各位折腾老设备的同好提交 Issue 或 Pull Request！无论是优化正则表达式解析，还是进一步修复特定古董设备上的 CSS 渲染 bug。

## **📄 开源协议**

本项目基于 **MIT License** 开源。