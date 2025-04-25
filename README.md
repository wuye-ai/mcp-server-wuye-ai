# CRIC物业AI MCP Server

--------------
[![zh-CN](https://img.shields.io/badge/lang-zh--CN-red.svg)](https://github.com/wuye-ai/mcp-server-wuye-ai/blob/master/README.md)
[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/wuye-ai/mcp-server-wuye-ai/blob/master/README.en.md)

已上架：[**[NPM]**](https://www.npmjs.com/package/@wuye-ai/mcp-server-wuye-ai) [**[MCP.so]**](https://mcp.so/server/CRIC%E7%89%A9%E4%B8%9AAI/CRIC)

（更多MCP平台陆续上架中……）

--------------

## 简介

**CRIC物业AI** 是 [克而瑞](http://www.cricchina.com/) 专为物业行业打造的智能 AI 助理，于2025年4月25日 [正式发布](https://mp.weixin.qq.com/s/GC4V1M6N199Ay2f3kZan_Q)。

**CRIC物业AI** 通过行业知识库建设，结合多模态大模型 + RAG 技术，集成五大核心能力模块：**行业研究**、**法律法规**、**社区治理**、**项目经营**、**文案写作**，并在行业垂类知识基础上，拓展了 **资讯舆情** 和 **人才培训** 两大智能体。

## 核心能力

克而瑞通过三个能力来构建其自身在物业AI合作领域优势：

- **数据资产转化能力：** 将10亿字行业语料、TB级多模态数据转化为物业行业的高质量数据集，并构建了一套行业数据质量评估体系，保障准确率和可信度；
- **场景穿透能力：** 聚焦20+物业行业垂直业务场景，定向选用对应领域知识库，精准匹配；
- **生态进化能力：** 通过每日实时监测超过500+可信资讯和数据来源，处理10万+实时数据的自更新系统，在政策预警、商机挖掘和招投标分析等环节实现准确率突破90%，形成行业AI知识中枢的持续升级。

## MCP Server 功能

**CRIC物业AI MCP Server** 是一个基于 [Model Context Protocol](https://modelcontextprotocol.github.io/) 的服务端实现，基于 **CRIC物业AI** 平台的部分原子能力，目前版本提供了以下功能（Tool）：

- **获取资讯日报：** 根据 YYYY-MM-DD 形式的日期，获取当日物业行业资讯日报。
- **获取行业热点问题列表：** 获取当前 CRIC物业AI 应用内物业行业热点问题的分类和列表。
- **获取可用知识库列表：** 获取可用知识库列表，后续可以使用其中的知识库搜索相关知识。
- **搜索知识库：** 指定具体知识库 ID，以及具体查询的问题，获取知识库搜索结果，以文档片段或全文形式返回，供 AI 参考。

更多能力即将推出，敬请期待。

## 获取 Access Token

您需要先获取 **CRIC物业AI Access Token** 才能使用 CRIC物业AI MCP Server 的功能。请联系我们的客服人员申请，联系邮箱：[xuanao@cric.com](mailto:xuanao@cric.com) 。

## 快速开始

### 1. SSE 方式（http）

#### 1.1 运行

您可以自行运行一个 MCP Server 并启用 HTTP 模式，或者直接使用我们提供的 URL。

##### A. 自行运行：

```bash
MODE=http PORT=3011 npx -y @wuye-ai/mcp-server-wuye-ai
```

运行成功后，MCP Server URL 为 `http://localhost:3011/sse/mcp` 。

##### B. 使用官方：

或者您也可以直接使用我们的官方的 MCP Server URL：

- 测试环境：`https://mcp.wuye-ai-staging.cricbigdata.com/sse/mcp`
- 生产环境：`https://mcp.wuye-ai.cricbigdata.com/sse/mcp`

#### 1.2 测试

您可以使用 MCP Inspector 或第三方工具连接 SSE 方式的 MCP Server。

##### MCP Inspector：

服务运行成功后，您可以运行 [MCP Inspector](https://github.com/modelcontextprotocol/inspector) 来查看并测试服务是否正常运行。

```bash
npx @modelcontextprotocol/inspector
```

MCP Inspector 启动后，用浏览器打开其 Web UI（默认为：http://127.0.0.1:6274/ ）。并按照如下步骤配置连接：

1. 在界面左侧设置 Transport Type 为 `SSE`，URL 为上一步获得的 MCP Server URL。
2. 展开 Authentication 面板，设置 Header Name 为 `Authorization` ，Bearer Token 为您的 **CRIC物业AI Access Token**。
3. 点击 Connect 按钮，连接成功后，左侧会显示当前连接的状态。

此时您就可以操作 MCP Inspector 测试 CRIC物业AI 的 MCP Server 了。具体使用方法您可以参考 [MCP Inspector 中文文档](https://mcp-docs.cn/docs/tools/inspector) 。

##### 第三方工具：

通过第三方工具使用 SSE 方式接入时，您需要通过 `Authorization` **HTTP 头** 指定 Access Token。例如，[Cline](https://cline.bot/) 设置文件：

```json
{
  "mcpServers": {
    "CRIC物业AI": {
      "transportType": "sse",
      "url": "{{您的 CRIC物业AI MCP Server URL}}",
      "headers": {
        "Authorization": "Bearer {{您的 CRIC物业AI Access Token}}"
      }
    }
  }
}
```

请注意，当前部分使用 [@modelcontextprotocol/typescript-sdk](https://github.com/modelcontextprotocol/typescript-sdk) 的工具 [其 ***HTTP 头*** 设置可能无法正确生效](https://github.com/modelcontextprotocol/typescript-sdk/issues/317)，因此建议使用 MCP Inspector 来测试。或者，作为一种临时措施，我们也支持在 URL 中使用 Query 方式指定 Access Token，例如：

```json
{
  "mcpServers": {
    "CRIC物业AI": {
      "transportType": "sse",
      "url": "{{您的 CRIC物业AI MCP Server URL}}?token={{您的 CRIC物业AI Access Token}}"
    }
  }
}
```

### 2. Stdio 方式

#### 2.1 运行

我们也支持 stdio 方式运行 MCP Server。命令如下：

```bash
CRIC_WUYE_AI_ACCESS_TOKEN={{您的 CRIC物业AI Access Token}} npx -y @wuye-ai/mcp-server-wuye-ai
```

#### 2.2 测试

您可以使用第三方工具或者 MCP Inspector 来连接 Stdio 方式的 MCP Server。请注意，Stdio 方式下一般无需用户手动运行 MCP Server，通常是由第三方工具自动运行。

##### MCP Inspector

在 MCP Inspector 中，您也可以选择 Stdio 方式接入。具体步骤如下：

1. 在界面左侧设置 Transport Type 为 `Stdio`，Command 为 `npx`，Arguments 为 `-y @wuye-ai/mcp-server-wuye-ai`。
2. 展开 Environment Variables 面板，添加或设置 `CRIC_WUYE_AI_ACCESS_TOKEN` 为您的 **CRIC物业AI Access Token**。
3. 点击 Connect 按钮，MCP Inspector 会自动运行命令启动 MCP Server 并连接。连接成功后，左侧会显示当前连接的状态。

此时您就可以操作 MCP Inspector 测试 CRIC物业AI 的 MCP Server 了。

##### 第三方工具

通过第三方工具使用 Stdio 方式接入时，如果您需要指定 Access Token，请通过环境变量 `CRIC_WUYE_AI_ACCESS_TOKEN` 指定。例如，Cline 设置文件：

```json
{
  "mcpServers": {
    "CRIC物业AI": {
      "transportType": "stdio",
      "command": "npx",
      "args": [
        "-y",
        "@wuye-ai/mcp-server-wuye-ai"
      ],
      "env": {
        "CRIC_WUYE_AI_ACCESS_TOKEN": "{{您的 CRIC物业AI Access Token}}"
      }
    }
  }
}
```

## 可选配置

您可以通过环境变量来配置 CRIC物业AI MCP Server 的运行方式。以下是可用的配置项：

| 参数名                              | 默认值                                      | 描述                                                                                                                                                                            |
|----------------------------------|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MODE`                           | `stdio`                                  | 运行模式，支持 `stdio` 和 `http` 两种模式。                                                                                                                                                |
| `HOSTNAME`                       | `0.0.0.0`                                | HTTP 绑定主机名，仅在 `http` 模式下有效。`0.0.0.0`即为绑定到本机所有IP地址。                                                                                                                            |
| `PORT`                           | `3011`                                   | HTTP 绑定端口，仅在 `http` 模式下有效。                                                                                                                                                    |
| `CRIC_WUYE_AI_ACCESS_TOKEN`      | *无*                                      | CRIC物业AI Access Token。如果不提供，则使用实际请求 HTTP Authorization Header 中的值。                                                                                                            |
| `CRIC_WUYE_AI_PROVIDER_API_BASE` | `https://export.wuye-ai.cricbigdata.com` | CRIC物业AI 后端接入 API，请注意 ***此 URL 不是 CRIC物业AI MCP Server 的 URL*** 。可选值为 `https://export.wuye-ai-staging.cricbigdata.com` （测试环境）、 `https://export.wuye-ai.cricbigdata.com` （生产环境） |
