# Model Context Protocol (MCP) Server for dify workflows
[![smithery badge](https://smithery.ai/badge/dify-mcp-server)](https://smithery.ai/server/dify-mcp-server)
A simple implementation of an MCP server for using [dify](https://github.com/langgenius/dify). It achieves the invocation of the Dify workflow by calling the tools of MCP.
## 🔨Installation

### Installing via Smithery

To install Dify MCP Server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/dify-mcp-server):

```bash
npx -y @smithery/cli install dify-mcp-server --client claude
```

### Prepare config.yaml
Before using the mcp server, you should prepare a config.yaml to save your dify_base_url and dify_sks. The example config like this:
```yaml
dify_base_url: "https://cloud.dify.ai/v1"
dify_app_sks:
  - "app-sk1"
  - "app-sk2"
```
Different SKs correspond to different dify workflows.
### Run mcp server
Then you can run the dify mcp server in your clients. The config of client should like the following format:
```json
"mcpServers": {
  "mcp-server-rag-web-browser": {
    "command": "uv",
      "args": [
        "--directory", "${DIFY_MCP_SERVER_PATH}",
        "run", "dify_mcp_server"
      ],
    "env": {
       "CONFIG_PATH": "$CONFIG_PATH"
    }
  }
}
```
Example config:
```json
"mcpServers": {
  "mcp-server-rag-web-browser": {
    "command": "uv",
      "args": [
        "--directory", "/Users/lyx/Downloads/dify-mcp-server",
        "run", "dify_mcp_server"
      ],
    "env": {
       "CONFIG_PATH": "/Users/lyx/Downloads/config.yaml"
    }
  }
}
```
### Enjoy it
At last, you can use dify tools in any client who supports mcp.
