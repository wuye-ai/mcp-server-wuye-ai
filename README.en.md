# CRIC Wuye AI MCP Server

--------------
[![NPM Version](https://img.shields.io/npm/v/%40wuye-ai%2Fmcp-server-wuye-ai)](https://www.npmjs.com/package/@wuye-ai/mcp-server-wuye-ai)
[![zh-CN](https://img.shields.io/badge/lang-zh--CN-red.svg)](https://github.com/wuye-ai/mcp-server-wuye-ai/blob/master/README.md)
[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/wuye-ai/mcp-server-wuye-ai/blob/master/README.en.md)

Available on |
[<img src="https://static-production.npmjs.com/b0f1a8318363185cc2ea6a40ac23eeb2.png" width="12" height="12" alt="NPM Logo"> **NPM**](https://www.npmjs.com/package/@wuye-ai/mcp-server-wuye-ai) |
[<img src="https://mcp.so/favicon.ico" width="12" height="12" alt="MCP.so Logo"> **MCP.so**](https://mcp.so/server/CRIC%E7%89%A9%E4%B8%9AAI/CRIC) |
[<img src="https://mcpservers.org/icon.png" width="12" height="12" alt="MCPServers.org Logo"> **MCPServers.org**](https://mcpservers.org/servers/wuye-ai/mcp-server-wuye-ai) |
[<img src="https://tcb.cloud.tencent.com/favicon.ico" width="12" height="12" alt="Tencent CloudBase Logo"> **Tencent CloudBase**](https://tcb.cloud.tencent.com/mcp-server/mcp-server-wuye-ai) |
[<img src="https://g.alicdn.com/sail-web/maas/2.8.5/favicon/128.ico" width="12" height="12" alt="ModelScope Logo"> **ModelScope**](https://modelscope.cn/mcp/servers/@wuye-ai/mcp-server-wuye-ai) |
[<img src="https://gw.alicdn.com/imgextra/i4/O1CN01vVn7g32134zNZEeAR_!!6000000006928-55-tps-24-24.svg" width="12" height="12" alt="Aliyun Bailian Logo"> **Aliyun Bailian**](https://bailian.console.aliyun.com/?tab=mcp#/mcp-market/detail/cric-wuye-ai) |
[<img src="https://agi-dev-platform-web.cdn.bcebos.com/ai_apaas/favicon.ico" width="12" height="12" alt="Baidu AI Cloud Logo"> **Baidu AI Cloud**](https://console.bce.baidu.com/ai_apaas/mcpServerCenter/mcp_t_cric_ai/detail) |
[<img src="https://gips3.baidu.com/it/u=1551671786,626435656&fm=3028&app=3028&f=PNG&fmt=auto&q=100&size=f300_315" width="12" height="12" alt="Baidu Search AI Logo"> **Baidu Search AI**](https://sai.baidu.com/server/CRIC?id=DZy6eHdoKx2v3gfThymJXf)

(More MCP platform integrations coming soon…)

--------------

## Overview

**CRIC Wuye AI** (CRIC物业AI) is an intelligent assistant developed by [CRIC](http://www.cricchina.com/) specifically for the property management industry. It was [officially launched](https://mp.weixin.qq.com/s/GC4V1M6N199Ay2f3kZan_Q) on April 25, 2025.

*P.S. Wuye (物业) means Property Management in Chinese.*

Leveraging a combination of industry knowledge base construction, multimodal large models, and RAG technology, **CRIC Wuye AI** integrates five core capability modules: **Industry Research**, **Laws & Regulations**, **Community Governance**, **Project Operations**, and **Content Writing**. It also expands into two smart agents focused on **News & Public Opinion** and **Talent Training** based on vertical industry knowledge.

## Core Capabilities

CRIC builds its competitive edge in the Wuye AI collaboration space through three main capabilities:

- **Data Asset Transformation:** Converts over 1 billion characters of industry text and terabytes of multimodal data into high-quality datasets tailored for the property sector, along with a custom industry data quality evaluation system to ensure accuracy and reliability.
- **Scenario Penetration:** Focused on 20+ vertical business scenarios in property management, leveraging targeted knowledge bases to enable precise matching.
- **Ecosystem Evolution:** Real-time monitoring of 500+ trusted information and data sources daily, processing over 100,000 real-time data updates. Achieves over 90% accuracy in areas like policy alerts, business opportunity mining, and tender analysis—creating a continuously evolving industry AI knowledge hub.

## MCP Server Features

**CRIC Wuye AI MCP Server** is a server-side implementation based on the [Model Context Protocol](https://modelcontextprotocol.io/), delivering part of the atomic capabilities of the **CRIC Wuye AI** platform. The current version provides the following main feature modules:

- **Daily News:** Retrieve the property management industry’s daily news report.
- **Knowledge Base:** Search the property management industry’s expertise knowledge bases.
- **Question Answering:** Ask questions to CRIC Wuye AI and receive answers, or let CRIC Wuye AI analyze questions related to property management issues.

Please check out the [Tool Definition & Configuration](./TOOLS.md) doc for detailed tool definitions. More features are coming soon. Stay tuned.

## CRIC Wuye AI Knowledge Bases

By using the CRIC Wuye AI MCP Server, you can query high-quality, domain-specific knowledge bases built by CRIC for the property management industry. These knowledge texts can be retrieved based on user queries to support AI responses.

Currently available knowledge bases include: **Laws and Regulations, Property Management Company Information, CRIC Rankings, Outstanding Property Service Cases, Industry Research, Emergency Response in Property Projects, Comprehensive Project Management, Complaint Handling, Legal Case Studies in Property Management, Non-Residential Property Management Research, and Property Management Case Studies**, among others.

## Obtaining an Access Token

To use the CRIC Wuye AI MCP Server, you must first obtain an **Access Token**. Please contact our support staff via email at [xuanao@cric.com](mailto:xuanao@cric.com).

## Getting Started

### 1. SSE Mode (http)

#### 1.1 Run

You can run your own MCP Server with HTTP mode enabled, or use the official URL we provide.

##### A. Self-hosted:

```bash
MODE=http PORT=3011 npx -y @wuye-ai/mcp-server-wuye-ai
```

After successful startup, your MCP Server URL is `http://localhost:3011/sse/mcp`.

##### B. Use Official:

Alternatively, you can use our official MCP Server URLs:

- Testing: `https://mcp.wuye-ai-staging.cricbigdata.com/sse/mcp`
- Production: `https://mcp.wuye-ai.cricbigdata.com/sse/mcp`

#### 1.2 Test

You can test the SSE MCP Server using MCP Inspector or third-party tools.

##### MCP Inspector:

Once the server is running, use [MCP Inspector](https://github.com/modelcontextprotocol/inspector) to test service status:

```bash
npx @modelcontextprotocol/inspector
```

After launching, open the Web UI in your browser (default: http://127.0.0.1:6274/) and configure the connection:

1. Set **Transport Type** to `SSE` and **URL** to the MCP Server URL obtained earlier.
2. Under **Authentication**, set **Header Name** to `Authorization` and **Bearer Token** to your **CRIC Wuye AI Access Token**.
3. Click **Connect**. Once connected, the left panel will show the connection status.

You can now use MCP Inspector to test CRIC Wuye AI MCP Server. See the [MCP Inspector Documentation](https://modelcontextprotocol.io/docs/tools/inspector) for more details.

##### Third-Party Tools:

When using SSE mode with other tools, set the `Authorization` header with your Access Token. For example, in [Cline](https://cline.bot/):

```json
{
  "mcpServers": {
    "CRIC-Wuye-AI": {
      "transportType": "sse",
      "url": "https://mcp.wuye-ai.cricbigdata.com/sse/mcp?name_en=true",
      "headers": {
        "Authorization": "Bearer {{Your Access Token}}"
      }
    }
  }
}
```

Note: Some tools using [@modelcontextprotocol/typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) may not properly apply HTTP headers ([known issue](https://github.com/modelcontextprotocol/typescript-sdk/issues/317)). As a workaround, you can also pass the token via the query string:

```json
{
  "mcpServers": {
    "CRIC-Wuye-AI": {
      "transportType": "sse",
      "url": "https://mcp.wuye-ai.cricbigdata.com/sse/mcp?name_en=true&token={{Your Access Token}}"
    }
  }
}
```

Also, setting the `name_en` query parameter to `true` will use English names for the tools, which is useful for non-Chinese users.

### 2. Stdio Mode

#### 2.1 Run

Stdio mode is also supported. To start the server:

```bash
CRIC_WUYE_AI_ACCESS_TOKEN={{Your Access Token}} npx -y @wuye-ai/mcp-server-wuye-ai
```

#### 2.2 Test

You can test using either third-party tools or MCP Inspector. Typically, Stdio mode does not require manual startup, as tools will start it automatically.

##### MCP Inspector:

To use Stdio in MCP Inspector:

1. Set **Transport Type** to `Stdio`, **Command** to `npx`, and **Arguments** to `-y @wuye-ai/mcp-server-wuye-ai`.
2. Under **Environment Variables**, set `CRIC_WUYE_AI_ACCESS_TOKEN` to your **Access Token**.
3. Click **Connect**. The Inspector will auto-run the server and connect.

You can now test CRIC Wuye AI MCP Server using MCP Inspector.

##### Third-Party Tools:

For Stdio access via third-party tools, specify the Access Token using the `CRIC_WUYE_AI_ACCESS_TOKEN` environment variable. For example, in Cline:

```json
{
  "mcpServers": {
    "CRIC-Wuye-AI": {
      "transportType": "stdio",
      "command": "npx",
      "args": [
        "-y",
        "@wuye-ai/mcp-server-wuye-ai"
      ],
      "env": {
        "CRIC_WUYE_AI_ACCESS_TOKEN": "{{Your Access Token}}"
      }
    }
  }
}
```

## Optional Configuration

You can configure how CRIC Wuye AI MCP Server runs via environment variables. Supported options:

| Environment Variable Parameter   | URL Query Parameter | Default                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------------------|---------------------|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MODE`                           | *Not Supported*     | `stdio`                                  | Run mode. Options: `stdio`, `http`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `HOSTNAME`                       | *Not Supported*     | `0.0.0.0`                                | Hostname for HTTP mode. `0.0.0.0` binds to all your IP addresses.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `PORT`                           | *Not Supported*     | `3011`                                   | Port for HTTP mode.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `CRIC_WUYE_AI_ACCESS_TOKEN`      | `token`             | *none*                                   | CRIC Wuye AI Access Token. If not provided, will use the `Authorization` HTTP header value.                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `CRIC_WUYE_AI_PROVIDER_API_BASE` | *Not Supported*     | `https://export.wuye-ai.cricbigdata.com` | Backend API base URL (***this is not the MCP Server URL***). Optional values: `https://export.wuye-ai-staging.cricbigdata.com` (testing) or `https://export.wuye-ai.cricbigdata.com` (production).                                                                                                                                                                                                                                                                                                                   |
| `CRIC_WUYE_AI_NAME_EN`           | `name_en`           | Preset for you by CRIC Wuye AI team      | Whether English tool names are used. Options: `true`, `false`. If set to `true`, English names will be used for the tools, which would be useful for non-Chinese users and improve compatibility with some non-Chinese models. We recommend to set this to `false` for models that support Chinese tool names, in order to get better performance. If set, the given value will override preset value.                                                                                                               |
| `CRIC_WUYE_AI_FEATURE_SET`       | `feature_set`       | Preset for you by CRIC Wuye AI team      | Pre-configured feature set of tools. Options: `base`, `detail` and more. This flag decides what set of tools are available for you. The `base` feature set includes `List Available Knowledge Bases` tool and a universal `Search Knowledge Base` tool. While the `detail` feature set does not provide the `List Available Knowledge Bases` tool, but will provide specialized `Search Knowledge Base` tools for every single knowledge base available for you. If set, the given value will override preset value. |
| `CRIC_WUYE_AI_OUTPUT_FORMAT`     | `output`            | `raw`                                    | Tool call output format. Options: `raw`(original), `text`(converted to Markdown text).                                                                                                                                                                                                                                                                                                                                                                                                                               |

*P.S.* To set URL query parameters, just append them to SSE URL, like:

```json
{
  "mcpServers": {
    "CRIC-Wuye-AI": {
      "transportType": "sse",
      "url": "https://mcp.wuye-ai.cricbigdata.com/sse/mcp?name_en=true&token={{Your Access Token}}"
    }
  }
}
```

For more information about `CRIC_WUYE_AI_NAME_EN` and `CRIC_WUYE_AI_FEATURE_SET`, please refer to the [Tool Definition & Configuration](./TOOLS.md) documentation.
