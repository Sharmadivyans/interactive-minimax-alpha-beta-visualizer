# Interactive Minimax + Alpha-Beta Visualizer

A lightweight browser app for visualizing **Minimax search with Alpha-Beta pruning**.

This project lets you:
- Provide your own game-tree data through a JSON input.
- Run alpha-beta pruning in the browser.
- See the computed node values and which branches were pruned.
- Quickly load a built-in **Example #5** dataset.

---

## Features

- **User-provided input** (no code edits needed).
- **Input validation** for depth, branching factor, and leaf count.
- **Tree rendering in SVG** with color-coded node roles:
  - Green: MAX nodes
  - Blue: MIN nodes
  - Purple: leaf nodes
  - Red (dashed edges): pruned subtree
- **Run summary** showing:
  - Best root value
  - Visited leaves
  - Pruned leaves

---

## Input Format

Use the JSON textbox in the UI with this shape:

```json
{
  "depth": 3,
  "branching": 2,
  "leafValues": [3, 5, 6, 9, 1, 2, 0, -1]
}
```

### Rules

- `depth`: integer `>= 1`
- `branching`: integer `>= 2`
- `leafValues`: array length must equal `branching^depth`

For example, when `depth=3` and `branching=2`, you must provide `2^3 = 8` leaf values.

---

## Quick Start

1. Open `index.html` in any modern browser.
2. (Optional) Click **Load Example #5**.
3. Edit JSON if you want to test your own tree.
4. Click **Run**.
5. Inspect the visualization and status line.

---

## How It Works (High Level)

1. A full tree is generated from `depth`, `branching`, and `leafValues`.
2. Alpha-beta pruning runs top-down from a MAX root node.
3. Each internal node receives its minimax value.
4. Branches cut by alpha-beta are marked as pruned.
5. The resulting tree is laid out and drawn as SVG.

---

## Project Files

- `index.html` — App UI, algorithm, validation, and SVG rendering.
- `screenshot.svg` — Static visualization artifact for Example #5.
- `README.md` — Project documentation.

---

## Notes

- This is a client-side educational visualizer (single HTML file).
- No external libraries are required.
- Node expansion order is left-to-right, which affects pruning behavior.
