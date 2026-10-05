# llmsplain

An agent skill that explains things in [ASD-STE100](https://www.asd-ste100.org) Simplified Technical English: short sentences, active voice, one word for one meaning.

Inspired by [Andrej Karpathy's tip](https://x.com/karpathy): ask your LLM to explain in ASD-STE100, or "80% of the way" there.

## Install

```bash
npx skills add ReidBraswell/llmsplain
```

Works with any agent the `skills` CLI supports (Claude Code, Codex, Cursor, and more). Add `-g` for a global install, or `-a <agent>` to pick one agent.

## Use

```
llmsplain this diff
llmsplain how the auth middleware works
strict STE: <paste text>
```

The default is **lite** (about 80% STE). Say "strict STE" or "100%" for the full spec.
