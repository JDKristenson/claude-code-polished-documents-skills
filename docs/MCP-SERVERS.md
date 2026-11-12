# MCP Server Configuration Guide

This inherited guide describes optional MCP examples. **NOT RUN / UNVERIFIED:** package names, CLI flags, config locations, environment substitution, tool schemas, pricing, and provider behavior below were not validated. Consult current [FireCrawl documentation](https://docs.firecrawl.dev/) and client documentation before use. Read [license, setup, and credential boundaries](REFERENCE-AND-SAFETY.md) first. Built-in themes do not require a provider. No provider or credential validity probes were made.

## Table of Contents

- [What is MCP?](#what-is-mcp)
- [FireCrawl MCP Server](#firecrawl-mcp-server)
- [Installation Methods](#installation-methods)
- [Configuration](#configuration)
- [Available Tools](#available-tools)
- [Usage Examples](#usage-examples)
- [Other Useful MCP Servers](#other-useful-mcp-servers)

---

## What is MCP?

The **Model Context Protocol (MCP)** is an open standard that allows AI assistants like Claude to connect with external tools and services. MCP servers provide Claude Code with additional capabilities like:

- Web scraping and brand extraction (FireCrawl)
- Database access (Supabase, Postgres)
- File system operations
- API integrations

---

## FireCrawl MCP Server

### Overview

FireCrawl is a web scraping API that extracts structured data from websites. The FireCrawl MCP server enables Claude Code to:

- **Extract brand identity** - Colors, fonts, logos from any website
- **Scrape content** - Convert web pages to markdown
- **Compare brands** - Analyze differences between two websites
- **Capture screenshots** - Visual references of web pages

### Prerequisites

1. **Node.js 18+** - Required to run MCP servers
2. **FireCrawl API Key** - Get one at [firecrawl.dev](https://firecrawl.dev)

### Get Your API Key

1. Go to [firecrawl.dev](https://firecrawl.dev)
2. Click "Sign Up" or "Get Started"
3. Review current account terms and pricing before creating an account; availability is not verified here
4. Navigate to Dashboard → API Keys
5. Generate a new API key
6. Copy and save it securely

> **Security Note**: Never commit API keys to version control. Store them securely in environment variables or use a secrets manager.

---

## Installation Methods

### Method 1: Client-supported secret injection

Confirm current package identity and client configuration syntax with official documentation. Use the client's supported secret store or protected environment injection. Do not put a real key in CLI arguments, shell history, prompts, or tracked files. This review does not supply a verified install command.

### Method 2: Manual Configuration

Add to your MCP configuration file:

**Location:**
- macOS/Linux: `~/.claude/mcp_servers.json`
- Windows: `%USERPROFILE%\.claude\mcp_servers.json`

```json
{
  "mcpServers": {
    "firecrawl": {
      "command": "npx",
      "args": ["-y", "@anthropic/firecrawl-mcp"],
      "env": {
        "FIRECRAWL_API_KEY": "fc-your-api-key-here"
      }
    }
  }
}
```

### Method 3: Project-Specific Configuration

For project-specific MCP servers, create `.claude/mcp.json` in your project:

```json
{
  "mcpServers": {
    "firecrawl": {
      "command": "npx",
      "args": ["-y", "@anthropic/firecrawl-mcp"],
      "env": {
        "FIRECRAWL_API_KEY": "${FIRECRAWL_API_KEY}"
      }
    }
  }
}
```

Provide any required environment variable through protected local injection, not a literal value typed into shell history. The `${FIRECRAWL_API_KEY}` JSON string above is an inherited illustration; whether a client expands it must be verified, not assumed.

---

## Configuration

### Full Configuration Example

```json
{
  "mcpServers": {
    "firecrawl": {
      "command": "npx",
      "args": ["-y", "@anthropic/firecrawl-mcp"],
      "env": {
        "FIRECRAWL_API_KEY": "fc-your-api-key-here"
      },
      "disabled": false
    }
  }
}
```

### Configuration Options

| Option | Type | Description |
|--------|------|-------------|
| `command` | string | The command to run (usually `npx`) |
| `args` | array | Arguments for the command |
| `env` | object | Environment variables |
| `disabled` | boolean | Temporarily disable the server |

### Verify Installation

After configuration, restart Claude Code and check:

```bash
# List configured MCP servers
claude mcp list
```

Or in Claude Code, the MCP tools should appear with prefix `mcp__firecrawl__`:
- `mcp__firecrawl__firecrawl_extract_branding`
- `mcp__firecrawl__firecrawl_scrape_with_branding`
- `mcp__firecrawl__firecrawl_compare_branding`

---

## Available Tools

### 1. Extract Branding

Extract complete brand identity from a website.

**Tool**: `mcp__firecrawl__firecrawl_extract_branding`

**Parameters**:
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | Yes | Website URL to analyze |
| `response_format` | string | No | `markdown` or `json` (default: `markdown`) |

**Returns**:
- Color scheme (light/dark)
- Color palette (primary, secondary, accent, background, text)
- Typography (font families, sizes, weights)
- Spacing values
- UI component styles
- Brand assets (logo, favicon, OG image)
- Brand personality traits

**Example**:
```
Extract the branding from https://stripe.com in JSON format
```

### 2. Scrape with Branding

Combine brand extraction with content scraping.

**Tool**: `mcp__firecrawl__firecrawl_scrape_with_branding`

**Parameters**:
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | Yes | Website URL |
| `include_markdown` | boolean | No | Include page content |
| `include_screenshot` | boolean | No | Include page screenshot |
| `include_links` | boolean | No | Include extracted links |
| `only_main_content` | boolean | No | Exclude headers/footers |

**Example**:
```
Scrape https://linear.app with branding and markdown content
```

### 3. Compare Branding

Compare brand identity between two websites.

**Tool**: `mcp__firecrawl__firecrawl_compare_branding`

**Parameters**:
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url1` | string | Yes | First website URL |
| `url2` | string | Yes | Second website URL |
| `response_format` | string | No | `markdown` or `json` |

**Example**:
```
Compare the branding of stripe.com and square.com
```

---

## Usage Examples

### Extract and Add New Brand Theme

```
1. Extract branding from https://notion.com
2. Add it as a new brand theme called "notion" to the document-polisher skill
```

Claude Code will:
1. Use FireCrawl to extract colors, fonts, and styling
2. Update `brand-mapping.json` with the new theme
3. Create a reference file in `brands/notion.md`

### Analyze Competitor Branding

```
Compare the branding of our website https://ourcompany.com with competitor https://competitor.com and summarize the key differences
```

### Create Brand-Consistent Documents

```
1. Extract the branding from https://client-website.com
2. Create a project proposal document styled with their brand
```

### Bulk Brand Extraction

```
Extract branding from these websites and create a comparison table:
- stripe.com
- square.com
- paypal.com
```

---

## Other Useful MCP Servers

### Supabase MCP

Database access and management:

An inherited optional integration reference, not configured or validated here. Confirm the current official package and use protected secret injection; never put an access token into chat or shell arguments.

### 21st Magic (UI Components)

UI component generation:

```bash
claude mcp add magic \
  --command "npx" \
  --args "-y" "@anthropic/21st-magic-mcp"
```

### File System MCP

Enhanced file operations:

```bash
claude mcp add filesystem \
  --command "npx" \
  --args "-y" "@anthropic/filesystem-mcp" \
  --args "/path/to/allowed/directory"
```

---

## Troubleshooting

### MCP Server Not Loading

1. **Check Node.js version**: Requires Node.js 18+
   ```bash
   node --version
   ```

2. **Inspect configuration locally** using the current client's documented location. Do not print full configs or parser diagnostics that can expose values.

3. **Check presence only**, without printing the key:
   ```bash
   if [ -n "${FIRECRAWL_API_KEY:-}" ]; then
     printf '%s\n' 'FIRECRAWL_API_KEY is set (value not shown)'
   else
     printf '%s\n' 'FIRECRAWL_API_KEY is not set'
   fi
   ```
   This does not validate the key, account, permissions, or service. This check was not run here.

### "Tool not found" Errors

1. Restart Claude Code after adding MCP servers
2. Check that the server isn't disabled
3. Verify the MCP server is listed: `claude mcp list`

### Rate Limiting

FireCrawl has rate limits on the free tier:
- Consider upgrading for production use
- Add delays between bulk requests
- Cache results when possible

### Timeout Errors

Large websites may timeout:
- Try extracting from specific pages instead of homepage
- Use `only_main_content: true` to reduce processing

---

## Security Best Practices

1. **Never commit API keys** - Use environment variables
2. **Use project-specific configs** - Limit scope of credentials
3. **Rotate keys regularly** - Especially if exposed
4. **Review MCP permissions** - Understand what each server can access
5. **Use `.gitignore`** - Exclude configuration files with secrets

---

## Resources

- [MCP Specification](https://modelcontextprotocol.io/)
- [FireCrawl Documentation](https://docs.firecrawl.dev/)
- [Claude Code Documentation](https://claude.com/claude-code)
- [Available MCP Servers](https://github.com/anthropics/mcp-servers)
