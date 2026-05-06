# Changelog

## [Unreleased] — 2026-05-06

### Added
- **Startup metro menu** — after the splash screen, the app now opens a menu where you can select a saved metro or create a new one.
- **Multi-save slots** — metro designs are now stored in a save index (`metroDesignerSavesV1`) with per-save metadata instead of a single global save.
- **Save management actions** — each save row in the start menu now supports Duplicate, Rename, and Delete actions.
- **Back to menu control** — added a toolbar `Menu` button in the designer view to return to the metro-selection menu without refreshing.

### Changed
- **Curved track corners** — track lines now render with smooth quadratic-bezier bends at every corner using `drawRoundedPolyline`; the live freehand preview also uses curved corners for visual consistency.
- **Train follows curved path** — train position and heading are now interpolated along the same rounded-corner geometry (`sampleRoundedPathPoints`), keeping trains visually centred on curved bends instead of cutting corners.
- **Transition splash on metro entry** — loading into a metro now plays the splash again, including a dynamic label showing which metro is being loaded.
- **Splash branding** — both startup and transition splashes now show the `Metro Designer` title above the intro GIF.
- **Save name length rule** — metro save names are now capped at 20 characters across create, rename, duplicate, and load-label flows.
- **Station placement on rails** — placing a station directly on a line now inserts that station into the line path for all nearby lines (including same-colour lines), so the station immediately joins the route.
- **Web app icon** — configured `icon.png` as the page favicon.

---

## [0.1.0] — 2026-03-04

### Added
- **Station name pool** — new stations automatically receive real place names drawn from a 486-name pool sourced from `stations.md` (Abbotsford Road → Zinnia Cross), cycling in alphabetical order; pool resets on Clear.
- **Freehand line drawing** — replaced the click-to-connect tool with a marker-style drag tool; the raw stroke is shown in real time and straightens to valid 45 °/90 ° grid segments on mouse-up.
- **Grid-snap for stations** — stations can only be placed on grid dots; a ghost preview ring shows the target dot while hovering (turns orange if occupied).
- **Automatic loop line detection** — lines that connect back to their starting station automatically become circular routes; trains continuously circle without reversing at termini.
- **localStorage persistence** — all stations, lines, trains, viewport position, and zoom level automatically save to browser storage; designs persist across page refreshes and tab closures; auto-saves occur 500ms after any change with debouncing.
- `stations.md` — reference list of 486 metro station names.

### Changed
- **Line drawing no longer auto-places stations** — drawing a line only creates stations at the start and end endpoints; intermediate grid dots that coincide with existing stations are connected through automatically.
- **All trains travel in the same direction** — additional trains added via "Add Train" are placed with the same heading as the first train on the line.
- **Train continuation after line extension** — trains that had reversed at a terminus now continue forward when the line is extended beyond that terminus, rather than bouncing back; fixed progress check that was preventing proper train flipping when trains had moved beyond the terminus.
- **Head-prepend segment fix** — inserting stations before the start of a line correctly offsets all existing train segment indices so no train teleports.
- **Line rename input stays in sync** — switching between lines in the sidebar now always updates the name input to show the selected line's name; typing a new name updates the sidebar label in-place without disrupting the cursor.

### Fixed
- **Train reversal at extended termini** — removed restrictive progress check (`>= 0.9`) that prevented trains from being flipped forward when lines were extended; trains now properly continue toward new termini regardless of how far they've traveled backward.

### Removed
- River and zone creation tools (and all associated state, draw functions, and keyboard shortcuts).
