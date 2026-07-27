> [!WARNING]
> **Scheduled for deletion**
>
> This legacy repository has been consolidated into
> [`cerul-ai/cerul`](https://github.com/cerul-ai/cerul) at
> `integrations/claude-code`. Do not start new features or releases here. It
> remains temporarily available for historical and release recovery and will be
> deleted after final consolidation verification.

# Cerul Plugin for Claude Code

**Cerul: where video becomes citable** — Claude Code plugin.

The video search API for agents — meaning-based, grounded, timestamped.

## Install

```bash
# Step 1: Add the marketplace
/plugin marketplace add cerul-ai/cerul-plugin-cc

# Step 2: Install the plugin
/plugin install cerul@cerul-plugin
```

That's it. Claude Code will automatically set up the CLI and credentials on first use.

## What you can ask

Once installed, just ask Claude naturally:

- "What did Sam Altman say about AGI timelines?"
- "Find Jensen Huang's comments on AI infrastructure at GTC"
- "Compare what Dario Amodei and Sam Altman said about open-source AI"
- "What did Andrej Karpathy explain about LLM training?"

## How it works

The plugin adds a skill that Claude automatically invokes when you ask about video content. Under the hood it uses the [Cerul CLI](https://github.com/cerul-ai/cerul-cli) to search across indexed video transcripts.

## Requirements

- A Cerul API key — get one free at [cerul.ai/dashboard](https://cerul.ai/dashboard)
- The CLI is auto-installed on first use

## Links

- [Cerul](https://cerul.ai) — product homepage
- [CLI](https://github.com/cerul-ai/cerul-cli) — command-line tool
- [Python SDK](https://pypi.org/project/cerul/) — `pip install cerul`
- [TypeScript SDK](https://www.npmjs.com/package/cerul) — `npm install cerul`
- [Docs](https://cerul.ai/docs) — full API reference
