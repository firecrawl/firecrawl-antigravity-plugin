# Firecrawl plugin for Gemini CLI and Google Antigravity

> Generated from Firecrawl's plugin source. Do not edit this repository by hand; changes made here are overwritten by the next sync.

Firecrawl is the context API for AI agents. This package connects Gemini CLI and Google Antigravity to the hosted [Firecrawl MCP server](https://docs.firecrawl.dev/mcp-server/oauth) to search the web, read pages, collect structured data, interact with live pages, and track changes. One repository serves both: Gemini CLI reads `gemini-extension.json`, and Antigravity reads `plugin.json` and `mcp_config.json`.

## What's included

- `gemini-extension.json`: the Gemini CLI extension manifest, with the hosted MCP server at `https://mcp.firecrawl.dev/v2/mcp-oauth`
- `plugin.json` and `mcp_config.json`: the Antigravity plugin manifest and its MCP server definition
- `skills/firecrawl`: routes each request to the right Firecrawl tool (search, scrape, Alexandria data providers, agent, map and crawl, interact, parse, monitors, developer, paper and US government search), with a reference per operation
- `skills/firecrawl-deep-research`: cited, multi-source investigations, comparisons, prospect discovery and enrichment

## Install

**Gemini CLI**

```sh
gemini extensions install https://github.com/firecrawl/firecrawl-antigravity-plugin
```

Start `gemini`, then run `/mcp auth firecrawl` to sign in to Firecrawl in your browser. `/mcp list` shows the server as connected once you have signed in.

**Antigravity CLI, app and IDE**

```sh
agy plugin install https://github.com/firecrawl/firecrawl-antigravity-plugin
```

Plugins installed in the Antigravity app also appear in the CLI. Sign in to Firecrawl when Antigravity asks on the first Firecrawl call.

## Use an API key instead of browser sign-in

Create a key at [firecrawl.dev/app/api-keys](https://www.firecrawl.dev/app/api-keys), disable this package's server, and add your own server entry.

Gemini CLI, in `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "firecrawl-key": {
      "type": "http",
      "url": "https://mcp.firecrawl.dev/v2/mcp",
      "headers": { "x-firecrawl-api-key": "YOUR_API_KEY" }
    }
  }
}
```

Antigravity, in `~/.gemini/config/mcp_config.json`:

```json
{
  "mcpServers": {
    "firecrawl-key": {
      "serverUrl": "https://mcp.firecrawl.dev/v2/mcp",
      "headers": { "x-firecrawl-api-key": "YOUR_API_KEY" }
    }
  }
}
```

## Capabilities

- **Search**: web, news and image search with query-relevant excerpts, plus matching Alexandria data providers
- **Scrape**: any URL to clean Markdown, JSON with a schema, a grounded answer or verbatim highlights
- **Alexandria**: discover catalogued data providers and execute them for structured records
- **Agent**: autonomous multi-source collection into structured data
- **Map and crawl**: list a site's URLs or collect a bounded section
- **Interact**: clicks, forms and navigation in a live browser session
- **Parse**: PDFs and documents, including local files through a hosted upload
- **Monitor**: recurring checks for page changes
- **Developer, paper and US government search**: issues, merged pull requests, READMEs and docs; published papers; statutes, regulations and court opinions

Which tools appear depends on your account; the live tool list is the authority.

## Links

- Docs: https://docs.firecrawl.dev
- Terms: https://www.firecrawl.dev/terms-of-service
- Privacy: https://www.firecrawl.dev/privacy-policy

## License

MIT
