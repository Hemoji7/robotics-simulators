# Fanuc ER-4iA simulator

A browser-based 3D simulation of the Fanuc ER-4iA six-axis arm with teach-pendant style operation.

## Purpose

A hobby project to help students learn industrial robot operation. Students can practise jogging, positions, and teach-pendant style programs in the browser. It is for learning and practice, not for programming real robots.

## Author

Hemoji Rao G

**Open it:** [fanuc-er4ia](https://hemoji7.github.io/robotics-simulators/fanuc-er4ia/) (or open `index.html` locally in a modern browser).

## Features

- Interactive 3D view: drag to orbit, wheel to zoom, double-click to reset.
- Jog joints J1 to J6 or move the tool in X, Y, and Z (position only).
- Gripper types: parallel, wide parallel, and vacuum cup.
- Positions: record the current pose or use "Current position" in the program builder.
- Program tab: sample programs from simple to advanced, custom scripts, step, pause, and stop.
- Joint labels, axis display, and per-joint colour coding.

## Program language

| Command | Meaning |
|---|---|
| `J P[n] [%]` | Joint move to position n, at a percentage of maximum speed |
| `L P[n] [mm/s]` | Straight-line TCP move to position n |
| `GRIP OPEN` / `GRIP CLOSE` | Open or close the fingers, or release and grip with the vacuum cup |
| `WAIT sec` | Pause for the given time |
| `END` | End the program |

Text after `;` is a comment and is shown as the step explanation.

## Limitations

- Geometry, joint limits, and sample poses are approximations, not Fanuc CAD data.
- J2 is restricted to 0° to 120° so the upper arm stays above the base.
- No collision checking.
- TP and KAREL are not interpreted.
- Saved custom scripts are kept in the browser. Use "Download .json" to keep a copy.

## Version

See [CHANGELOG.md](CHANGELOG.md). The current version is shown in the simulator's footer.
