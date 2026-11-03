# Repository Guidelines

## Project Structure & Module Organization

n-gon is a browser-based 2D physics roguelite using vanilla JavaScript and Matter.js.

- `index.html` defines the page, menus, canvas, and script loading order.
- `style.css` contains UI styles; `favicon.ico` supplies the browser icon.
- `js/` contains gameplay systems: `simulation.js` for the game loop, `player.js` for player behavior, `bullet.js` for weapons, `mob.js` and `spawn.js` for enemies, and `tech.js` for upgrades. Level, editor, and save systems also live here.
- `lib/matter.min.js` is the bundled physics engine. Avoid incidental vendor edits.
- No dedicated test directory or package manifest is present.

## Build, Test, and Development Commands

Run commands from the repository root:

```bash
python3 -m http.server 8000 --bind 127.0.0.1
```

Open `http://localhost:8000` to play. Static files run directly; no build or dependency installation is required. Stop the server with Ctrl+C.

Check JavaScript syntax with Node.js:

```bash
for file in js/*.js; do node --check "$file" || break; done
```

## Coding Style & Naming Conventions

Use four-space indentation and follow surrounding conventions for quotes and semicolons; existing files vary. Use camelCase for functions and properties, and descriptive lowercase or hyphenated filenames consistent with `level-editor.js`. Prefer focused edits over whole-file formatting. No shared formatter or linter configuration is checked in.

Scripts share global objects and depend on the ordering in `index.html`. Preserve initialization order and register new scripts explicitly.

## Testing Guidelines

No automated test framework, test naming convention, or coverage threshold is configured. Validate changes in the browser: start a run, exercise affected controls and gameplay, and inspect the console for errors. For UI changes, check the title screen, menus, and in-game HUD. For editor or save changes, verify the affected create, load, and round-trip flows. Record reproduction steps and the randomization seed for gameplay bugs. Syntax checks alone do not verify runtime behavior.

## Commit & Pull Request Guidelines

Recent commits use short, descriptive subjects such as `plasma ball rework` and `level editor (beta)`; no mandatory prefix is evident. Keep commits focused. Pull requests should explain the change, provide reproduction and validation steps, link relevant issues, and include screenshots or short recordings for visible changes.
