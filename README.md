# Swarmcast

Concept app: describe an idea (product, policy, announcement) and watch a simulated crowd of AI personas react to it on a live social graph — then read the forecast and interview anyone in the crowd.

Single static file (`index.html`), no build step, no backend, no API keys. Everything runs in the browser with seeded rules (same idea → same crowd, "Re-roll crowd" for another sample).

## What you can do

- **Run** a simulation: 20–90 agents, 5–40 rounds (extend later with +10 rounds).
- **Steer it live:** pause / step one round / speed 0.5–4×, inject breaking news (good or bad, for everyone or one group, with strength), boost any post, drag a slider to change any persona's opinion and watch it spread.
- **Graph:** drag nodes, hover for details, click to select (shows who they follow and who follows them), highlight a group.
- **Feed:** filter by mood, search, filter by concern or author.
- **Forecast report:** support / undecided / oppose, opinion over time (hover to read any round, injected events marked), top concerns (click → posts), opinion leaders (click → interview), groups (click → highlight), biggest shifts.
- **Interview:** one-on-one with any agent, or "Ask the crowd" (most supportive, most opposed + two random people answer).
- **Share & export:** copy a link (`#idea=…&a=…&r=…` re-runs the same scenario), download the report as Markdown or all data as JSON.

Keyboard: `Space` pause/resume, `N` next round, `E` event panel.

## Limits

This is a concept demo: agents use rule-based opinion dynamics and sentence templates, not a language model. The output illustrates how a crowd simulation could look; it is not a real prediction. Next step would be to give each agent an LLM for posts and interviews.

## Run locally

Open `index.html` in a browser, or serve the folder (`python -m http.server`).
