# Swarmcast

Concept app: describe an idea (product, policy, announcement) and watch a simulated crowd of AI personas react to it on a live social graph — then read the forecast and interview anyone in the crowd.

Single static file (`index.html`), no build step, no backend, no API keys. Everything runs in the browser with seeded rules (same idea → same crowd, "Re-roll crowd" for another sample).

## What you can do

- **Run** a simulation: 20–90 agents, 5–40 rounds (extend later with +10 rounds).
- **Steer it live:** pause / step one round / speed 0.5–4×, inject breaking news (good or bad, for everyone or one group, with strength), boost any post, drag a slider to change any persona's opinion and watch it spread.
- **Reads your idea:** spots the topic (transport, pricing, education, work, devices, data & AI, environment, health, housing) and whether it takes something away, gives something or both. The groups it hits hardest start more opposed, and their main worry is added to their concerns. All of this is shown under the question.
- **Graph:** drag nodes, hover for details, click to select (shows who they follow and who follows them), highlight a group. **Replay** or drag the slider to rewind the graph and the feed to any round.
- **How sure is this?** Re-runs the idea with 40 alternate crowds (different random people and connections, same events). It shows the support range (10th–90th percentile), a histogram and how often support wins.
- **Compare variants:** pin a run as a baseline, change the idea and run again. You see a side-by-side table and the change in percentage points, the baseline line on the chart, and whether the alternate-crowd ranges overlap (if they do, the difference may be luck).
- **Recent runs** on the start screen (stored only in your browser).
- **Feed:** filter by mood, search, filter by concern or author.
- **Forecast report:** support / undecided / oppose, opinion over time (hover to read any round, injected events marked), top concerns (click → posts), opinion leaders (click → interview), groups (click → highlight), biggest shifts.
- **Interview:** one-on-one with any agent, or "Ask the crowd" (most supportive, most opposed + two random people answer).
- **Share & export:** copy a link (`#idea=…&a=…&r=…&s=…` re-runs the same scenario, including a re-rolled crowd), download the report as Markdown or all data as JSON.

Keyboard: `Space` pause/resume, `N` next round, `E` event panel, `R` replay.

## Limits

This is a concept demo: agents use rule-based opinion dynamics and sentence templates, not a language model. The output illustrates how a crowd simulation could look; it is not a real prediction. Next step would be to give each agent an LLM for posts and interviews.

## Run locally

Open `index.html` in a browser, or serve the folder (`python -m http.server`).
