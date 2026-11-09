# Changelog: Fanuc ER-4iA simulator

All notable changes to this simulator are recorded here. Versions follow semantic numbering.

## 1.0.0

First public release.

- 3D arm with per-joint colour coding and joint labels that show only the moving axis.
- Joint and Cartesian jog, override, Home, and Zero.
- Program tab with sample programs (12, simple to advanced) and custom scripts.
- Run, Step, Pause, and Stop. Editing and selection are locked while a program is active.
- Command builder with "Current position" as the default position.
- Gripper types: parallel, wide parallel, and vacuum cup.
- Teach-pendant style Controls pane with JOG, POSITIONS, STATUS, and PROGRAM tabs.
- J2 limited to 0° to 120° so the upper arm stays above the base.
- Download and open custom scripts as `.json` files.
