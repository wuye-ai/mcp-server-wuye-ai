# CRIC物业AI MCP Server

## 介绍

CRIC物业AI 是 [克而瑞](http://www.cricchina.com/) 专为物业行业打造的智能 AI 助理。

## 功能

CRIC物业AI MCP Server 是一个基于 [Model Context Protocol](https://modelcontextprotocol.github.io/) 的服务端实现，基于
CRIC物业AI 平台的部分原子能力，目前版本提供了以下功能（Tool）：

- 获取资讯日报
- 获取行业热点问题列表
- 获取可用知识库列表
- 搜索知识库

更多能力即将推出，敬请期待。

## 获取 Access Token

您需要先获取 **CRIC物业AI Access Token** 才能使用 CRIC物业AI MCP Server 的功能。请联系我们的客服人员申请，联系邮箱：[xuanao@cric.com](mailto:xuanao@cric.com) 。

## 使用

### 1. SSE 方式（http）

#### 1.1 运行

您可以自行运行一个 MCP Server 服务并启用 HTTP 模式，或者使用我们提供的服务。自行运行：

```bash
MODE=http PORT=3011 npx -y @wuye-ai/mcp-server-wuye-ai
```

运行成功后，服务端口 URL 为 `http://localhost:3011/sse/mcp` 。或者您也可以直接使用我们提供的服务端口
URL `https://mcp.staging.yiliaoconsulting.com/sse/mcp` （测试环境）、 `https://mcp.yiliaoconsulting.com/sse/mcp`
（生产环境）作为后续测试开发使用。

#### 1.2 测试

服务运行成功后，您可以使用 [MCP Inspector](https://github.com/modelcontextprotocol/inspector) 来查看并测试服务是否正常运行。

```bash
npx @modelcontextprotocol/inspector
```

MCP Inspector 启动后，用浏览器打开其 Web UI（默认为：http://127.0.0.1:6274/ ）。并按照如下步骤配置连接：

1. 在界面左侧设置 Transport Type 为 `SSE`，URL 为上一步获得的服务端口 URL。
2. 展开 Authentication 面板，设置 Header Name 为 `Authorization` ，Bearer Token 为您的 **CRIC物业AI Access Token**。
3. 点击 Connect 按钮，连接成功后，左侧会显示当前连接的状态。

此时您就可以操作 MCP Inspector 测试 CRIC物业AI 的 MCP Server
了。具体使用您可以参考 [MCP Inspector 中文文档](https://mcp-docs.cn/docs/tools/inspector) 。

### 2. Stdio 方式

#### 2.1 运行

我们也支持 stdio 方式运行 MCP Server。命令如下：

```bash
npx -y @wuye-ai/mcp-server-wuye-ai
```

#### 2.2 测试

您可以使用第三方工具或者 MCP Inspector 来连接 Stdio 方式的 MCP Server。请注意，Stdio 方式下一般无需用户手动运行 MCP
Server，通常是由第三方工具自动运行。

通过第三方工具使用 Stdio 方式接入时，如果您需要指定 Access Token，请通过环境变量 `CRIC_WUYE_AI_ACCESS_TOKEN` 指定。例如，Cline
设置文件：

```json
{
  "mcpServers": {
    "CRIC物业AI": {
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

在 MCP Inspector 中，您也可以选择 Stdio 方式接入。具体步骤如下：

1. 在界面左侧设置 Transport Type 为 `Stdio`，Command 为 `npx`，Arguments 为 `-y @wuye-ai/mcp-server-wuye-ai`。
2. 展开 Environment Variables 面板，添加或设置 `CRIC_WUYE_AI_ACCESS_TOKEN` 为您的 **CRIC物业AI Access Token**。
3. 点击 Connect 按钮，MCP Inspector 会自动运行命令启动 MCP Server 并连接。连接成功后，左侧会显示当前连接的状态。

## 可选配置

您可以通过环境变量来配置 CRIC物业AI MCP Server 的运行方式。以下是可用的配置项：

| 参数名                              | 默认值                                   | 描述                                                                                                                                                                      |
|----------------------------------|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `MODE`                           | `stdio`                               | 运行模式，支持 `stdio` 和 `http` 两种模式。                                                                                                                                          |
| `HOSTNAME`                       | `0.0.0.0`                             | HTTP 绑定主机名，仅在 `http` 模式下有效。`0.0.0.0`即为绑定到本机所有IP地址。                                                                                                                      |
| `PORT`                           | `3011`                                | HTTP 绑定端口，仅在 `http` 模式下有效。                                                                                                                                              |
| `CRIC_WUYE_AI_ACCESS_TOKEN`      | *无*                                   | CRIC物业AI Access Token。如果不提供，则使用实际请求 HTTP Authorization Header 中的值。                                                                                                      |
| `CRIC_WUYE_AI_PROVIDER_API_BASE` | `https://export.yiliaoconsulting.com` | CRIC物业AI 后端接入 API，请注意 ***此 URL 不是 CRIC物业AI MCP Server 的 URL*** 。可选值为 `https://export.staging.yiliaoconsulting.com` （测试环境）、 `https://export.yiliaoconsulting.com` （生产环境） |
