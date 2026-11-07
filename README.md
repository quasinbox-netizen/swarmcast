# Swarmcast

Concept app: describe an idea (a product, policy or announcement) and watch a simulated crowd of personas react to it on a live social graph. Then read the forecast and interview anyone in the crowd. English and Polish.

The simulation is one static file (`index.html`) with no build step. It runs in the browser with seeded rules: the same idea gives the same crowd, and "Re-roll crowd" draws another sample. One optional serverless function (`api/agent.js`) can write posts and interview answers with Claude. It is off until the owner sets an API key.

## What you can do

- **Run** a simulation: 20–90 agents, 5–40 rounds (+10 rounds later if you want). Pick a **crowd mix** (balanced, big city, countryside, students & young, older population, business district) and optionally **add your own persona type** with a stance, a main worry and a share of the crowd.
- **Steer it live:** pause, step one round, speed 0.5–4×. You can also:
  - inject breaking news (good or bad, for everyone or one group, with a strength);
  - boost any post;
  - drag a slider to change any persona's opinion and watch it spread.
- **Reads your idea** (in English or Polish):
  - It spots the topic: transport, pricing, education, work, devices, data & AI, environment, health or housing.
  - It sees whether the idea takes something away, gives something, or both.
  - It notices softeners: a pilot, exemptions, money given back, voluntary, phased in, a consultation.
  - The groups hit hardest start more opposed, and their main worry is added to their concerns. All of this is shown under the question.
- **Graph:** drag nodes, hover for details, click to select (shows who they follow and who follows them), highlight a group. **Replay**, or drag the slider, to rewind the graph and the feed to any round.
- **How sure is this?** Re-runs the idea with 40 alternate crowds: different random people and connections, same events. It shows the support range (10th–90th percentile), a histogram, and how often support wins.
- **What would make it land better?** Tests each softener the idea doesn't have yet, with 20 crowds per variant, and ranks them by change in support. "Run it" pins the current run as the baseline and starts the variant.
- **Compare variants:** pin a run as a baseline, change the idea and run it again. You get:
  - a side-by-side table and the change in percentage points;
  - the baseline line on the chart;
  - whether the alternate-crowd ranges overlap (if they do, the difference may be luck).
- **Does it match real votes?** A benchmark of 9 real referendums with known results (congestion charges in Stockholm, Edinburgh, Manchester and Gothenburg; Swiss votes; Berlin housing). Each is typed in as a plain idea. Current result: an average miss of 22.6 points, worse than always guessing 50% (16.0). The page says so. The rules are deliberately **not** tuned to these cases.
- **Interview:** one-on-one with any agent, or "Ask the crowd" (the most supportive, the most opposed and two random people answer).
- **Share & export:**
  - copy a link: `#idea=…&a=…&r=…&s=…&m=…&c=…` re-runs the same scenario, crowd mix and own persona included;
  - a result card as a PNG;
  - the report as Markdown, all data as JSON;
  - **Save run .json**, which reopens the run exactly, with your events, nudges and boosts replayed.
- **Recent runs** on the start screen (stored only in your browser).

Keyboard: `Space` pause/resume, `N` next round, `E` event panel, `R` replay.

## Optional AI voices (`api/agent.js`)

When the Vercel project has `ANTHROPIC_API_KEY` set, an "AI voices" switch appears. Claude then writes the answers in interviews and up to 24 posts per run, from the six most influential personas. The numbers stay rule-based; the model only puts a persona's current stance into words.

- Model: `claude-opus-5-5` at low effort, with server-side refusal fallback. Set `SWARMCAST_MODEL` to use another model, for example `claude-haiku-5-5`, which is much cheaper.
- Guard rails:
  - allowed origins only (swarmcast.vercel.app, quasipi.tech, localhost);
  - 30 requests per IP per 10 minutes and 600 per instance per hour (best effort, held in memory);
  - capped input sizes and short outputs;
  - a system prompt that keeps the model in a fictional persona and on the idea.
- Requests without an `Origin` header (scripts) are still subject to the rate limits only.
- Without a key, or if a call fails, the app falls back to the rule-based text.

## Limits

This is a concept demo. Opinion dynamics and the default texts are rules and templates, and the benchmark shows they don't predict real votes. Treat the output as an illustration of how a crowd simulation behaves, not as a forecast.

## Run locally

Open `index.html` in a browser, or serve the folder (`python -m http.server`). The AI function only runs on Vercel, or under any server that can call `api/agent.js`.
