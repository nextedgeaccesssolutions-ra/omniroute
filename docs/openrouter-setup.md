# OpenRouter Integration

OmniRoute routes requests through OpenRouter to access 400+ models from a single endpoint.

## Setup

### 1. Create an OpenRouter API key

1. Go to [openrouter.ai/keys](https://openrouter.ai/keys)
2. Click **Create Key** — name it something like `neas-omniroute`
3. Copy the key (starts with `sk-or-v1-`) — you won't see it again

### 2. Add the key to your `.env`

```
OPENROUTER_API_KEY=sk-or-v1-...
```

### 3. Add the key to Vercel

```bash
vercel env add OPENROUTER_API_KEY
```

Or via the Vercel dashboard: **Project → Settings → Environment Variables**.

## Usage

Once OmniRoute is running (`npm run dev`), point Claude Code at it:

```bash
claude config set apiBaseUrl http://localhost:20128/v1
```

Then use `model: "auto"` in requests to let OmniRoute pick the best available model via its 4-tier fallback: Subscription → API Key → Cheap → Free.

## Available OpenRouter models

OmniRoute exposes OpenRouter models with their native IDs, e.g.:
- `openrouter/auto`
- `anthropic/claude-sonnet-4-5`
- `openai/gpt-4o`
- `google/gemini-2.0-flash-exp:free`
