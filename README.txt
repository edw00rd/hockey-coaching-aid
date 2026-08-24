BOTD Hockey Coaching Aid v6.7
Creator: Nicholas Heller

Release focus
-------------
Version 6.7 makes Glow and Blink behave like editable timeline actions. New Glow intervals inherit the duration of the selected hockey action by default, whole-track selections can create a full-timeline Glow interval, and existing Glow/Blink blocks can now be dragged directly to a new time.

What's new in v6.7
------------------
1. Action-sized Glow and Blink defaults
   - Select a player movement action and enable Glow: the new Glow interval begins at that movement's start time and initially lasts for the same duration as its Skate Time.
   - Select a Pass or Shot action and enable Glow: the puck Glow interval begins with that puck action and initially lasts for the same duration as its Travel Time.
   - The Glow Time slider remains available after creation, so the coach can lengthen or shorten the presentation effect independently of the movement, pass, or shot.
   - Glow color, Blink, and Blink Rate remain editable in the existing timeline toolbar.
   - Applying Glow to an action replaces only the overlapping Glow range for that player or the puck. Earlier and later Glow intervals are preserved when possible.

2. Whole-player timeline Glow
   - Select a player's complete track by clicking the player's name at the left of the timeline or by clicking empty space in that player's timeline row.
   - Enabling Glow in that state creates one interval from 0:00.0 through the complete current timeline length.
   - The selected track receives a subtle yellow indicator at the left so it is clear that the whole row—not one movement clip—is being edited.
   - The same full-track selection behavior is also available for the puck row.
   - Turning Glow off while the whole track is selected removes that object's whole-track Glow presentation without changing movement or puck actions.

3. Direct Glow/Blink timeline dragging
   - Glow and Blink blocks now use the same direct timeline interaction model as movement and puck actions.
   - Press anywhere on a Glow/Blink block and drag it left or right with a mouse, finger, or Apple Pencil-like pointer.
   - The interval's duration, color, Blink state, and Blink Rate remain unchanged while it is moved.
   - The playhead and timeline toolbar update continuously during the drag.
   - Dragging is constrained to the current timeline and to the available space between neighboring Glow/Blink intervals for the same player or puck, preventing overlaps.
   - One Undo restores the pre-drag position, and one Redo reapplies the move.

4. Selection-state reliability
   - The timeline toolbar now refreshes immediately when switching between an individual action, a Glow/Blink block, and a whole track.
   - The Glow checkbox and duration description always reflect the currently selected scope rather than retaining the state of the previous selection.
   - The visible application subtitle, browser title, saved-state version, and standard playbook name now consistently report Version 6.7.

Playback behavior retained
--------------------------
Glow and Blink remain presentation effects and do not extend the natural playback endpoint. Playback still stops at the end of the final real hockey action—or at the end of enabled timed Telestration—regardless of a longer Glow/Blink interval.

Core systems retained
---------------------
- Blank New board with one puck at center ice and two complete ordered benches.
- Inspector-free floating Player and Puck controls.
- Player Move editing from the exact playhead position.
- Passes to players or open ice.
- Shot aiming, editable Shot Power, editable Travel Time, wall-following paths, and board/net ricochets.
- Editable Skate Time with direct mouse, finger, and Apple Pencil-like dragging.
- Timeline-based Glow/Blink color, Blink, Blink Rate, and Glow Time controls.
- Optional timed Telestration with DRAW/ERASE clips and Display Time editing.
- Pinch zoom and pan on the rink.
- Enlarged timeline-playhead acquisition for Pencil input.
- Freehand marker, held-shape correction, arrows, and solid/dashed/dotted lines.
- Apple Pencil-like double-tap switching between Marker and Eraser.
- Full Ice and camera-based Left/Right Half Ice views with permanent world coordinates.
- Play Options, independent Puck Routes, Copy & Reuse, Undo/Redo, responsive benches, and the left Board Setup drawer.
- Metallic B.O.T.D. dog-tag playbook artwork and BEWARE OF THE DAWG center-ice artwork.
- Default Token Display settings: Names Off, Numbers Off, Positions On, Leadership Off, and Offside light On.

Storage and compatibility
-------------------------
Version 6.7 uses these browser-storage keys:

  botdHockeyCoachingAid.session.v6_7
  botdHockeyCoachingAid.playbook.v6_7

Version 6.6 session and playbook keys are the first migration fallback. The earlier fallbacks retained by Version 6.6 remain available.

The migration updates the standard playbook name from "BOTD Playbook v6.6" to "BOTD Playbook v6.7" while preserving play geometry, rosters, teams, movement, puck routes, drawings, Glow/Blink intervals, timed Telestration, custom artwork, display preferences, play options, and Undo-compatible timeline data.

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
- Inline JavaScript syntax validation with Node.js.
- Version, browser-title, visible-subtitle, saved-state, and release-ready checks.
- Duplicate DOM ID inspection.
- Action-sized Glow creation from a player movement clip.
- Puck Glow creation using a Pass action's exact Travel Time.
- Full-timeline Glow creation from both a player-name selection and empty player-row space.
- Direct Glow/Blink dragging with mouse input at desktop, tablet, and phone dimensions.
- Apple Pencil-like pen-pointer Glow dragging.
- Finger-like touch-pointer Glow dragging.
- Duration and presentation-property preservation while dragging.
- Neighbor-boundary clamping and non-overlap behavior.
- Live playhead and timeline-context updates during dragging.
- Undo and Redo of a complete Glow-drag operation.
- Continued Glow Time slider editing after action-sized creation.
- Responsive-layout checks at 1920 x 1080, 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Browser runtime, console-error, duplicate-ID, and page-overflow checks.

Physical iPad and Apple Pencil hardware were not available for this release validation. Pen-like pointer events, touch input, pointer capture, and responsive tablet layouts were exercised through Chromium emulation.
