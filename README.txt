BOTD Hockey Coaching Aid v6.2
Creator: Nicholas Heller

Release focus
-------------
Version 6.2 is a focused usability release for the contextual timeline sliders and temporary rink controls introduced in Versions 6.0 and 6.1.

The Skate Time control is now a true direct-manipulation slider: press its thumb or track, keep holding, and drag continuously with a mouse, finger, or Apple Pencil. The same interaction improvement applies to Pass/Shot Travel Time and Shot Power. Floating Move, Bench, Pass, Shoot, Cancel, and shot-confirmation controls now share one consistent rounded-rectangle size.

What's new in v6.2
------------------
1. Reliable click-and-drag Skate Time editing
   - Select a player's movement clip in the timeline to reveal Skate Time.
   - Press anywhere on the enlarged slider surface and drag left or right continuously.
   - Mouse, touch, and Apple Pencil input use the same pointer-capture interaction.
   - The slider keeps ownership of the pointer even when the pointer moves outside the visible thumb.
   - Coalesced pointer samples are used when the browser supplies them, improving Pencil and fast-drag smoothness.
   - Duration, time readout, and calculated speed update live throughout the drag.
   - Releasing the pointer commits the final value and browser autosave.
   - Tapping/clicking the track to jump remains supported.
   - Keyboard arrow-key adjustment remains supported when the slider has focus.

2. Stable timeline editor during a drag
   - Version 6.1 could rebuild the contextual timeline editor while playback rendering was updating the rink.
   - That replacement detached the live range control after the first value change, making a drag feel like a single click.
   - Version 6.2 preserves the active editor and slider for the entire pointer or keyboard interaction.
   - Normal timeline rendering resumes after the control releases focus.

3. Larger Pencil- and touch-friendly slider geometry
   - The slider has a 40-pixel-tall interaction surface.
   - The visible track is eight pixels tall.
   - The thumb is larger and uses a strong focus/drag treatment.
   - The control automatically narrows on compact screens while retaining the larger grab surface.

4. Pass, shot, and power controls receive the same drag behavior
   - Pass and shot Travel Time can be dragged continuously.
   - Shot Power can be dragged continuously.
   - Travel Time still changes puck speed without moving the path target.
   - Shot Power remains independent and continues to control projected travel and board-following distance.

5. Uniform floating rink buttons
   - Move, Bench, Pass, and Shoot use exactly the same width, height, corner radius, padding, and text alignment.
   - Temporary Cancel and shot-action buttons use the same footprint as the primary floating actions.
   - Bench remains red but is now a conventional rounded rectangle rather than a circular control.
   - The contextual controls remain border-light and appear without the former black background panel.

Core Version 6.1 systems retained
---------------------------------
- A blank New board with one puck at center ice and two complete ordered benches.
- Temporary player controls beside the selected player: Move and Bench.
- Temporary puck controls beside the puck: Pass and Shoot.
- Mid-playhead player rerouting that preserves the past and replaces only the selected player's future.
- Passes to players or open ice.
- Two-stage shot aiming and independently editable Shot Power and Travel Time.
- Eased puck movement and deterministic board-following shot paths.
- Pinch zoom and pan on the rink.
- Timeline Glow/Blink controls.
- Enlarged Apple Pencil playhead acquisition.
- Smart marker shapes, arrows, solid/dashed/dotted lines, and held-shape correction.
- Full Ice and camera-based Left/Right Half Ice views with permanent world coordinates.
- Play options, independent puck routes, Copy & Reuse, Undo/Redo, responsive benches, and the left Board Setup drawer.

Using Skate Time
----------------
1. Expand the timeline.
2. Select a movement clip in a player's row.
3. Press the Skate Time thumb or any point on its track.
4. Keep the mouse button, Pencil, or finger held down and drag left or right.
5. Release at the desired duration.

A shorter duration makes the player complete the unchanged route more quickly. A longer duration makes the player complete it more slowly. The originally traced time remains the route's baseline metadata.

Using puck timing and power
---------------------------
1. Select a pass or shot event in the puck row.
2. Drag Travel Time to change how quickly the puck follows its existing path.
3. For a shot, drag Power independently to change projected distance and board-following travel.
4. Release the control to commit the value.

Floating-control behavior
-------------------------
- Select a player to see equal-size Move and Bench controls.
- Select the puck to see equal-size Pass and Shoot controls.
- Bench is red and rectangular to distinguish it without changing its footprint.
- Floating actions disappear when an action begins, playback resumes, the playhead changes, blank ice is selected, or the action is completed.

Storage and compatibility
-------------------------
Version 6.2 uses these browser-storage keys:

  botdHockeyCoachingAid.session.v6_2
  botdHockeyCoachingAid.playbook.v6_2

Version 6.1 session and playbook data migrate automatically on first load. The earlier migration fallbacks retained by Version 6.1 remain available.

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
- JavaScript syntax validation with Node.js.
- Continuous mouse dragging of Skate Time with multiple live input updates during one held gesture.
- Apple Pencil-like pointer dragging through pen pointer-event emulation.
- Finger-like dragging through touch pointer-event emulation.
- Pointer capture, pointer release, and cancellation-state cleanup.
- Pass/Shot Travel Time direct dragging.
- Shot Power direct dragging.
- Equal dimensions for Move, Bench, Pass, and Shoot.
- Red Bench styling and non-circular 12-pixel corner radius.
- No page-level horizontal overflow at 1920 x 1080, 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Successful slider dragging at each tested responsive size.
- Version 6.1 session and playbook storage migration into Version 6.2 keys.
- No uncaught runtime exceptions or browser-console errors in the focused release tests.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, touch input, Pencil-like pointer events, continuous drag behavior, and pointer capture were exercised through Chromium emulation.

Version history
---------------
6.2  Reliable direct-drag timeline sliders for mouse, finger, and Pencil; larger slider hit areas; stable contextual editor during drag; and uniform floating action geometry.
6.1  Timeline speed controls, separate shot power/travel time, revised shot aiming, smoother puck motion, pinch zoom, Glow/Blink timeline controls, improved Pencil scrubbing, expanded smart marker tools, and BEWARE OF THE DAWG artwork.
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
