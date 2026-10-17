# Autonomous Maze Solver — Code2Career AI Hackathon

An autonomous maze-solving robot developed for **Round 2 of the Code2Career AI Hackathon**, organized by Coding Ninjas at Lovely Professional University (LPU).

The challenge was to build the decision-making logic for a two-wheeled robot exploring an unknown maze using only its sensor readings. My approach went beyond basic wall-following by combining **persistent memory, maze mapping, odometry, and BFS-based navigation** to make exploration more systematic.

## What I Built

- **Autonomous decision-making:** Chose the robot's next action from its sensor readings at every tick.
- **Persistent memory:** Stored information between decisions instead of treating every tick as an isolated problem.
- **Maze mapping:** Built and updated an internal representation of the maze from observations.
- **Odometry and heading tracking:** Used wheel RPM and motion feedback to estimate position and orientation.
- **BFS path planning:** Used breadth-first search to plan routes through known open cells and support more purposeful exploration.
- **Collision awareness:** Used sensor and motion feedback to detect blocked movement and avoid unnecessary wall hits.
- **Local visualizer:** Used a Python GUI to watch runs, replay individual ticks, inspect sensor values, and diagnose unsuccessful attempts.

## How It Works

1. **Sense** — read front, left, and right distance sensors, wheel RPM, and acceleration.
2. **Update state** — estimate movement and heading from the previous action.
3. **Update the map** — record observed open cells and walls in memory.
4. **Plan** — use the known map and BFS to choose a useful route or exploration target.
5. **Act** — return one valid action: `forward`, `turn_left`, `turn_right`, or `wait`.
6. **Repeat** — continue until the robot reaches the goal or the run ends.

## Tech Stack

- **Language:** Python
- **Algorithms:** Breadth-first search (BFS), grid-based mapping, odometry-based state tracking
- **Interface:** Tkinter-based local visualizer
- **Libraries:** Python standard library

## Project Files

| File | Purpose |
|---|---|
| `robot.py` | Robot decision logic and sensor-to-action interface |
| `play.py` | GUI for running and replaying maze attempts |
| `sim_lite.py` | Local maze simulator used by the visualizer |
| `selftest.py` | Checks the robot program's input/output protocol |
| `CONTRACT.md` | Sensor, action, and simulation rules |
| `mazes/` | Practice maze layouts, when included |

## Running the Local Visualizer

Python 3.11+ is recommended. Tkinter is also required for the GUI.

1. Clone or download this repository.
2. Open a terminal in the project folder.
3. Run:

```bash
python play.py
```

Select a maze and press **Run**. Use the playback controls to inspect the robot's movement, decisions, and sensor readings tick by tick.

To check the robot's input/output protocol:

```bash
python selftest.py robot.py
```

> The visualizer is for local practice and debugging. It does not reproduce the competition's hidden test set or calculate the official score.

## What I Learned

This project gave me practical experience with autonomous-agent design, state estimation from noisy motion signals, mapping an environment incrementally, graph search, and debugging decisions through simulation. It also reinforced an important lesson: a robot needs not only to react to its immediate surroundings, but also to remember what it has learned and use that information to plan.

## Acknowledgements

The hackathon provided the problem statement, robot interface contract, and starter-kit structure. The mapping, memory, and BFS navigation approach described above reflects the advanced maze-solving strategy I worked on for the challenge.
