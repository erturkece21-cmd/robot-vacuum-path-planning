# Robot Vacuum Path-Planning Simulation

A real-time robot-vacuum navigation simulator that implements and visually compares classic **path-planning algorithms** on a 2D indoor map. Built in Python with an interactive Pygame dashboard for a Computational Geometry elective at Istanbul Technical University.

---

## Overview

The simulator models a robot vacuum moving through a room with walls and obstacles. It plans a collision-free route from a start position to target points and lets you run and compare four planners on the same map, so their behaviour and resulting paths can be observed side by side.

## Algorithms

| Planner | Type | Idea |
|---------|------|------|
| **A\*** | Graph search | Heuristic (Euclidean) shortest-path search over a visibility graph. |
| **Dijkstra** | Graph search | Uniform-cost shortest-path search (no heuristic). |
| **PRM** | Sampling-based | Probabilistic Roadmap — samples free points, connects nearby collision-free pairs, then searches the roadmap. |
| **RRT** | Sampling-based | Rapidly-exploring Random Tree — incrementally grows a tree toward the goal by steering from random samples. |

## Computational-geometry core

- Segment–segment intersection via CCW (counter-clockwise) orientation tests.
- Segment vs. polygon-obstacle collision checking.
- **Visibility-graph** construction from obstacle vertices, used by the A\* and Dijkstra planners.

## Environment

- A 12 × 9 m room represented as an **occupancy grid** (0.2 m cells, NumPy) plus **polygon obstacles** for the geometry engine.
- Boundary walls, interior walls with gaps, and rectangular obstacles, with several target points to navigate to.

## Tech Stack

**Python** · NumPy · Pygame

## Run

```bash
pip install -r requirements.txt
python main.py
```

Select a planner from the on-screen dashboard to run it; press **ESC** to quit.

## Project Structure

```
main.py              App entry point and render loop
environment.py       Builds the room, walls and obstacles
grid_map.py          Occupancy grid (MapGrid)
geometry.py          Computational-geometry core (intersection, visibility graph)
planner_astar.py     A* planner
planner_dijkstra.py  Dijkstra planner
planner_prm.py       PRM (Probabilistic Roadmap) planner
planner_rrt.py       RRT (Rapidly-exploring Random Tree) planner
ui_dashboard.py      Interactive Pygame dashboard
ui_theme.py          Colours / theme
ui_widgets.py        Panels, buttons, text helpers
requirements.txt     Dependencies
```

## Authors

Developed by **Ece Ertürk** and project teammates for the Computational Geometry course, Istanbul Technical University.
