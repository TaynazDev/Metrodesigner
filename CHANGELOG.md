# Changelog

## [Unreleased] — 2026-03-04

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
