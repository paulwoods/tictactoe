# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A single-file Tic Tac Toe game. The entire application — markup, CSS, and JavaScript — lives in `index.html`. There is no build system, package manager, test suite, or dependencies (fonts load from Google Fonts at runtime).

## Running

Open the file directly in a browser; there is no server or build step:

```sh
xdg-open index.html   # Linux
open index.html       # macOS
```

## Architecture

Everything is in `index.html`, split into three concerns:

- **`<style>`** — a risograph print-zine theme driven by CSS custom properties in `:root` (`--paper`, `--ink`, `--pink` for X, `--blue` for O, hard-offset `--shadow`s). Grain is an inline SVG `feTurbulence` overlay on `body::before`. Marks animate via the `stamp` keyframes; the winning line uses `pop`. All motion is gated behind `prefers-reduced-motion`.
- **`<script>`** — the game logic. State lives in module-level vars: `state` (9-cell array), `current` ('X'/'O'), `over`, `vsComputer`. `init()` rebuilds the board DOM and wires click handlers; `play(i)` places a mark, checks `winningLine()`, advances the turn, and triggers the AI when it's O's turn.
- **AI** — `aiMove()` + `minimax()` implement an unbeatable opponent (full search, depth-weighted scoring). `HUMAN` is always X, `AI` is always O.

### Key coupling between CSS and JS

The JS targets specific DOM hooks that the styling depends on — changing one side requires updating the other:

- Cells get classes `cell`, `x`/`o` (lowercased mark), and `win` — all three drive distinct CSS rules (`.cell.x`, `.cell.x.win`, etc.).
- Element IDs are load-bearing: `board`, `status`, `reset`, `mode`, `valueX`/`valueO`/`valueDraw`, `labelX`/`labelO`.

When restyling, preserve these class/ID names. When editing logic, keep `index.html` self-contained — do not introduce external files or a build step.
