# FireCrawl Setup Guide

**Inherited optional provider guide — NOT RUN / UNVERIFIED.** Read [provenance, license boundaries, and safe setup](../docs/REFERENCE-AND-SAFETY.md) first. Package names, client commands, tools, pricing, and provider behavior here are not validated. Do not paste keys into chat or commands, print configuration values, or test real credentials to validate this guide. Confirm current official documentation before setup.

FireCrawl lets you scrape a company's website and automatically extract their colors, fonts, and styling. Then you can apply that branding to your documents!

---

## Do I Need This?

**You DON'T need FireCrawl if:**
- You're happy with the 10 built-in brand themes (McKinsey, Stripe, Apple, etc.)
- You just want to polish documents with existing styles

**The inherited FireCrawl workflow proposes these uses (not requirements; manual theme configuration is also possible):**
- You want to extract branding from a client's website
- You want to create custom themes from any company
- You want to match a specific brand not in the default list

---

## Step 1: Get Your Free API Key

### Option A: Let Claude Help You (Recommended)

Just paste this into Claude Code:

```
I want to set up FireCrawl to extract website branding.
Walk me through getting an API key from firecrawl.dev step by step.
Open the signup page for me and tell me exactly what to click.
```

### Option B: Do It Yourself

1. **Go to FireCrawl**: https://firecrawl.dev

2. **Click "Get Started" or "Sign Up"**

3. **Create an account** (you can use Google, GitHub, or email)

4. **Go to Dashboard** after signing in

5. **Find "API Keys"** in the sidebar or settings

6. **Click "Create API Key"** or "Generate New Key"

7. **Copy your key** - it looks like: `fc-xxxxxxxxxxxxxxxxxxxxxxxx`

8. **Save it somewhere safe** - you'll need it in the next step!

---

## Step 2: Add FireCrawl to Claude Code

### Option A: Review a Safe Setup Plan

```text
Explain the current official FireCrawl/client setup documentation and permissions.
Do not install or contact a provider yet. Do not ask me to paste credentials.
Propose a supported local secret-store or protected environment-injection plan.
```

### Option B: Have Claude Do Everything

Paste this and Claude will guide you:

```text
I will keep credentials in a protected local store, outside this conversation.
Help me review configuration scope and current official client/provider guidance.
Do not display values, read full secret configs, or run credential-validity probes.
```

### Option C: Manual Setup

Use the current [official FireCrawl documentation](https://docs.firecrawl.dev/) and the client's supported secret configuration. No verified install command is supplied here. Do not enter real values in shell arguments/history or tracked configuration.

---

## Step 3: Verify It's Working

Paste this into Claude Code:

```
Test my FireCrawl setup by extracting the branding from https://linear.app
Show me the colors, fonts, and style they detected.
```

If it works, you'll see output like:
- Primary color: #5E6AD2
- Fonts: Inter, system fonts
- Style: Modern, minimal

---

## Step 4: Extract Your First Custom Brand

Now the fun part! Try this:

```
Extract the branding from https://[ANY-WEBSITE-YOU-WANT]
and add it as a new brand theme called "[BRAND_NAME]" to document-polisher.
Then create a test document using that new theme.
```

**Example:**
```
Extract the branding from https://notion.com
and add it as a new brand theme called "notion-custom" to document-polisher.
Then create a test document using that new theme.
```

---

## Troubleshooting

### "FireCrawl tools not found"

Paste this:
```
The FireCrawl MCP tools aren't showing up. Help me debug:
1. Check if the MCP server is in my config
2. Verify the API key is set correctly
3. Restart Claude Code if needed
4. Test the connection
```

### "API key invalid"

Paste this:
```
I'm getting API key errors with FireCrawl. Help me:
1. Explain current official credential setup guidance without reading my key
2. Check presence only, with values hidden; do not validate against the provider
3. Keep all credential updates in a protected local store, not this chat
```

### "Rate limit exceeded"

The free tier has limits. Options:
- Wait a few minutes and try again
- Upgrade your FireCrawl plan at firecrawl.dev
- Cache/save results so you don't re-extract the same sites

### "Timeout on large sites"

Paste this:
```
FireCrawl is timing out on [WEBSITE].
Try extracting from a specific page instead of the homepage,
like their About or Product page.
```

---

## Quick Reference: FireCrawl Prompts

### Extract Branding
```
Extract branding from https://[WEBSITE] and show me the results
```

### Add as New Theme
```
Extract branding from https://[WEBSITE] and add it as a "[NAME]" theme to document-polisher
```

### Compare Two Brands
```
Use FireCrawl to compare the branding of https://[SITE1] and https://[SITE2]
```

### Full Workflow
```
1. Extract branding from https://[CLIENT-WEBSITE]
2. Add it as a theme called "[CLIENT-NAME]"
3. Create a proposal document using their brand style
4. Save it as "[CLIENT-NAME]_proposal.docx"
```

---

## Free Tier Limits

The inherited guide included free-tier estimates; these were not validated and are not a current offer. Check [official pricing](https://firecrawl.dev/pricing) and terms before any provider use. No subscription or service use was performed here.

---

## Security Note

Storage and transmission depend on the actual client/provider configuration; this review establishes no local-only or non-sharing guarantee. A `.gitignore` alone cannot prevent exposure in logs, backups, screenshots, or shell history. Never share keys in prompts, repos, reports, or chats. Use [presence-only diagnostics](../docs/REFERENCE-AND-SAFETY.md#credentials-and-diagnostics), not value printing or validity probes. No credential checks were run.
