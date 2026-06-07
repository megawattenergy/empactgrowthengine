# emPACT Sales Engine

Four-agent sales system for the Electric Miles emPACT CPO product. Scout finds and scores prospects, Analyst qualifies and finds the buyer, Closer-Prep writes the outreach, Coach preps you to close.

Built as a Next.js app so the Anthropic API key stays server-side. The browser only ever talks to your own `/api/agent` route, which holds the key and calls Anthropic. This is why the standalone version needs a server and cannot be a pure static page.

## Run locally

1. Install Node.js 18 or newer.
2. In this folder, run:
   ```
   npm install
   ```
3. Copy `.env.example` to `.env.local` and paste your Anthropic key:
   ```
   ANTHROPIC_API_KEY=sk-ant-...
   ```
   Get a key at https://console.anthropic.com
4. Start it:
   ```
   npm run dev
   ```
5. Open http://localhost:3000

## Deploy to Vercel

1. Push this folder to a GitHub repo.
2. At https://vercel.com, click New Project and import the repo.
3. Under Settings then Environment Variables, add:
   - Name: `ANTHROPIC_API_KEY`
   - Value: your key
4. Deploy. Vercel gives you a live URL.

The key is never exposed to the browser. Do not commit `.env.local`.

## Notes

- Web search is off by default. It is optional and slower, and can occasionally fail. Turn it on only for Scout's live prospecting if you want current named prospects.
- The "Paste my leads" mode never touches web search and is the most reliable path.
- All copy follows the Arun Anand CEO register: direct, no em-dashes, no filler.

## Next step: Clay and Outreach

The cleanest upgrade is to replace Scout's model-only prospecting with real Clay account data, and to push the finished email straight into an Outreach sequence. Both are server-side API calls that slot into the existing `/api/agent` pattern as new routes. Ask and this can be wired in.
