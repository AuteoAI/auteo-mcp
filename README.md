# Auteo MCP

[Auteo](https://auteo.ai) is an AI-native creative suite. Its remote MCP server lets assistants generate images, video, music, and spoken audio from prompts.

Generate instrumentals or songs with vocals using [YuE2](https://auteo.ai/models/yue2) or the [free AI music generator](https://auteo.ai/apps/free-ai-music-generator). In the browser, you can also create covers with the [AI song cover generator](https://auteo.ai/apps/ai-song-cover-generator) and draft lyrics with the [AI lyrics generator](https://auteo.ai/apps/ai-lyrics-generator).

## Connect

- **Endpoint:** `https://auteo.ai/api/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** Create a key under [Auteo → API keys](https://auteo.ai/me/settings#api-keys) and send `Authorization: Bearer YOUR_API_KEY`. Keep the key in your client’s private settings or environment.

### Claude

Open [Add Auteo to Claude](https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Auteo&connectorUrl=https%3A%2F%2Fauteo.ai%2Fapi%2Fmcp), which pre-fills the name and endpoint. In **Request headers**, add the following and save.

```http
Authorization: Bearer YOUR_API_KEY
```

### Cursor

Add the `auteo` entry to your personal `~/.cursor/mcp.json`.

```json
{
  "mcpServers": {
    "auteo": {
      "url": "https://auteo.ai/api/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http auteo https://auteo.ai/api/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

### Codex

Add this entry to `~/.codex/config.toml`.

```toml
[mcp_servers.auteo]
url = "https://auteo.ai/api/mcp"
bearer_token_env_var = "AUTEO_API_KEY"
```

Set the environment variable in the shell that launches Codex.

```bash
export AUTEO_API_KEY="YOUR_API_KEY"
```

### VS Code

With the Copilot harness selected, open **Chat: Open Customizations → MCP Servers** and use the **Copilot Global** configuration (`~/.copilot/mcp-config.json` by default). Set `AUTEO_API_KEY` in the environment of the host running the harness.

```json
{
  "mcpServers": {
    "auteo": {
      "type": "http",
      "url": "https://auteo.ai/api/mcp",
      "headers": {
        "Authorization": "Bearer ${AUTEO_API_KEY}"
      },
      "tools": ["*"]
    }
  }
}
```

[VS Code MCP configuration reference](https://code.visualstudio.com/docs/agents/reference/mcp-configuration#portable-configuration)

### Windsurf

In Cascade’s MCP menu, select **Open MCP config file**. Add the following entry to the `mcp_config.json` file it opens, then refresh MCP servers.

```json
{
  "mcpServers": {
    "auteo": {
      "serverUrl": "https://auteo.ai/api/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

[Windsurf MCP configuration reference](https://docs.devin.ai/windsurf/plugins/cascade/mcp#remote-http-mcps)

## Tools

| Tool | What it does |
| --- | --- |
| `auteo_account_status` | Shows the account plan, credit balance, and API usage limits. |
| `auteo_list_models` | Lists available models, capabilities, and starting credit costs. |
| `auteo_get_model` | Shows a model’s supported parameters and settings. |
| `auteo_estimate_cost` | Estimates the credit cost for specific settings and checks the available balance. |
| `auteo_upload_image` | Imports a publicly accessible HTTPS image as a reference asset. |
| `auteo_generate_image` | Submits a prompt or reference-based image generation job. |
| `auteo_generate_video` | Submits a video generation job from a prompt, with optional reference media where supported. |
| `auteo_generate_music` | Submits a song or instrumental generation job from a description or custom lyrics and style. |
| `auteo_generate_speech` | Submits text-to-speech using a model and a preset voice. |
| `auteo_get_generation` | Checks a generation by request ID and returns available results. |
| `auteo_list_generations` | Lists recent generations, optionally filtered by media type. |

Generation uses your Auteo credits. Ask for an estimate first if you want to review the cost.

## Example prompts

- “Find a model for a square watercolor illustration and show me the cost before generating it.”
- “Turn this reference image into a five-second shot with a slow camera push-in. Show me the available resolutions first.”
- “Generate a mellow instrumental jazz loop for a podcast intro.”
- “Read ‘Welcome to the night train’ in a calm English voice.”
- “Find my latest video generation and return its result URL if it’s ready.”

## More

- [Auteo MCP setup](https://auteo.ai/mcp)
- [Auteo CLI (`@auteo/cli`)](https://auteo.ai/cli)
- [AuteoAI/skills](https://github.com/AuteoAI/skills)

[`server.json`](server.json) contains the MCP Registry manifest. Publication to the Registry is pending.
