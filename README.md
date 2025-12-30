# OECD数据查询服务 OECD Search

一个通过SDMX API提供OECD全面统计数据的模型上下文协议（MCP）服务器，支持AI助手和聊天机器人查询经济、健康、教育、环境等OECD数据集。
A model Context Protocol (MCP) server that provides comprehensive OECD statistics through the SDMX API, supporting AI assistants and chatbots to query OECD datasets in areas such as economy, health, education, and environment.## 工具列表 Tool List

本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。 本MCP服务封装下列工具，可让模型通过标准化接口调用以下功能。

| 工具 Tool   | 描述 Description         |
|-------|--------------------|
| search_dataflows | Search for OECD datasets (dataflows) by keyword. Returns matching datasets with their IDs, names, and descriptions. |
| list_dataflows | List available OECD dataflows (datasets), optionally filtered by category. Use this to browse datasets by topic area. |
| get_data_structure | Get the metadata and structure of a specific OECD dataset. Returns dimensions, attributes, and valid values for querying data. |
| query_data | Query actual statistical data from an OECD dataset. ⚠️ IMPORTANT: Defaults to last 100 observations (max 1000) to protect context window. Use filters, time periods, or last_n_observations to control data size. Large datasets (e.g. SOCX_AGG) can have 70,000+ observations - always specify limits! |
| get_categories | Get all available OECD data categories (17 categories covering all topics: Economy, Health, Education, Environment, etc.) |
| get_popular_datasets | Get a curated list of commonly used OECD datasets across all categories. |
| search_indicators | Search for specific economic or social indicators by keyword (e.g., "inflation", "unemployment", "GDP"). |
| get_dataflow_url | Generate an OECD Data Explorer URL for a dataset. Use this to provide users with a direct link to explore data visually in their browser. |
| list_categories_detailed | Get all OECD data categories with example datasets for each category. Returns comprehensive information about all 17 categories. |


## 检查服务 ## Inspector

工具在线测试： [https://mcp.xiaobenyang.com/inspector/1777316659351555](https://mcp.xiaobenyang.com/inspector/1777316659351555)

Online Tool test [https://mcp.xiaobenyang.com/inspector/1777316659351555](https://mcp.xiaobenyang.com/inspector/1777316659351555)

## 服务配置 MCP Server Config


> #### 如何获取 XBY-APIKEY ？ How to get XBY-APIKEY ?
> 访问小笨羊科技网站 [https://xiaobenyang.com](https://xiaobenyang.com)，注册用户即可获得APIKEY
> Visit XiaoBenYang website [https://xiaobenyang.com](https://xiaobenyang.com), register and get the APIKEY.

### SSE
```json
{
  "mcpServers": {
    "OECD数据查询服务": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "sse",
      "url": "https://mcp.xiaobenyang.com/1777316659351555/sse"
    }
  }
}
```
### STREAMABLE HTTP
```json
{
  "mcpServers": {
    "OECD数据查询服务": {
      "headers": {
        "XBY-APIKEY": "<YOUR_XBY_APIKEY>"
      },
      "type": "streamable_http",
      "url": "https://mcp.xiaobenyang.com/1777316659351555/mcp"
    }
  }
}
```
### STDIO
```json
{
    "mcpServers": {
        "OECD数据查询服务": {
          "command": "npx",
          "args": [
            "-y",
            "xiaobenyang-mcp"
          ],
          "env": {
            "XBY_APIKEY": "<YOUR_XBY_APIKEY>",
            "mcpId": "1777316659351555",
          },
          "transport": "stdio"
        }
      }
}

```
