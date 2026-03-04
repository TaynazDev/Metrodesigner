# 🚇 Metro Designer

**[taynazdev.github.io/Metrodesigner/](https://taynazdev.github.io/Metrodesigner/)**

A browser-based metro map designer. Draw lines, place stations, and watch trains run your network — all in a single HTML file with no dependencies.

---

## Features

- **Freehand line drawing** — sketch a route freely; it snaps to clean 45°/90° grid segments on release
- **Station placement** — stations snap to the dot grid; ghost preview shows where the station will land
- **Animated trains** — trains run automatically on every line, stopping at each station
- **Interchange detection** — stations shared by two or more lines render as interchange circles
- **Station open/close** — toggle stations closed; trains skip closed intermediate stops and still reverse at termini
- **Line & station naming** — rename anything by double-clicking on the canvas or typing in the toolbar input
- **486 real station names** — drawn from `stations.md` and assigned automatically
- **Zoom & pan** — scroll wheel to zoom, right-click drag (or Alt+drag) to pan
- **Sidebar** — Lines and Stations tabs list everything on the map

## Controls

| Action | How |
|---|---|
| Select / move station | `V` or Select tool, then click & drag |
| Add station | `S` or Station tool, then click |
| Draw line | `L` or Line tool, then click & drag |
| Toggle station closed | `C` or Close/Open tool, then click |
| Add train to selected line | `T` or Add Train button |
| Rename station | Double-click station on canvas |
| Rename line | Double-click line on canvas, or use the toolbar input when a line is selected |
| Delete selected | `Delete` / `Backspace` |
| Pan | Right-click drag, middle-click drag, or Alt+drag |
| Zoom | Scroll wheel |
| Reset view | Reset View button |

## Usage

Open `index.html` in any modern browser — no server or build step required.
