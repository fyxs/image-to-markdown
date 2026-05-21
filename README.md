# 图片转 Markdown 工具

将图片中的文字内容通过 OCR 识别并转换为结构化 Markdown 格式的纯前端 Web 工具。

## 功能

- **图片上传**：支持拖拽和点击选择，JPG/PNG/WebP 格式，最大 10MB
- **图片预览**：自动显示文件名、大小、尺寸
- **智能压缩**：大图自动压缩至 2560px 以内，保证 OCR 质量
- **图像预处理**：灰度化 → 对比度增强 → 自适应二值化 → 卷积锐化，提高识别率
- **OCR 识别**：Tesseract.js 引擎，中文简体 + 英文混合识别
- **Markdown 转换**：自动识别表格、标题、列表、代码块、粗体/斜体
- **格式工具栏**：手动调整标题级别、加粗、斜体、列表、表格、代码块
- **复制/下载**：一键复制到剪贴板或下载 `.md` 文件
- **结果持久化**：自动保存到 localStorage，刷新不丢失

## 使用

直接在浏览器打开 `index.html` 即可使用，无需任何构建步骤或服务器。

```
# 克隆或下载项目后
open index.html
```

## 技术栈

| 技术 | 用途 |
|------|------|
| [Tesseract.js](https://github.com/naptha/tesseract.js) v4 | OCR 文字识别（chi_sim + eng） |
| [Tailwind CSS](https://tailwindcss.com/) | UI 样式（CDN） |
| Canvas API | 图像预处理（灰度/对比度/二值化/锐化） |
| 原生浏览器 API | 文件读取、剪贴板、ObjectURL 预览、localStorage |

零构建、零依赖安装，所有库通过 CDN 加载。

## 项目结构

```
image-to-markdown/
├── index.html                 # 主应用
├── simple-test.html           # 图片选择功能测试
├── image-preview-test.html    # 图片预览功能测试
├── cors-test.html             # CORS 与 Tesseract 加载测试
├── ocr-fix-test.html          # OCR 流水线测试
├── test-fix.html              # 事件监听 / DOM 集成测试
├── test-ocr-optimization.html # 图像预处理步骤可视化对比
├── test-performance.html      # 图片处理性能测试
└── test-regex-fix.html        # 正则表达式修复验证
```

## 兼容性

现代浏览器（Chrome、Firefox、Edge、Safari）。剪贴板复制在 `https` 或 `localhost` 下使用 Clipboard API，其他环境自动回退到 `execCommand`。

## License

MIT
