<p align="center">
  <a href="https://flashdata.dev"><img src="https://flashdata.dev/logo.png" alt="FlashData logo" width="72"></a>
</p>

<h1 align="center">FlashData</h1>

<p align="center"><strong>Google Search and YouTube data for developers and AI agents.</strong></p>

<p align="center">
  <a href="https://flashdata.dev/app/api-keys">Get an API key</a> ·
  <a href="https://flashdata.dev/#playground">Playground</a> ·
  <a href="https://flashdata.dev/docs">Documentation</a> ·
  <a href="https://flashdata.dev/mcp">MCP</a> ·
  <a href="./README.zh-CN.md">简体中文</a>
</p>

## Get started

Set `FLASHDATA_API_KEY` in your environment for the SDK examples. Get a key from your [FlashData account](https://flashdata.dev/app/api-keys). The examples print Google result titles and links. Data requests use [FlashData credits](https://flashdata.dev/pricing).

### Python

```sh
pip install flashdata
```

Save as `search.py` and run `python search.py`:

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

With Node.js 22+, save as `search.mjs` and run `node search.mjs`:

```javascript
import { FlashData } from '@flashdata-dev/sdk';

const client = new FlashData({ apiKey: process.env.FLASHDATA_API_KEY });
const response = await client.google.search({ query: 'battery recycling research', num: 5 });
for (const page of response.results) {
  for (const hit of page.organic ?? []) console.log(hit.title, hit.link);
}
```

### Terminal

```sh
uv tool install flashdata-cli
flashdata auth login
flashdata search "battery recycling research" --num 5
```

Paste your key at the hidden prompt. See the [installation guide](https://github.com/flashdatadev/flashdata-cli/blob/main/docs/installation.md) for Homebrew, APT, RPM and standalone binaries. For agent setup, run `flashdata setup` and follow the prompts.

## What you can build

- **Search monitoring and source discovery:** Collect Google web, news, image, shopping, video and local results.
- **YouTube research and datasets:** Find videos, read metadata and available transcripts or uploader captions, and export results for a list of video IDs.
- **Bulk media delivery:** Send audio or video to your own cloud storage and export per-video delivery receipts.

## Choose an integration

| If you’re building… | Start here |
| --- | --- |
| A Python script, notebook or data pipeline | [Python SDK](https://github.com/flashdatadev/flashdata-python) |
| A Node.js application or service | [TypeScript / JavaScript SDK](https://github.com/flashdatadev/flashdata-typescript) |
| A Go service or worker | [Go SDK](https://github.com/flashdatadev/flashdata-go) |
| A shell script or a bulk workflow from your terminal | [CLI](https://github.com/flashdatadev/flashdata-cli) |
| An agent that connects to tools over MCP | [Hosted MCP setup](https://flashdata.dev/mcp) · [MCP server](https://github.com/flashdatadev/flashdata-mcp) |
| An agent that follows reusable search and research workflows | [Agent skills](https://github.com/flashdatadev/flashdata-skills) |

**Need help?** Start with the [API docs](https://flashdata.dev/docs), open an issue in the relevant repository, or email [support@flashdata.dev](mailto:support@flashdata.dev) for account support.
