# Tic · Tac · Toe

A single-file Tic Tac Toe game with a **risograph print zine** aesthetic — warm
cream paper, a pink/blue duotone, grain texture, and marks that stamp onto the
board like a press hitting paper.

## Features

- **Unbeatable AI** — the computer plays a full minimax search, so the best you
  can do is force a draw.
- **Two modes** — *Vs Computer* or local *2 Players*.
- **Scoreboard** — tracks X wins, O wins, and draws across games (resets when you
  switch modes).
- **Zero dependencies, zero build** — everything (markup, styles, logic) lives in
  one `index.html`. Fonts load from Google Fonts.

## Run

Just open the file in any modern browser:

```sh
open index.html      # macOS
xdg-open index.html  # Linux
```

No server, bundler, or install step required.

## Project structure

```
index.html   # the entire game — HTML, CSS, and JS
```

## Design notes

- **Type** — [Fraunces](https://fonts.google.com/specimen/Fraunces) for the
  masthead, marks, and scores; [Space Mono](https://fonts.google.com/specimen/Space+Mono)
  for UI and labels.
- **Palette** — hot pink for **X**, ink blue for **O**, on warm cream paper.
- **Texture** — an inline SVG `feTurbulence` grain overlay blended with `multiply`.
- **Motion** — staggered tile reveal on load, a stamp animation per move, and a
  pop on the winning line (which inverts to a solid ink fill). All animations
  respect `prefers-reduced-motion`.
