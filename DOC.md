# CRIC物业AI MCP Server 接入（腾讯云开发）

接入 **CRIC物业AI 平台** 的 MCP 服务器。**CRIC物业AI** 是克而瑞专为物业行业打造的智能 AI 助理。

[前往云开发平台运行 MCP Server](https://tcb.cloud.tencent.com/dev#/ai?tab=mcp&p&mcp-template=mcp-server-wuye-ai)

---

## 环境变量

- 需要将 **CRIC_WUYE_AI_ACCESS_TOKEN** 配置为 **CRIC物业AI Access Token**。如果不提供，则使用实际请求 HTTP Authorization Header 中的值。
- 可选配置项：需要将 **CRIC_WUYE_AI_PROVIDER_API_BASE** 配置为 **CRIC物业AI 后端接入 API**。如果不提供，默认为生产环境（`https://export.wuye-ai.cricbigdata.com`）。请注意 ***此 URL 不是 CRIC物业AI MCP Server 的 URL*** 。可选值为 `https://export.wuye-ai-staging.cricbigdata.com` （测试环境）、 `https://export.wuye-ai.cricbigdata.com` （生产环境）
- 可选配置项：需要将 **MODE** 配置为 **运行模式**，支持 `stdio` 和 `http` 两种模式。如果不提供，默认为 `stdio`。
- 可选配置项：需要将 **HOSTNAME** 配置为 **HTTP 绑定主机名**，仅在 `http` 模式下有效。如果不提供，默认为 `0.0.0.0`，即为绑定到本机所有IP地址。
- 可选配置项：需要将 **PORT** 配置为 **HTTP 绑定端口**，仅在 `http` 模式下有效。如果不提供，默认为 `3011`。

具体配置要求也可以参考 [README](https://github.com/wuye-ai/mcp-server-wuye-ai/blob/master/README.md)。

## 🗺️ 功能清单

| 命令名称         | 功能描述                                                   | 核心参数                                                              |
|--------------|--------------------------------------------------------|-------------------------------------------------------------------|
| `获取资讯日报`     | 根据YYYY-MM-DD形式的日期，获取当日物业行业资讯日报。                        | `date`(要获取资讯日报的日期，形如 YYYY-MM-DD。如果不提供，则默认为今天。)                    |
| `获取行业热点问题列表` | 获取当前CRIC物业AI应用内物业行业热点问题的分类和列表。                         | 无                                                                 |
| `获取可用知识库列表`  | 获取可用知识库列表，后续可以使用其中的知识库搜索相关知识。                          | 无                                                                 |
| `搜索知识库`      | 指定具体知识库ID，以及具体查询的问题，获取知识库搜索结果，以知识片段或知识文档全文的形式返回，供AI参考。 | `knowledge_base_id`(知识库的 ID), `query`(查询的问题), `top_k`(最大返回结果数量) 等 |

## 仓库地址

[https://github.com/wuye-ai/mcp-server-wuye-ai](https://github.com/wuye-ai/mcp-server-wuye-ai)

---

## 🔌 使用方式

- [在云开发 Agent 中使用](https://docs.cloudbase.net/ai/mcp/use/agent)
- [在 MCP Host 中使用](https://docs.cloudbase.net/ai/mcp/use/mcp-host)
- [通过 SDK 接入](https://docs.cloudbase.net/ai/mcp/use/sdk)

---

[云开发 MCP 控制台](https://tcb.cloud.tencent.com/dev#/ai?tab=mcp)  
