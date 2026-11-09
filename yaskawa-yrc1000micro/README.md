# Yaskawa YRC1000micro simulator

A browser-based 3D simulation of a small six-axis MOTOMAN-class arm, run from a YRC1000micro-style controller with a teach-pendant style panel. It follows the [Fanuc ER-4iA simulator](../fanuc-er4ia/) and adds controller features that are specific to the YRC1000micro.

## Setup (Three.js)

The page uses Three.js r128, included in `vendor/three.min.js` (MIT licence, from https://github.com/mrdoob/three.js at tag r128). Keep the folder next to `index.html`. If the file is missing, the page tries the CDN, and if that also fails it shows a message explaining what to add.

## Purpose

A hobby project to help students learn industrial robot operation. Students can practise jogging, positions, digital I/O, and small programs in the browser. It is for learning and practice, not for programming real robots.

## Author

Hemoji Rao G

## Features

- Interactive 3D view: drag to orbit, wheel to zoom, double-click to reset.
- Jog joints J1 to J6 or move the TCP in X, Y, and Z (position only).
- Positions named P001, P002, and so on, as on the controller. Record the current pose or use "Current position" in the program builder.
- **I/O tab:** simulated inputs IN#(1) "Part present" and IN#(2) "Bin full", plus output OT#(1) for the gripper or vacuum. Inputs are toggled by hand, as a sensor would change.
- **Wait on input:** `WAIT IN#(n)=ON` holds the program until the input matches. Toggling the input during a run releases it.
- **Cycle timer:** shows the time for the current or last program run and a count of finished programs. The count can be reset.
- **Payload interlock:** the Status tab has a payload setting. If it is above the rated payload of the model, Run is blocked with an alarm.
- **Controller block:** a simplified teach-pendant and cabinet front panel, always visible above the tabs. Mode key TEACH / PLAY / REMOTE; SERVO ON / OFF; an ENABLE button that must be on to jog or move by hand; an EMERGENCY STOP that latches and stops any program until it is released and servo is turned on again; START (external start) for REMOTE mode; and an alarm history.
- **Reachability alarm:** a `MOVL` that cannot be reached within the joint limits stops the program with an alarm.
- Gripper types: parallel, wide parallel, and vacuum cup.
- Program tab with nine sample programs, from simple to advanced, plus custom scripts, step, pause, and stop.

## Program language (teaching subset)

The syntax follows the style of the YRC1000micro's INFORM language, but only these commands are interpreted.

| Command | Meaning |
|---|---|
| `MOVJ Pnnn VJ=%` | Joint move to position Pnnn, at a percentage of maximum speed |
| `MOVL Pnnn V=mm/s` | Straight-line TCP move to position Pnnn |
| `DOUT OT#(1) ON` / `OFF` | Close the gripper (or switch vacuum on), or open it (or switch vacuum off) |
| `TIMER T=sec` | Pause for the given time |
| `WAIT IN#(n)=ON` / `OFF` | Hold until the input matches; `n` is 1 or 2 |
| `NOP` | No operation; takes one scan |
| `END` | End the program |

A `'` starts a comment, as in INFORM. `;` also works in this simulator. Comment text is shown as the step explanation.

## Limitations

- The arm geometry, joint limits, and sample poses are approximations for a generic small robot. They are not MOTOMAN data, and the model is not a specific robot.
- The controller is simulated only as far as the commands above. INFORM job structure, labels, jumps, registers, arc and spot weld instructions, and user frames are not interpreted.
- No collision checking.
- The controller replica is simplified: the ENABLE control is a button rather than a three-position switch, the mode key and alarm codes are teaching approximations, and the pendant screen is not a copy of the real touch-screen interface.
- The payload rating (7 kg in this model) is illustrative. The real YRC1000micro is rated for robots up to about 12 kg, and the rating depends on the robot.
- Saved custom scripts are kept in the browser. Use "Download .json" to keep a copy.

## Version

See [CHANGELOG.md](CHANGELOG.md). The current version is shown in the simulator's footer.
