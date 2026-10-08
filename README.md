# CDALib Documentation

Documentation website for [CDALib](https://github.com/CDAFM-Robotics/CDALib) — an FTC robot
library built on PedroPathing and PhotonFTC, providing subsystems, tasks, controllers, and a
modular OpMode framework.

**Live site:** https://cdafm-robotics.github.io/CDALib-website/

## Contents

The site is a set of self-contained, static HTML pages (all CSS inlined, no external resources)
plus the generated Javadoc API reference.

| Path | Purpose |
|------|---------|
| `index.html` | Landing page |
| `overview.html` | What CDALib is and how the pieces fit |
| `installation.html` | JitPack + Gradle setup |
| `getting-started.html` | First `ModularOpMode`, registration, lifecycle |
| `modular-opmode.html` | `ModularOpMode` deep dive |
| `subsystems.html` | `Subsystem` lifecycle and provided subsystems |
| `devices.html` | Hardware device wrappers |
| `controllers.html` | PID / feedforward / compound controllers |
| `bindings.html` | Named gamepad button/analog bindings |
| `tasks.html` | Task framework and composition |
| `modules.html` | OpMode-shaped modules (incl. PedroPathing TeleOp) |
| `telemetry.html` | `TelemetryManager` and tagged entries |
| `javadoc/` | Generated Javadoc API reference |

## Hosting

Served via GitHub Pages from the `main` branch root. A `.nojekyll` file disables Jekyll
processing so the Javadoc files are served as-is.
