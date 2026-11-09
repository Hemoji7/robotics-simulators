# Changelog: Yaskawa YRC1000micro simulator

All notable changes to this simulator are recorded here. Versions follow semantic numbering.

## 1.2.0

- Controller tab (CTRL): mode key TEACH / PLAY / REMOTE, Servo ON / OFF, enable switch, EMERGENCY STOP with release and reset, External START for REMOTE, and an alarm history. The LCD shows the mode, servo state and E-stop.
- Jog, Home, Zero and position moves need TEACH mode, servo on and the enable switch. Programs run from PLAY, or from External START in REMOTE. Changing the mode key is blocked while a program runs.
- Pressing the E-stop stops the program and turns the servo off. Runtime and payload alarms are written to the alarm history.
- Arm: tapered square base, tapered upper arm and forearm, dark window panels and a warning sticker on the upper arm, deeper blue, slimmer shoulder and elbow, and a three-quarter default camera.

## 1.1.0

- Arm restyled to match the reference photo: Yaskawa-style blue housings, dark hubs, black tool flange with a brass ring, and a white YASKAWA logo on both sides of the upper arm. Joint colours remain on the joint labels and the active-axis glow.
- Housings are a little larger, and the home and reference pose is the upright upper arm shown in the photo.
- Three.js loads from `vendor/three.min.js` first, then the CDN. If neither loads, the page explains what to download instead of showing a blank screen.

## 1.0.0

First public release. Built on the Fanuc ER-4iA simulator's 3D view, jog, and program engine.

- Generic small six-axis arm (not a specific MOTOMAN model), with per-joint colour coding and joint labels.
- Joint and Cartesian jog, override, Home, and Zero.
- Teaching subset of INFORM-style syntax: `MOVJ`, `MOVL`, `DOUT OT#(1)`, `TIMER T=`, `WAIT IN#(n)=`, `NOP`, `END`, and `'` comments.
- Positions named P001 and so on.
- I/O tab with simulated inputs IN#(1) and IN#(2) and output OT#(1).
- Cycle timer and production counter, with a reset.
- Payload setting with an interlock that blocks Run above the rated payload.
- Reachability alarm for `MOVL` moves that cannot be reached within the joint limits.
- Program tab with nine sample programs (from base-turn joint moves to a three-slot palletizing cycle), custom scripts, Run, Step, Pause, and Stop.
- Editing and selection are locked while a program is active.
- Teach-pendant style Controls pane with JOG, POSITIONS, I/O, STATUS, and PROGRAM tabs.
- Download and open custom scripts as `.json` files.
