# Changelog: Fanuc ER-4iA simulator

All notable changes to this simulator are recorded here. Versions follow semantic numbering.

## 1.3.0

- Same screen layout as the Yaskawa and ABB simulators: the controller block (MODE, SERVO, ENABLE, E-STOP, RESET, START) sits above the tabs, and the tabs are JOG, POSITIONS, I/O, STATUS and PROGRAM.
- Positions and I/O have their own tabs (they were folded into JOG and STATUS).
- START button (AUTO mode), in addition to Run.
- Payload interlock (4 kg rated) and a cycle timer with a cycle count, as on the other two simulators.
- Home button in the view returns to the home page.
- Three.js is loaded from the local vendor folder, so the page works offline.

## 1.2.0

- Mode key: AUTO (program run, jog off), T1 (manual, 25% max), and T2 (manual, full speed).
- Servo ON and OFF (motor power). Servo starts off, so turn it on before jogging or running.
- Deadman enable switch: hold it on for jog and Step in T1 and T2.
- Emergency stop latches: it stops motion and the program and turns the servo off. Reset it, then turn the servo on.
- Home, Zero, position Go, and Run are blocked while the servo is off or the emergency stop is active. Run also needs AUTO.

## 1.1.0

- Controls pane simplified to three tabs: JOG, PROGRAM, and STATUS. Positions moved to the top of PROGRAM.
- Mode switch: AUTO and T1. T1 is a reduced-speed test mode where Run is blocked and Step is allowed.
- Frames for Cartesian jog: World, User (turned about Z by an angle you set), and Tool (TCP).
- Simulated digital I/O: 8 inputs (click to toggle) and 8 outputs. Programs can use SET DO[n] ON|OFF and WAIT DI[n] ON|OFF.
- Alarm and event log in STATUS: joint limit reached, program error, and mode changes, with timestamps.

## 1.0.0

First public release.

- 3D arm with per-joint colour coding and joint labels that show only the moving axis.
- Joint and Cartesian jog, override, Home, and Zero.
- Program tab with sample programs (12, simple to advanced) and custom scripts.
- Run, Step, Pause, and Stop. Editing and selection are locked while a program is active.
- Command builder with "Current position" as the default position.
- Gripper types: parallel, wide parallel, and vacuum cup.
- Teach-pendant style Controls pane with JOG, POSITIONS, STATUS, and PROGRAM tabs. (Superseded in 1.1.0.)
- J2 limited to 0° to 120° so the upper arm stays above the base.
- Download and open custom scripts as `.json` files.
