BOTD Hockey Coaching Aid v6.5
Creator: Nicholas Heller

Release focus
-------------
Version 6.5 corrects timeline Glow/Blink playback, replaces puck-travel underlines with full-duration action clips, and removes the empty Telestration track whenever timed Telestration is not enabled.

The result is easier to read during playback: visual emphasis remains synchronized to moving players and the moving puck, pass and shot blocks directly show how long those actions take, and static marker artwork no longer consumes an unused timeline row.

What's new in v6.5
------------------
1. Glow and Blink remain visible during movement
   - Glow and Blink intervals are evaluated from the current timeline time on every rendered playback frame.
   - A glowing player remains highlighted while skating along a recorded movement path.
   - A glowing puck remains highlighted while being carried or traveling through a pass or shot.
   - Blink timing remains synchronized to the timeline even though player and puck SVG tokens are redrawn while moving.
   - Pausing inside a Glow/Blink interval displays the full glow so the interval is easy to inspect and edit.
   - Existing Glow color, Blink, Blink Rate, and Glow Time controls remain in the contextual timeline toolbar.
   - Multiple player and puck Glow/Blink intervals can still overlap independently.

2. Full-duration Pass and Shot clips
   - A pass or shot now appears as one rounded timeline block extending from the event start to puck arrival.
   - The previous thin blue travel underline is hidden.
   - Pass, pass-to-space, and shot actions retain their distinct colors and labels.
   - Selecting any part of the rounded action block selects that puck event for editing.
   - The block width updates while Travel Time is dragged, giving immediate visual feedback for puck speed changes.
   - Shot Power remains independent from Shot Travel Time.
   - Possession events remain compact point-in-time actions because they do not have travel duration.

3. Conditional Telestration timeline
   - With the TELESTRATION checkbox unchecked, marker artwork remains visible as static coaching-board markup.
   - The Telestration timeline row is completely removed in Static mode, eliminating unused vertical space.
   - Checking TELESTRATION enables timed playback and expands the DRAW/ERASE track.
   - Existing recorded DRAW and ERASE clips reappear when timed Telestration is enabled.
   - Unchecking the control hides the track again without deleting drawings or timed actions.
   - Display Time editing, progressive drawing playback, eraser playback, Undo/Redo, Play Options, and Copy & Reuse remain available when the timed track is enabled.

Using Glow/Blink on the timeline
--------------------------------
1. Select a player row, movement clip, puck row, or puck event.
2. Move the playhead to the desired start time.
3. Check Glow in the contextual timeline controls.
4. Choose a color and optionally enable Blink and adjust Blink Rate.
5. Move the playhead to the desired end time.
6. Uncheck Glow.
7. Press Play. The effect remains synchronized while the selected player or puck moves.

Using timed Telestration
-------------------------
Static coaching-board use:
- Leave TELESTRATION unchecked.
- Draw and erase normally.
- The final artwork remains visible and no Telestration row occupies timeline space.

Recorded playback use:
1. Check TELESTRATION.
2. Draw or erase at the current playhead position.
3. The action appears as a DRAW or ERASE clip.
4. Select the clip and use Display Time to change how quickly it plays.
5. Uncheck TELESTRATION to return to a compact static-markup timeline without deleting the recorded actions.

Core systems retained
---------------------
- Blank New board with one puck at center ice and two complete ordered benches.
- Inspector-free floating Player and Puck controls.
- Mid-playhead player rerouting that preserves the past and replaces only the selected player's future.
- Passes to players or open ice.
- Two-stage shot aiming, editable Shot Power, editable Travel Time, board-following paths, and board/net ricochets.
- Editable Skate Time with direct mouse, finger, and Apple Pencil-like dragging.
- Playback stopping at the final recorded action.
- Goalie number display.
- Pinch zoom and pan on the rink.
- Enlarged timeline-playhead acquisition for Pencil input.
- Freehand marker, smart held-shape correction, straight/curved arrows, open/closed arrowheads, and solid/dashed/dotted lines.
- Apple Pencil-like double-tap switching between Marker and Eraser.
- Full Ice and camera-based Left/Right Half Ice views with permanent world coordinates.
- Play Options, independent Puck Routes, Copy & Reuse, Undo/Redo, responsive benches, and the left Board Setup drawer.

Storage and compatibility
-------------------------
Version 6.5 uses these browser-storage keys:

  botdHockeyCoachingAid.session.v6_5
  botdHockeyCoachingAid.playbook.v6_5

Version 6.4 session and playbook keys are included as the first migration fallback. Earlier migration fallbacks retained by Version 6.4 remain available.

GitHub Pages installation
-------------------------
The release ZIP contains exactly four root files:

  index.html
  README.txt
  Preview.png
  .nojekyll

To publish:
1. Extract the ZIP.
2. Place all four files directly in the repository root or selected GitHub Pages publishing folder.
3. Commit and push the files.
4. Open the configured GitHub Pages URL after deployment finishes.

The application is self-contained in index.html. It does not require a build step, package manager, external JavaScript library, or application server.

Validation performed
--------------------
- Full inline JavaScript syntax validation with Node.js.
- Duplicate DOM ID inspection.
- Steady player Glow while the player was moving during real requestAnimationFrame playback.
- Timeline-driven player Blink on/off phases while moving.
- Timeline-driven puck Blink while the puck was in flight.
- Paused Glow/Blink inspection behavior.
- Pass and Shot action-block start, arrival, duration, and pixel-width checks.
- Removal of the legacy visible travel underlines.
- Selection of the expanded full-duration puck action block.
- Live action-block resizing while the Travel Time slider was dragged.
- Telestration row absent in Static mode, present when enabled, and hidden again when disabled.
- Static artwork retention while the timed Telestration track was hidden.
- Version 6.4 state normalization and explicit browser-storage fallback checks.
- Version 6.4 regressions for goalie numbers, content-aware playback stopping, mouse and Pencil-like shot aiming, board/net ricochets, and Pencil marker/eraser switching.
- Runtime and browser-console error checks.
- Responsive layout and page-overflow checks at 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- ZIP compressed-data integrity and exact four-file root structure.

Physical iPad and Apple Pencil hardware were not available for release validation. Pencil-like pointer input, touch-sized controls, moving Glow/Blink states, and responsive layouts were exercised through Chromium emulation.

Version history
---------------
6.5  Playback-safe timeline Glow/Blink; full-duration rounded Pass and Shot clips; hidden Telestration row in Static mode.
6.4  Goalie numbers; playback ending at the final action; live red/gray shot projection; mouse click-to-lock aiming; board/net ricochets; and Pencil marker/eraser double-tap switching.
6.3  Timeline-based Glow/Blink intervals; optional recorded Telestration playback; DRAW and ERASE timeline actions; and editable Display Time.
6.2  Reliable direct-drag timeline sliders for mouse, finger, and Pencil; larger slider hit areas; stable contextual editor during drag; and uniform floating action geometry.
6.1  Timeline speed controls, separate shot power/travel time, revised shot aiming, smoother puck motion, pinch zoom, Glow/Blink controls, improved Pencil scrubbing, expanded smart marker tools, and BEWARE OF THE DAWG artwork.
6.0  Rink-first floating player/puck actions, Inspector removal, unified Pass targeting, two-stage Shot workflow, deterministic board-following shots, and clean New board.
5.10 On-rink Full/Half Ice badge, Half Ice end pill, simplified Settings, and centered goalie badge.
5.9  Canonical Full Ice world with rotated/cropped Half Ice cameras and exact view-invariant play geometry.
5.8  Initial Full/Half Ice route orientation and Half Ice off-side work.
5.7  Permanent playback transport, marker preview, timeline player focus, animated targeting, and independent puck-route selection.
5.6  Tap-to-set possession, compact Inspector sections, revised puck art, and pass/shot route styling.
5.5  Two ordered team benches, simplified top toolbar, corrected Move from playhead, and one timeline toggle.
5.4  Independent player rerouting and clean New board.
5.3  Frame-accurate player-action revision workflow.
5.2  Restored classic tokens, canonical deployment, collapsible timeline, non-overlapping clips, and Copy & Reuse.
