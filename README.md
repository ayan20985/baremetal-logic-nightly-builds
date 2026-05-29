# bareMetal Logic Nightly Builds

Download the latest Windows build from [Releases](https://github.com/ayan20985/baremetal-logic-nightly-builds/releases).

## Release history

### v44.03

- Fixed: isometric voxel view depth buffer used a constant z, which caused z-fighting and stippled faces; ortho and perspective now use view-space depth
- Fixed: perspective voxel view no longer rasterizes faces with clipped or invalid vertices, which produced screen-spanning triangles and heavy lag at some camera angles
- Fixed: loading overlay shows loadingAnimation.gif circuit preview when the file is beside the exe or under release/assets
- Added: wire probing (P on cursor) with oscilloscope panel showing digital charge traces per simulation tick (View menu to toggle panel; up to 8 probes; highlighted wires on canvas)
- Improved: shared imgui panel toolbar helpers (main viewport menu styling + oscilloscope theme); scope View menu left and zoom/fit cluster right; bottom bar shows selected-probe period/frequency and is no longer clipped
- Fixed: scope View menu popup padding no longer double-pops imgui style stack (PopStyleVar/PopStyleColor errors)
- Changed: probed wire canvas outlines are thicker and match scope trace colors
- Added: oscilloscope Data menu with CSV import/export (settings, markers, reserved header rows, then sample data); marker/cursor overview positions use closest tick match and zoomed viewport mapping on the main plot
- Changed: status bar history controls (rewind, play, timeline toggle, node count) moved into a History drop-up menu with main-menu popup padding; undo and redo stay as buttons
- Changed: history viewer panel uses dark green theme, toolbar title reads History viewer
- Fixed: pause, edit canvas, then resume or step no longer resets all wire charges to zero (charges are preserved by pixel-to-wire mapping; merged wires take the max of contributing prior charges)
- Fixed: paused single-step after edits syncs the full canvas from simulation once so unchanged wires do not flash stale pixel colors for one frame

[Download v44.03](https://github.com/ayan20985/baremetal-logic-nightly-builds/releases/tag/v44.03)

### v44.02

- Fixed: jumping to an early history node from the latest no longer rebuilds the simulation on every undo/redo step (one rebuild per touched layer at the end)
- Added: history timeline zoom with mouse wheel, plus Fit and Current buttons to see long histories without endless panning
- Improved: history toolbar uses full-width grey bar with 8px inset for labels and buttons; bottom-left resize grip works again
- Fixed: history Fit zoom uses the graph area size instead of the toolbar strip, so it no longer zooms way out
- Fixed: mouse wheel over the history panel no longer zooms the main canvas (only the timeline graph zooms)
- Improved: drawing on large canvases updates only dirty quadtree regions instead of recompositing the full canvas each edit
- Fixed: first placed pixel and first few edits after load now appear immediately (per-pixel composite texture upload; edit updates take priority over simulation incremental redraw)
- Fixed: ghost, line preview, paste preview, cursor, and placed pixels stay aligned at high zoom and when panned (screen mapping matches clipped canvas blit)
- Fixed: ImGui Alt+Tab and stuck focus no longer brick the game (Alt+Tab blocked from ImGui, keyboard nav disabled, input cleared on focus change; Tab wire toggle ignores Alt)
- Added: single-tick simulation step while paused (Step button in top bar or with N key); documented in Help under Simulation
- Added: 3D viewer auto-homes on startup and when opening or loading a design
- Improved: Live Minimap, Live 3D, 3D On/Off, 3D Home, and Isometric/Perspective moved to the View menu (less cluttered top bar)
- Fixed: stray pixel on startup (T toggle now tracked in keyboard state; inputs ignored for the first few frames after boot)
- Improved: Live 3D is on by default
- Improved: while paused, simulation rebuilds and history graph layout updates are deferred until resume so edits stay responsive
- Fixed: paused edits now update the canvas immediately (display composites from pixel layers, not stale simulation state)
- Fixed: simulation step (N) while paused updates the canvas again; unpausing after paused edits + step refreshes without needing another edit
- Added: Space toggles pause/resume; T toggles pixel at cursor (was Space)
- Added: full-screen loading overlay (45% dim) via setLoadingOverlay/loadingPulse when opening designs; blocks input, pauses simulation, and keeps menus plus the previous canvas visible above the 3D view
- Improved: loading overlay plays loadingAnimation.gif as a live circuit preview — all four layers shown at once in a 2x2 grid (L0 top-left through L3 bottom-right), stepped at 15 TPS; uses the dot spinner if the file is missing
- Fixed: open-from-menu load no longer crashes ImGui (deferred until after UI render)
- Added: Edit menu stepping modes for Global stepping (default, full canvas sync) and Localized stepping (changed wires only).
- Improved: paused edits no longer seed simulation wire charge from placed pixel voltage; charges settle when stepping or unpausing
- Improved: power-source wires skip further stepping once saturated at max charge
- Fixed: multi-layer paste (Ctrl+Shift+C) anchors at the current layer and fills downward; excess layers are truncated below layer 0
- Changed: window title shows the build version (vXX.XX locally; nightly CI uses the resolved package version)

[Download v44.02](https://github.com/ayan20985/baremetal-logic-nightly-builds/releases/tag/v44.02)

### v44.01

- Fixed: very large canvases no longer become extremely laggy when panning, zooming, or running simulation
- Improved: simulation updates now redraw only changed wires instead of recompositing the entire canvas every step
- Improved: texture uploads now update only the changed region on large maps
- Improved: when zoomed in, only the visible canvas region is drawn to the screen

[Download v44.01](https://github.com/ayan20985/baremetal-logic-nightly-builds/releases/tag/v44.01)

