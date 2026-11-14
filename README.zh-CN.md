<p align="center">
  <a href="https://flashdata.dev"><img src="https://flashdata.dev/logo.png" alt="FlashData 标志" width="72"></a>
</p>

<h1 align="center">FlashData</h1>

<p align="center"><strong>为开发者和 AI 智能体提供 Google 搜索与 YouTube 数据。</strong></p>

<p align="center">
  <a href="https://flashdata.dev/app/api-keys">获取 API 密钥</a> ·
  <a href="https://flashdata.dev/#playground">在线试用</a> ·
  <a href="https://flashdata.dev/docs">API 文档</a> ·
  <a href="https://flashdata.dev/mcp">MCP</a> ·
  <a href="./README.md">English</a>
</p>

## 快速开始

运行 SDK 示例前，请在环境变量 `FLASHDATA_API_KEY` 中设置从 [FlashData 账户](https://flashdata.dev/app/api-keys)获取的密钥。下方示例会输出 Google 搜索结果的标题和链接。数据请求消耗 [FlashData 点数](https://flashdata.dev/pricing)。

### Python

```sh
pip install flashdata
```

将下方代码保存为 `search.py`，然后运行 `python search.py`：

```python
import os
from flashdata import FlashData

with FlashData(api_key=os.environ["FLASHDATA_API_KEY"]) as client:
    response = client.google.search("battery recycling research", num=5)
    for page in response["results"]:
        for hit in page.get("organic", []):
            print(hit["title"], hit["link"])
```

### JavaScript / TypeScript

```sh
npm install @flashdata-dev/sdk
```

使用 Node.js 22 或更新版本，将下方代码保存为 `search.mjs`，然后运行 `node search.mjs`：

```javascript
import { FlashData } from '@flashdata-dev/sdk';

const client = new FlashData({ apiKey: process.env.FLASHDATA_API_KEY });
const response = await client.google.search({ query: 'battery recycling research', num: 5 });
for (const page of response.results) {
  for (const hit of page.organic ?? []) console.log(hit.title, hit.link);
}
```

### 命令行

```sh
uv tool install flashdata-cli
flashdata auth login
flashdata search "battery recycling research" --num 5
```

在隐藏输入提示中粘贴密钥。[安装指南](https://github.com/flashdatadev/flashdata-cli/blob/main/docs/installation.zh-CN.md)包含 Homebrew、APT、RPM 和独立二进制安装方式。配置智能体时，运行 `flashdata setup` 并按提示操作。

## 可以用来做什么？

- **搜索监测与资料发现：** 获取 Google 网页、新闻、图片、购物、视频和本地搜索结果。
- **YouTube 研究与数据集构建：** 查找视频，读取元数据、已有的转录文本或上传者字幕，并按视频 ID 列表导出结果。
- **批量媒体交付：** 将音频或视频保存到自己的云存储，并导出逐条交付结果。

## 选择接入方式

| 应用场景 | 从这里开始 |
| --- | --- |
| Python 脚本、Notebook 或数据流水线 | [Python SDK](https://github.com/flashdatadev/flashdata-python) |
| 使用 Python 下载 YouTube 视频、音频、片段或批量交付媒体 | [YouTube 视频下载 API 工具包](https://github.com/flashdatadev/youtube-video-download-api) |
| 按 ID 文件批量下载视频，跟踪进度、导出交付清单并单独重试失败项 | [Python 批量视频下载工具](https://github.com/flashdatadev/bulk-video-download) |
| Node.js 应用或服务 | [TypeScript / JavaScript SDK](https://github.com/flashdatadev/flashdata-typescript) |
| Go 服务或后台任务 | [Go SDK](https://github.com/flashdatadev/flashdata-go) |
| Shell 脚本或命令行批量任务 | [CLI](https://github.com/flashdatadev/flashdata-cli) |
| 通过 MCP 连接工具的智能体 | [托管 MCP 配置](https://flashdata.dev/mcp) · [MCP 服务端](https://github.com/flashdatadev/flashdata-mcp) |
| 使用可复用搜索和研究流程的智能体 | [智能体技能](https://github.com/flashdatadev/flashdata-skills) |

**需要帮助？** 请查阅 [API 文档](https://flashdata.dev/docs)，在对应仓库提交 Issue，或通过 [support@flashdata.dev](mailto:support@flashdata.dev) 联系账户支持。
