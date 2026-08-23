BOTD Hockey Coaching Aid v6.1
Creator: Nicholas Heller

Release focus
-------------
Version 6.1 builds on the rink-first Version 6.0 interface. It adds timeline-based speed editing for skaters and the puck, a cleaner shot workflow, softer on-ice puck motion, pinch zoom, timeline Glow/Blink controls, improved Apple Pencil scrubbing, and a substantially expanded marker system.

The two ordered team benches, left Board Setup drawer, temporary floating rink controls, permanent playback toolbar, expandable timeline, play options, puck routes, Full Ice/Half Ice camera model, and off-side aid remain in place.

What's new in v6.1
------------------
1. Timeline action-time and speed editing
   - Select a player's movement clip in the timeline to reveal a Skate Time slider in the timeline header.
   - The slider changes how long that player takes to complete the selected route and therefore changes skating speed without changing route geometry.
   - A live speed readout is shown beside the slider.
   - A newly traced route still uses the time taken to trace it as its baseline duration.
   - The original trace-time baseline remains stored even after the clip duration is edited.
   - Start time, Move from playhead, Continue, Glow, and Delete remain available in the same contextual timeline toolbar.

2. Pass and shot travel-time editing
   - Select a pass or shot event in the puck row to reveal a Travel Time slider.
   - Travel Time changes how quickly the puck follows the recorded route without moving the route's target.
   - A live puck-speed readout is shown beside the slider.
   - Shot Power remains an independent control. Power determines projected shot travel and board-following distance; Travel Time determines how quickly the puck completes that route.
   - Pass and shot timing is constrained so an edited event does not overlap the next puck event.

3. Cleaner floating player controls
   - The floating player actions remain limited to Move and Bench.
   - Return to bench has been shortened to Bench.
   - Bench is red so its destructive/removal purpose is clear.
   - The black panel behind the floating controls has been removed. Only the two individual action pills and the animated selection ring remain visible.

4. Revised shot workflow
   - Shoot now opens a quiet, thin dashed aim guide rather than the previous large, heavy arrow.
   - Aim by tapping or dragging to the intended target.
   - After aiming, a compact card appears near the puck with Power, Re-aim, Cancel, and Shoot controls.
   - Re-aim returns directly to target selection without discarding the shot setup.
   - Committing the shot removes all temporary controls.
   - The timeline can later edit the shot's power and travel time independently.

5. More natural puck motion on ice
   - Passes and shots now use eased progression instead of mechanically moving at an identical visual rate through every frame.
   - Shots decelerate as they travel.
   - High-power shots that reach the boards follow a denser rounded-rink perimeter path.
   - Impact angle affects how much remaining travel continues along the wall.
   - Board travel remains deterministic so a saved play replays the same way every time.
   - This is a coaching-diagram motion model, not a full physical collision simulation.

6. Pinch-to-zoom rink camera
   - Pinch with two fingers to zoom in and out around the gesture midpoint.
   - Continue moving both fingers to pan while zoomed.
   - Ctrl/Command + mouse wheel provides the equivalent desktop zoom control.
   - A Reset zoom control appears only while the rink is zoomed or panned.
   - Switching between Full Ice and Half Ice, choosing another Half Ice end, or starting New resets the zoom while preserving all world positions and paths.

7. Timeline Glow and Blink controls
   - Select a player movement clip or a player row in the timeline and enable Glow.
   - Enabling Glow reveals a color selector and a Blink checkbox.
   - Enabling Blink reveals a Blink Rate slider.
   - The same controls are available for the puck when a puck event or puck row is selected.
   - Glow and Blink are display effects only; they do not change routes, timing, possession, or event order.

8. Improved Apple Pencil timeline scrubbing
   - The visible yellow playhead arrow remains compact, but its invisible grab target is substantially larger.
   - Pencil and touch input may begin slightly beside the visible arrow and still acquire it.
   - Coalesced pointer samples are used when available for smoother movement.
   - This makes back-and-forth playhead navigation easier without making the timeline visually heavier.

9. Expanded marker and telestration tools
   - The marker selector still uses a color circle with a smaller width indicator.
   - The width indicator is now offset to the lower-right of the color circle.
   - Line patterns: Solid, Dashed, and Dotted.
   - Drawing tools: Freehand, Straight Arrow, and Curved Arrow.
   - Arrow endings: Open and Closed.
   - With Freehand selected, draw a square, rectangle, triangle, circle, or X and hold the Pencil still at the end of the stroke. The app snaps a recognized gesture into a clean geometric shape.
   - Shape recognition uses the recorded stroke itself and may leave ambiguous gestures as freehand rather than forcing an incorrect shape.
   - Undo restores the previous drawing state.

10. Updated default artwork
   - The built-in header and center-ice artwork now reads BEWARE OF THE DAWG.
   - Existing plays that use custom artwork remain unchanged.

Core Version 6.0 interaction model retained
-------------------------------------------
- Selecting a player on the rink reveals temporary Move and Bench controls beside that player.
- Selecting Move begins a route at the player's exact current playhead position.
- Movement before the playhead is preserved; only that player's future movement is replaced.
- Selecting the puck reveals temporary Pass and Shoot controls.
- Pass may target either a player or open ice.
- A player-directed pass transfers possession on arrival.
- An open-ice pass leaves the puck loose at its destination.
- A short pass beside or behind the carrier provides drop-pass behavior without a separate Drop command.
- Temporary rink controls disappear when an action begins, playback resumes, the playhead changes, blank ice is selected, or the action is completed.
- Exact clip and puck-event editing remains in the timeline header; no permanent right Inspector is used.

New-play workflow
-----------------
1. Select New.
2. A blank Full Ice surface opens with one puck at center ice and no deployed personnel.
3. Select the desired player, goalie, and staff cards from either team bench.
4. Hide the benches when the lineup is ready.
5. Select a player and choose Move to trace that player's first route.
6. Select the puck and choose Pass or Shoot.
7. Expand the timeline for precise action timing, speed, Glow/Blink, play-option, or puck-route editing.

Editing movement speed
----------------------
1. Expand the timeline.
2. Select a movement clip in a player's row.
3. Use Skate Time to make the action faster or slower.
4. The route remains unchanged; only its duration and calculated speed change.
5. Use Move from the displayed playhead time to replace that player's future route, or Continue to add movement after the selected clip.

Editing a pass or shot
----------------------
1. Select the pass or shot event in the puck row.
2. Use Travel Time to change puck speed along that event's route.
3. For a shot, use Power to change projected travel and board-following distance.
4. Use the event-time control to reposition the event when needed.
5. Use Edit/Retarget to choose a different destination, or Delete to remove the event.

Marker gesture guidance
-----------------------
- Use one continuous stroke.
- Finish near the beginning point for closed shapes.
- Hold the Pencil still briefly at the end of the stroke to request correction.
- For an X, cross through the center and complete both diagonals in one stroke.
- Freehand remains available when no supported shape is confidently recognized.

Touch, Pencil, and keyboard notes
---------------------------------
- Touch targets are sized for tablet use.
- Pinch gestures operate on the rink only and do not rewrite play coordinates.
- Escape cancels an unfinished Move, Pass, Shot, or drawing operation.
- Space toggles playback when focus is not in an input field.
- Arrow-key and existing transport controls remain available for timeline navigation.
- Reduced-motion mode retains all controls and route distinctions while suppressing nonessential animation.

Storage and compatibility
-------------------------
- Version 6.1 uses these browser-storage keys:
  botdHockeyCoachingAid.session.v6_1
  botdHockeyCoachingAid.playbook.v6_1
- Version 6.0 session and playbook data migrate automatically on first load.
- Existing movement clips receive a baseline duration equal to their saved duration when no older trace-time baseline exists.
- Existing puck events without an explicit travel duration continue to use their prior calculated timing until edited.
- Existing player and puck data receive disabled Glow defaults, preserving the prior appearance.
- Earlier migration fallbacks retained by Version 6.0 remain available.

GitHub Pages installation
-------------------------
The release ZIP contains exactly four root files:

  index.html
  README.txt
  Preview.png
  .nojekyll

To publish:
1. Extract the ZIP.
2. Place all four files directly in the repository root or the selected GitHub Pages publishing folder.
3. Commit and push the files.
4. Open the configured GitHub Pages URL after deployment finishes.

The application is self-contained in index.html and does not require a build step, package manager, external JavaScript library, or application server.

Validation performed
--------------------
- JavaScript syntax validation with Node.js.
- 81 automated Chromium release assertions.
- Player movement duration editing and trace-baseline preservation.
- Pass and shot travel-time editing.
- Independent shot power and travel-time behavior.
- Smoothed puck interpolation and rounded board-following paths.
- Floating Move/Bench styling and streamlined shot controls.
- Player and puck Glow, Blink, color, and blink-rate state.
- Marker line patterns, arrow modes, open/closed arrowheads, and five supported held-shape recognizers.
- Pen-like held-shape input through browser pointer-event emulation.
- Two-touch pinch zoom, pan, reset, and Full/Half Ice geometry preservation.
- Enlarged Apple Pencil playhead acquisition and pen-like scrubbing through pointer-event emulation.
- Version 6.0 storage migration.
- Responsive checks at 1920 x 1080, 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Duplicate DOM ID, uncaught runtime error, and browser-console error checks.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, touch gestures, Pencil-like pointer events, held-shape timing, and playhead acquisition were exercised through Chromium emulation.

Version history
---------------
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
