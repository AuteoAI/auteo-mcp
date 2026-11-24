# Auteo for DeepSeek Harness (`@auteo/dsh-plugin`)

A DeepSeek Harness (DSH) bundle plugin that adds the Auteo remote MCP server to a DSH profile via `dsh.bundle.patch`, enabling music, lyrics, image, video, and audio generation in DSH.

- **MCP Endpoint:** `https://auteo.ai/api/mcp` (Streamable HTTP, 10s startup timeout)
- **Compatibility:** `dsh >=0.2.2-rc.5 <0.3.0`

## Installation

Install into the DSH profile you use (for example, `tui`):

```sh
dsh plugin --profile tui add @auteo/dsh-plugin
```

## Configuration

Set `AUTEO_API_KEY` to your Auteo API key in the environment or DSH credential store where DSH runs, then start or restart DSH (`dsh tui`).

- DSH reads `AUTEO_API_KEY` through its credentials provider and sends `Authorization: Bearer <token>` when connecting. Resolved secrets are not written to the composed configuration.
- If the credential is not set yet, the MCP client waits until it is configured.
- To create or manage API keys, see [Auteo MCP setup](https://auteo.ai/mcp).

## Removal

```sh
dsh plugin --profile tui remove @auteo/dsh-plugin
```

## License

[MIT](./LICENSE)

[Visit Auteo](https://auteo.ai/apps/free-ai-music-generator)
