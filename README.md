# Fridge Rescue

A small tool that suggests a recipe based on what's already in your kitchen, prioritizing ingredients that are about to expire. Built to cut down on food waste, which costs the average US household close to $1,500–2,900 a year (EPA, 2025).

No backend, no build step. It's a single HTML file that calls the Claude API directly from your browser.

## How it works

1. You type in what you have (and flag anything close to expiring)
2. It sends that list to Claude with instructions to build one recipe around using those items up
3. Claude returns a recipe, which gets rendered on the page

## Running it

You need your own Anthropic API key. This project does not include one, and the person who wrote it does not pay for your usage.

1. Get a key at [console.anthropic.com](https://console.anthropic.com)
2. Open `index.html` in a browser (double-click it, or host it — see below)
3. Click "API key settings" at the top, paste your key, click **Save key**
4. Add ingredients and click **Find a recipe**

### Hosting it instead of opening it locally

You can serve this for free with **GitHub Pages**:

1. Push this repo to GitHub
2. Go to Settings → Pages
3. Set the source to your main branch, root folder
4. GitHub gives you a public URL serving `index.html`

Each visitor enters their own API key, so there's no shared cost and nothing for you to manage on a server.

## On the API key and security

- Your key is stored only in your browser's `localStorage`, on your own device
- It is sent directly to `api.anthropic.com` and nowhere else
- It is never written into this codebase or committed to git
- If you host this publicly, anyone who visits still needs to supply their own key. This is the standard "bring your own key" pattern for small client-side AI tools, and it's why no server or backend is required

This is fine for a personal tool or a small project shared with people you trust. It is not meant to be a production SaaS product; for that you'd want a real backend that holds the key server-side.

## Cost

Each recipe request costs a fraction of a cent on Claude Sonnet pricing ($3 per million input tokens, $15 per million output tokens as of mid-2026). Check [current pricing](https://platform.claude.com/docs/en/about-claude/pricing) before heavy use, since rates can change.

## Customizing

- Edit the `systemPrompt` string in `index.html` to change how recipes are generated
- Edit the `:root` CSS variables at the top of the `<style>` block to change the color palette
- The model used is `claude-sonnet-4-6`; swap this string if you want a different model

## License

MIT, see `LICENSE`.
