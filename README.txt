BOTD Hockey Coaching Aid v6.4
Creator: Nicholas Heller

Release focus
-------------
Version 6.4 improves playback finishing behavior, shot aiming and ricochet physics, goalie-number display, and Apple Pencil marker/eraser switching.

The shot workflow now gives the coach a complete projected result before the shot is committed. With a mouse, aiming follows hover and locks on click. With a Pencil or finger, aiming follows the contact point while it is held and locks on release. The portion from the puck to the active aiming point is red; the remaining projected travel is light gray. After aim lock, the complete red-and-black shot route remains fixed while Shot Power is adjusted.

What's new in v6.4
------------------
1. Goalie numbers on the ice
   - Goalies now display their roster number whenever Numbers is enabled under Token Display.
   - The number is centered inside the goalie body and remains visible in Full Ice and both Half Ice camera views.
   - The existing circular G role badge remains separate and centered.

2. Playback stops at the actual end of the play
   - Play now stops at the end of the latest recorded action instead of continuing through unused timeline space.
   - The end calculation includes:
       * Player movement clips
       * Pass and shot arrival times
       * Possession and puck-placement events
       * Glow/Blink intervals
       * Timed DRAW and ERASE actions
   - The timeline may still be longer than the play for editing room, but playback no longer waits for that unused time.
   - Pressing Play while already at the final action restarts playback from time zero.

3. Live two-part shot projection
   Apple Pencil or finger:
   - Press on the rink and drag to aim.
   - Before lifting, the line from the puck to the contact point is red.
   - The predicted travel beyond that point is shown in light gray, including board or net interactions.
   - Lift to lock the aim and reveal Shot Power controls.

   Mouse or trackpad:
   - Move the pointer over the rink to preview the shot continuously.
   - The line to the pointer is red and the projected travel beyond it is light gray.
   - Click the desired aim point to lock the shot and reveal Shot Power controls.
   - After the click, ordinary mouse movement cannot retarget the shot while the power control is being adjusted.

   After aim lock:
   - The full projected route uses the established thin red-and-black animated treatment.
   - Re-aim remains available from the power card.
   - Cancel discards the unfinished shot without changing the puck timeline.

4. Board and net ricochets
   - Direct shots into the boards now reflect back onto the ice.
   - Shallow-angle impacts retain the useful wall-following/rim behavior.
   - Shots can ricochet from the back and side surfaces of either net.
   - Net contacts absorb more energy than board contacts.
   - Remaining shot energy decreases after every contact.
   - Rounded corners continue to produce smooth, deterministic paths.
   - The projected path is calculated before commitment, so the coach sees the expected ricochet while aiming and while changing Shot Power.
   - Saved shots replay along the same deterministic route every time.

5. Apple Pencil marker/eraser switching
   - While Marker or Eraser is active, two quick Pencil taps at approximately the same rink location switch between the two tools.
   - The first tap is rolled back when it becomes part of the double-tap gesture, preventing an accidental dot or erase mark.
   - A pen eraser/barrel-button pointer event also switches tools when the browser exposes one.
   - Mouse and finger drawing behavior is unchanged.

   Browser note:
   Standard web pages do not receive a dedicated Apple Pencil hardware barrel-double-tap event on every iPad/browser combination. Version 6.4 therefore recognizes a quick two-tap Pencil gesture on the rink and also listens for a pen eraser-button event when one is supplied by the browser.

Using the revised Shot workflow
-------------------------------
1. Select the puck.
2. Select Shoot.
3. Aim:
   - Mouse: hover to preview, then click to lock.
   - Pencil/finger: press and drag to preview, then lift to lock.
4. Review the red live segment and light-gray projected continuation.
5. After aim lock, adjust Shot Power.
6. Review any board-follow, board bounce, or net bounce shown by the complete red-and-black route.
7. Select Shoot to commit, Re-aim to choose another direction, or Cancel to discard the action.

Core systems retained
---------------------
- Blank New board with one puck at center ice and two complete ordered benches.
- Inspector-free floating Player and Puck controls.
- Mid-playhead player rerouting that preserves the past and replaces only the selected player's future.
- Passes to players or open ice.
- Editable Skate Time, pass/shot Travel Time, and Shot Power.
- Timeline-based Glow/Blink intervals.
- Optional timed Telestration playback with DRAW and ERASE actions.
- Direct-drag timeline controls for mouse, finger, and Pencil-like pointer input.
- Pinch zoom and pan on the rink.
- Enlarged Apple Pencil playhead acquisition.
- Freehand marker, straight and curved arrows, open and closed arrowheads, solid/dashed/dotted lines, and held-shape correction.
- Full Ice and camera-based Left/Right Half Ice views with permanent world coordinates.
- Play Options, independent Puck Routes, Copy & Reuse, Undo/Redo, responsive benches, and the left Board Setup drawer.

Storage and compatibility
-------------------------
Version 6.4 uses these browser-storage keys:

  botdHockeyCoachingAid.session.v6_4
  botdHockeyCoachingAid.playbook.v6_4

Version 6.3 session and playbook data migrate automatically on first load. Earlier migration fallbacks retained by Version 6.3 remain available.

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
- Goalie number rendering in Full Ice and Half Ice.
- Content-end calculation for player movement, puck travel, Glow/Blink, and Telestration actions.
- Real-time playback stop at a sub-second final action while the timeline remained 12 seconds long.
- Mouse hover shot preview, click-to-lock, and protection from accidental retargeting while changing power.
- Pencil-like contact/drag preview before pointer release and aim lock on release.
- Goal-path preservation.
- Direct board ricochets, shallow wall-following paths, rounded corners, and net-back/net-side contacts.
- Four hundred randomized shot-path checks for finite coordinates and rink containment.
- Shot-event playback using the saved aim vector and revised physics path.
- Pencil-like double-tap switching with rollback of the first tap mark.
- Duplicate DOM ID, uncaught runtime exception, and browser-console error checks.
- Responsive layout and page-overflow checks at 1366 x 1024, 1024 x 768, 820 x 1180, and 390 x 844.
- ZIP compressed-data integrity and exact four-file root structure.

Physical iPad and Apple Pencil hardware were not available for release validation. Pencil-like pointer events, touch-sized controls, contact-drag aiming, pointer release, and double-tap timing were exercised through Chromium emulation.

Version history
---------------
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
