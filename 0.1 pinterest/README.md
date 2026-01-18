# ?? Pinterest Marketing Automation & AI Visual Engine
### ?? 赋能 [www.chinesename.us](https://www.chinesename.us) 的 AI 自动化内容生产流水线

本项目由 **Hellos AI** 开发，是一个高度自动化的内容营销引擎。它解决了 Pinterest 营销中“批量制图难”、“SEO 文案耗时”以及“内容重复率高”的痛点。通过集成 **飞书多维表格**、**DeepSeek 大模型**、以及 **Puppeteer 动态渲染技术**，实现从数据输入到图片生成、云端存储、最后数据回流的完整无人值守闭环。

---

## ?? 项目背景与目的 (Project Purpose)

为了提升 **chinesename.us** 在 Pinterest 上的流量转化，该工作流针对 **2026 马年 (Year of the Horse)** 进行了深度优化。它将繁琐的取名数据转化为极具美感的视觉名片，利用 AI 确保每一条 Pin 都具备极高的文化底蕴和搜索权重，助力品牌在全球市场出海。

---

## ?? 工作流核心架构 (Workflow Overview)

根据 `pinterest_automation_publish.json` 的逻辑配置，系统分为以下四个核心阶段：

### 1. 数据触发与获取 (Data Sourcing)
* **多源触发**：支持 `Manual Trigger` 手动执行或 `Schedule Trigger` 定时触发（预设每天 08:10 自动执行）。
* **飞书集成**：自动连接到 **飞书多维表格 (Feishu Bitable)**，通过 `Bitable:parseUrl` 节点检索状态为“初始”的任务记录，实现任务的精准抓取。

### 2. AI 智能内容大脑 (AI Content Engine)
* **核心模型**：集成 **DeepSeek Chat V3** (通过 n8n LangChain 架构)。
* **首席内容官模式**：AI 根据输入的性别、风格标签生成 20 组富有韵味的中文姓名，并自动输出符合 Pinterest 算法的标题、描述和 Alt 文本。
* **HTML 格式化**：AI 直接参与 HTML 结构的预处理，确保视觉展示与文化内涵深度统一。

### 3. 动态视觉工厂 (Visual Factory)
* **资源精准匹配**：查询 **n8n Data Table**，根据类别自动调取对应的背景底图路径和字体风格（针对 2026 马年定制）。
* **高保真渲染**：利用 HTML5 + CSS3 模板注入数据，通过 **Puppeteer** 模拟浏览器截取 2:3 比例 (1000x1500px) 的高分辨率图片。
* **防降权技术 (Anti-Detection)**：内置 JavaScript 干扰脚本，生成随机几何噪点、微调像素位置和背景缩放，确保每张图片的 **File Hash 唯一**，规避平台查重机制。

### 4. 云端分发与数据闭环 (Cloud & Integration)
* **对象存储**：生成的图片自动上传至 **Cloudflare R2**（S3 兼容模式）获取外链。
* **状态回写**：将生成的图片 URL、SEO 文案实时写回飞书，并将任务标记为“已发布”。
* **数据归档**：将批次数据汇总为 CSV 并上传至 **Google Drive**，方便进行长周期的营销效果分析。

---

## ??? 技术栈 (Tech Stack)

* **自动化平台**: n8n
* **营销目标**: [chinesename.us](https://www.chinesename.us)
* **数据管理**: Feishu Bitable (飞书), n8n Data Table
* **人工智能**: DeepSeek-V3 (via LangChain)
* **渲染技术**: HTML5, CSS3, Puppeteer (Headless Chrome)
* **云存储**: Cloudflare R2, Google Drive
* **监控系统**: SMTP Email (Sina Mail) 实时错误告警

---

## ?? 快速部署说明 (Setup Guide)

1. **导入工作流**：将 `pinterest_automation_publish.json` 导入你的 n8n 环境。
2. **环境依赖**：确保 n8n 所在的 Docker 容器安装了 `Puppeteer` 依赖库及中文系列字体（推荐 `fonts-noto-cjk`）。
3. **凭据配置**：在 n8n 后台配置以下 API 凭据：
   * Feishu API (多维表格权限)
   * DeepSeek API (内容生成)
   * AWS S3 API (用于 Cloudflare R2 存储)
   * Google Drive OAuth2
   * SMTP (用于告警)

---

## ?? 核心价值

> **“批量生产不代表流水线化，AI 可以实现高级定制。”**
> 
> 本项目通过“代码级随机干扰”技术和“AI 专家级取名逻辑”，让每一张 Pin 图在保持视觉高级感（Instagram-worthy）的同时，兼顾了文化准确性和 SEO 权重，是社交媒体自动化营销的实战级利器。

---

## ?? 关于作者与支持 (Contact & Support)

如果你对本项目感兴趣，或者想了解更多关于 AI 自动化营销的内容，欢迎通过以下频道联系我：

* **个人博客 (Blog)**: [https://hellosai.cc/](https://hellosai.cc/)
* **YouTube 频道**: [@hellos-ai](https://www.youtube.com/@hellos-ai)
* **GitHub**: [Hello AI 资源分享](https://github.com/tansunyj/my-n8n-sharing.git)

_?? Powered by **Hellos AI** Automation Flows_