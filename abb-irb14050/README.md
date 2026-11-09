# ABB IRB 14050 YuMi simulator

A browser-based 3D simulation of the ABB IRB 14050 single-arm YuMi, a seven-axis collaborative robot, run from an OmniCore C30 style controller with a teach-pendant style panel. It follows the [Fanuc ER-4iA](../fanuc-er4ia/) and [Yaskawa YRC1000micro](../yaskawa-yrc1000micro/) simulators, and adds features specific to the IRB 14050.

## Setup (Three.js)

The page uses Three.js r128, included in `vendor/three.min.js` (MIT licence, from https://github.com/mrdoob/three.js at tag r128). Keep the folder next to `index.html`. If the file is missing, the page tries the CDN, and if that also fails it shows a message explaining what to add.

## Purpose

A hobby project to help students learn industrial robot operation. Students can practise jogging, positions, digital I/O, and small programs in the browser. It is for learning and practice, not for programming real robots.

## Author

Hemoji Rao G

## Features

- Interactive 3D view: drag to orbit, wheel to zoom, double-click to reset.
- Joint jog for the seven axes (A1, A2, A7, A3, A4, A5, A6), or Cartesian jog of the TCP in X, Y and Z. Cartesian jog keeps the tool pointing the way it was when the jog started.
- Positions named p10, p20 and so on. Record the current pose, or use "Current position" in the line builder.
- **I/O tab:** simulated inputs diPart ("Part present") and diBin ("Bin full"), plus output doGrip for the gripper or vacuum.
- **Wait on input:** `WaitDI diPart, 1;` holds the program until the input matches. Toggling the input during a run releases it.
- **Controller block:** MANUAL and AUTO mode; SERVO ON / OFF; an ENABLE button that must be on to move by hand or step; an EMERGENCY STOP that latches and stops any program until it is released and motors are turned on again; START in AUTO; and an alarm history.
- **Speed limits:** in MANUAL mode the TCP is limited to 250 mm/s in this model. Each axis moves at its datasheet maximum speed scaled by the program or jog speed.
- **Payload interlock:** the Status tab has a payload setting. If it is above the rated 0.5 kg, Run is blocked with an alarm.
- **Reachability alarm:** a `MoveL` that cannot be reached on a straight line, with the taught tool direction, stops the program with an alarm.
- Gripper types: servo gripper (two fingers) and vacuum cup.
- Program tab with ten sample programs, from simple to advanced, plus custom programs, step, pause, and stop.
- Colour coding: each arm segment and joint cover takes its axis colour.
- Joint labels show only the moving axis; each axis has its own colour.

## Program language (teaching subset)

The syntax follows the style of RAPID, ABB's robot language, but only these instructions are interpreted.

| Instruction | Meaning |
|---|---|
| `MoveJ pN, vP;` | Joint move to position pN, at P percent of maximum axis speed |
| `MoveL pN, vV;` | Straight-line TCP move to position pN, at V mm/s |
| `SetDO doGrip, 0\|1;` | Open the gripper (or switch vacuum off), or close it (or switch vacuum on) |
| `WaitDI diPart\|diBin, 0\|1;` | Hold until the input matches |
| `WaitTime T;` | Pause for T seconds |
| `ENDPROC` | End the program |

A `!` starts a comment, as in RAPID. Comment text is shown as the step explanation. Real RAPID uses speed data and zone data (for example `v100`, `fine`) and a module structure. This page does not interpret those, and `MoveJ` speed is a percentage here.

## Where the numbers come from

Joint working ranges and maximum axis speeds are from the ABB IRB 14050 datasheet (ABB document 9AKK107046A3806, revision E). The 559 mm reach and 0.5 kg rated payload are from the same datasheet. Link lengths, base shape, gripper, controller panel and the 250 mm/s manual limit are approximations for teaching.

## Limitations

- Link lengths, shapes and sample poses are approximations, not ABB CAD data.
- The controller is simulated only as far as the commands above. RAPID modules, routines, data types, zones, tools and work objects are not interpreted.
- No collision checking, and no check of the table, bins or pallet. Positions can overlap.
- The controller panel is simplified: the ENABLE control is a button rather than a three-position switch, and the alarm texts are teaching approximations, not a real OmniCore alarm list.
- Motion timing follows the screen's frame rate, so the same program runs a little faster on a high-refresh display.
- Saved custom programs are kept in the browser. Use "Download .json" to keep a copy.

## Version

See [CHANGELOG.md](CHANGELOG.md). The current version is shown in the footer.
