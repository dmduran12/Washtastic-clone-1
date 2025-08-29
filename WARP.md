# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

Status and focus
- Current focus: V0.4. Use V0.4 artifacts for all work, reviews, and discussions.
- Deprecated: V0.3.5 is deprecated and retained for historical reference only. Do not modify or extend V0.3.5 except for documentation/labeling.

Repository overview
- This repository is not a software codebase. It contains manufacturing outputs and documentation for the “WashTastic” Meshtastic-based hardware node.
- There are no build, lint, or test scripts in this repo.
- From README.md: boards are provided under CC BY-NC-ND 4.0; most boards have not been tested (order at your own risk). “WashTastic” is a 1W node based on E22-90030S and a Pro Micro NRF52 module.

High-level structure (big picture)
- Versioned hardware releases live under directories named V<version>/ (e.g., V0.3.5, V0.4). Each contains:
  - A Gerber ZIP for PCB fabrication
  - BOM CSV variants (connectors/no-connectors; plus BME280 variants for 0.3.5)
  - Pick-and-place (PnP) CSV
- The root also includes earlier V0.3.3 artifacts and a pics/ folder with renders/diagrams.
- The primary board documentation is in “Readme Washtastic.md”.
- The WashTastic/ folder currently has no design source files in this clone; only manufacturing outputs are present.

Common terminal commands (macOS/zsh)
- List available hardware revisions
  - ls -1d V*/
- Preview a BOM as an aligned table (V0.4)
  - column -s, -t V0.4/BOM_1W-meshtastic-node_0.4_connectors.csv | less -S
- Compare BOM variants (V0.4)
  - diff -u V0.4/BOM_1W-meshtastic-node_0.4_connectors.csv V0.4/BOM_1W-meshtastic-node_0.4_no-connectors.csv
- Inspect contents of a Gerber ZIP (V0.4)
  - unzip -l V0.4/Gerber_1W-meshtastic-node_PCB_1W-meshtastic-node-0.4.zip
- Open board images/diagrams (V0.4)
  - open pics/V0.4/top_V0.4.png
- Preview pick-and-place files (V0.4)
  - column -s, -t V0.4/PickAndPlace_PCB_WashTastic-1W-meshtastic-node_V0.4.csv | less -S

Notes for future updates
- Treat V0.3.5 as read-only history. If a change is unavoidable, add/adjust deprecation labels only.
- Follow the observed structure when adding a new hardware revision: create a V<version>/ directory and include a Gerber ZIP, BOM CSV(s), and a PnP CSV. Update “Readme Washtastic.md” with release-specific notes. There are no automated build/test steps in this repo.

