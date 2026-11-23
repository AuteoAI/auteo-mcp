# Install Auteo MCP in Cline

Use a Cline CLI version with Streamable HTTP MCP support. Create an API key in [Auteo settings](https://auteo.ai/me/settings#api-keys) and set `AUTEO_API_KEY` in the shell where you run Cline. Keep the key out of chat, logs, and source control. The user supplies the key through their own shell.

```sh
cline mcp add auteo --transport streamable-http https://auteo.ai/api/mcp   --header "Authorization: Bearer ${AUTEO_API_KEY}" --yes
cline mcp list
```

Cline saves the Authorization header in its local MCP settings. Treat that file as sensitive. Reload Cline if the server was added from a separate session.

To verify the server without paying for a generation, ask Cline to call `auteo_list_models` and list available models. Remove the integration with `cline mcp remove auteo --yes`.
