# Changelog: ABB IRB 14050 simulator

All notable changes to this simulator are recorded here. Versions follow semantic numbering.

## 1.1.0

- Colour coding: each arm segment and joint cover takes the colour of its axis (A1 blue, A2 orange, A7 teal, A3 green, A4 violet, A5 red, A6 cyan, gripper pink). The "Colours" button in the view switches back to the ABB white housings.
- Fixed a gap between the flange and the gripper. The gripper now attaches to the flange.

## 1.0.0

First public release.

- Seven-axis model of the IRB 14050 single-arm YuMi, with joint working ranges and maximum axis speeds from the ABB IRB 14050 datasheet. Reach is 559 mm and the rated payload is 0.5 kg.
- Axes are named by ABB axis number (A1, A2, A7, A3, A4, A5, A6) in the physical order of the chain.
- Tool direction is held during Cartesian jog and MoveL, so the gripper keeps pointing down as the arm moves.
- Controller block: MANUAL / AUTO mode, Motors ON / OFF, a held enabling device, EMERGENCY STOP with release, START in AUTO, and an alarm history. The mode cannot change while a program runs.
- Manual mode limits TCP speed to 250 mm/s (teaching value). Programs run in AUTO. Step runs in MANUAL with the enabling device held.
- RAPID-style teaching subset: `MoveJ`, `MoveL`, `SetDO doGrip`, `WaitDI diPart|diBin`, `WaitTime` and `ENDPROC`, with `!` comments.
- Positions named p10, p20 and so on. Record the current pose, or use "Current position" in the line builder.
- Simulated digital I/O: inputs diPart and diBin, output doGrip.
- Cycle timer and production counter, with a reset.
- Payload setting with an interlock that blocks Run above the rated 0.5 kg.
- Reachability alarm for `MoveL` moves that cannot be reached on a straight line with the taught tool direction.
- Ten sample programs, from single-axis moves to a three-slot palletizing cycle.
- Look and feel follow the YuMi reference photo: white housings, light grey joint covers, a dark flange, a white gripper body with dark fingers, and a red ABB wordmark on the base and gripper.
- Servo gripper (two fingers) and vacuum cup gripper types.
- Teach-pendant style Controls pane with JOG, POSITIONS, I/O, STATUS and PROGRAM tabs, and dockable panels.
- Download and open custom programs as `.json` files.
