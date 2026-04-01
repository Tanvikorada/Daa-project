# 💣 MineTracer — Backtracking Visualizer

An interactive web-based visualizer that demonstrates the **Backtracking algorithm** by solving a minefield pathfinding problem in real time. Built as a **Design & Analysis of Algorithms (DAA)** course project.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=flat&logo=threedotjs&logoColor=white)

---

## 🎯 Overview

MineTracer visualizes how the **backtracking algorithm** explores an N×N grid to find the **shortest safe path** from the top-left corner `S(0,0)` to the bottom-right corner `E(N-1, N-1)`, while avoiding randomly placed mines.

### Key Concepts Demonstrated

- **Backtracking** — Recursive exploration of all possible paths with undo (backtrack) on dead ends.
- **Pruning** — Cutting off branches where the current path length already exceeds the best known solution.
- **Exhaustive Search** — Guarantees the shortest path by exploring all valid routes.
- **BFS Validation** — Ensures every generated grid has at least one solvable path.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🎮 **Interactive Grid** | Click cells to manually toggle, place, or erase mines |
| ⚡ **Real-Time Visualization** | Watch the algorithm explore, backtrack, and find the optimal path step-by-step |
| 📊 **Live Stats** | Track steps, backtracks, path length, and solver status in real time |
| 🎚️ **Configurable Parameters** | Adjust grid size (6×6 → 12×12), mine density (8–40%), and animation speed |
| 🧊 **3D Intro Animation** | Immersive Three.js-powered 3D intro scene of the minefield |
| 📚 **Built-in Algorithm Explainer** | Concept, step-by-step walkthrough, pseudocode, complexity analysis, and BFS/DFS comparison |
| 📖 **How to Play Guide** | Interactive onboarding overlay for first-time users |
| 🌙 **Dark Theme UI** | Sleek, modern dark interface with JetBrains Mono + Syne typography |

---

## 🚀 Getting Started

### Prerequisites

- Any modern web browser (Chrome, Firefox, Edge, Safari)

### Run Locally

1. **Clone the repository**
   ```bash
   git clone https://github.com/<your-username>/minetracer.git
   cd minetracer
   ```

2. **Open the app**
   ```
   Just open index.html in your browser — no build step or server required.
   ```

> **Tip:** You can also use a local server for development:
> ```bash
> npx serve .
> ```

---

## 🕹️ How to Use

1. **Configure** — Pick a grid size and mine density from the left panel.
2. **Generate** — Click **⟳ New Minefield** to create a solvable grid (path is guaranteed via BFS pre-check).
3. **Solve** — Hit **▶ Solve** and watch backtracking in action. Slow down the speed to observe every decision.
4. **Interact** — Toggle between edit modes to manually place or erase mines.
5. **Learn** — After solving, click **"See step-by-step explanation"** in the result banner, or open **Learn Algorithm** from the nav bar.

---

## 🧠 Algorithm Details

### Backtracking Approach

```
SOLVE(grid, N):
  bestPath ← []

  function BACKTRACK(row, col, path, visited):
    if out-of-bounds OR mine OR visited  → return
    if len(path)+1 ≥ len(bestPath) > 0   → return   // Prune

    visited.add(row, col)
    path.append((row, col))

    if (row,col) == (N-1,N-1):
      bestPath ← copy(path)               // New best!
    else:
      for (dr,dc) in [UP, DOWN, LEFT, RIGHT]:
        BACKTRACK(row+dr, col+dc, path, copy(visited))

    path.pop()                             // Backtrack!

  BACKTRACK(0, 0, [], {})
  return bestPath
```

### Complexity

| Metric | Value | Notes |
|---|---|---|
| **Time (Worst Case)** | O(4^N²) | 4 directional branches per cell |
| **Space (Stack)** | O(N²) | Maximum recursion depth |
| **Practical Performance** | Much better | Pruning + mines eliminate huge subtrees |

---

## 🗂️ Project Structure

```
daaproject/
├── index.html      # Complete single-file application (HTML + CSS + JS)
└── README.md       # This file
```

---

## 🛠️ Tech Stack

- **HTML5 / CSS3 / Vanilla JavaScript** — Zero dependencies, runs entirely in the browser
- **Three.js** (CDN) — 3D WebGL intro animation
- **Google Fonts** — JetBrains Mono (monospace) + Syne (display)

---

## 📸 Visual Legend

| Symbol | Meaning |
|---|---|
| **S** | Start cell (0,0) |
| **E** | End cell (N-1, N-1) |
| 💣 | Mine (blocked cell) |
| ★ | Current cell being explored |
| ● | Cells on the shortest path |
| ✗ | Backtracked cells |
| · | Visited cells |

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

<p align="center">
  Built with ❤️ as a <strong>DAA Course Project</strong>
</p>
