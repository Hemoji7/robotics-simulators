# robotics-simulators

Browser-based 3D simulators for industrial robot arms, with controller-style program operation.

**Live site:** https://hemoji7.github.io/robotics-simulators/

## Purpose

A hobby project to help students learn industrial robot operation. Students can practise jogging, positions, and teach-pendant style programs in the browser. It is for learning and practice, not for programming real robots.

## Author

Hemoji Rao G

## Simulators

| Folder | Robot | Status |
|---|---|---|
| [`fanuc-er4ia/`](fanuc-er4ia/) | Fanuc ER-4iA (R-30iB style operation) | Available |
| [`yaskawa-yrc1000micro/`](yaskawa-yrc1000micro/) | Yaskawa Motoman YRC1000micro (INFORM-style teaching subset) | Available |
| `abb-irb14050/` | ABB IRB 14050 with OmniCore C30 | Planned |

Each simulator is a single self-contained `index.html` file. Open it in a modern browser; it loads Three.js from a CDN, so an internet connection is needed.

## Important

These simulations are approximations for learning and demonstration. Geometry, joint limits, and sample programs are not manufacturer data and must not be used to program or operate real robots. Always follow the manufacturer's documentation and safety procedures.

## Versioning

Each simulator is versioned on its own. Versions use semantic numbering (major.minor.patch), and each simulator's changes are recorded in its `CHANGELOG.md`. Release tags use the simulator prefix, for example `er4ia-v1.0.0`.

## License

MIT. See [LICENSE](LICENSE).
