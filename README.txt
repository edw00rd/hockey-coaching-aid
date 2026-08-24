BOTD Hockey Coaching Aid v6.3
Creator: Nicholas Heller

Release focus
-------------
Version 6.3 turns presentation effects into real timeline actions.

Glow and Blink are no longer permanent object switches. A coach can turn Glow on at one playhead position and turn it off later, creating an editable interval on that player or puck timeline. Telestration can now remain a normal static coaching-board overlay or, when Timeline Telestration is enabled, record marker drawing and erasing as timed actions that replay with the play.

What's new in v6.3
------------------
1. Timeline-based Glow and Blink intervals
   - Select a player row, movement clip, puck row, or puck event to use the existing Glow controls in the timeline toolbar.
   - Turning Glow on marks the current playhead position as the start of the effect.
   - Move the playhead forward and turn Glow off to mark the end.
   - The player or puck glows only inside that interval during playback.
   - Multiple separate Glow/Blink intervals can be created for the same player or puck.
   - Different players and the puck can glow at the same time.
   - Enabling Glow reveals the color selector and Blink checkbox.
   - Enabling Blink reveals the Blink Rate slider.
   - Color, Blink state, and Blink Rate are stored with the timeline interval.

2. Visible Glow/Blink actions in the timeline
   - Each Glow interval appears as a compact GLOW or BLINK clip on its player or puck row.
   - Selecting the clip identifies its player or puck and exposes precise editing controls.
   - Glow Time changes the interval duration.
   - Start changes the interval's timeline position while respecting neighboring Glow clips.
   - Playhead jumps to the interval start.
   - Delete removes only the selected Glow/Blink interval.
   - Glow interval boundaries participate in Previous Action and Next Action navigation.

3. Optional Telestration playback timeline
   - A TELESTRATION checkbox now appears beside Play Option and Puck Route in the expanded timeline controls.
   - With Telestration disabled, marker artwork behaves as it did previously: the final markup remains visible as a static coaching-board layer.
   - With Telestration enabled, new marker and eraser gestures are recorded at the current playhead position.
   - Drawing duration is based on the time used to make the gesture.
   - The playhead advances to the end of the recorded gesture after completion.
   - The rink replays the mark progressively instead of revealing the completed shape all at once.
   - Eraser gestures are recorded without destructively removing the source stroke, allowing the erase to replay at the correct time.

4. Telestration timeline row
   - Timed marker actions appear as DRAW clips.
   - Timed eraser actions appear as ERASE clips.
   - Overlapping actions are automatically placed in separate lanes so they remain selectable.
   - Existing static strokes that do not have recorded timing remain visible throughout playback.
   - Disabling Telestration playback returns the rink to the final static markup state without deleting the recorded actions.

5. Editable Display Time
   - Select a DRAW or ERASE clip to reveal the Display Time slider in the timeline toolbar.
   - Drag with a mouse, finger, or Apple Pencil using the same direct-manipulation behavior as Skate Time.
   - A shorter Display Time makes the mark or erase appear more quickly.
   - A longer Display Time makes it play more slowly.
   - The Start control moves the action to a different point on the timeline.
   - Playhead and Delete controls are available for the selected action.
   - Telestration action boundaries participate in Previous Action and Next Action navigation.

6. Play options, saving, and migration
   - Glow/Blink intervals and Telestration actions are stored independently inside each Play Option.
   - Copy & Reuse carries intersecting Glow and Telestration actions into the new option.
   - Undo and Redo restore complete Glow and Telestration edits.
   - Browser autosave and saved plays retain all interval timing and marker-action data.
   - Version 6.2 permanent Glow settings migrate to full-length Version 6.3 timeline intervals, preserving the prior appearance.

Using timeline Glow/Blink
-------------------------
1. Expand the timeline.
2. Select the desired player row, movement clip, puck row, or puck event.
3. Move the playhead to the desired effect start.
4. Check Glow.
5. Choose the color and optionally enable Blink and set its rate.
6. Move the playhead to the desired effect end.
7. Uncheck Glow.
8. Select the resulting GLOW or BLINK clip to edit its start or Glow Time.

The switch reflects the current playhead state. It is checked only when the selected player or puck is inside an active Glow/Blink interval.

Using timed Telestration
------------------------
1. Expand the timeline.
2. Enable TELESTRATION.
3. Position the playhead where the markup should begin.
4. Select the Marker tool and draw normally.
5. The gesture becomes a DRAW action in the Telestration row.
6. Select the Eraser and erase a visible stroke to create an ERASE action.
7. Select either action and drag Display Time to tune its playback speed.
8. Press Play to watch the marks and erasures occur with the players and puck.

Turning TELESTRATION off does not delete the actions. It displays the final markup as a static coaching-board overlay. Turning it back on restores timed playback.

Core systems retained
---------------------
- Blank New board with one puck at center ice and two complete ordered benches.
- Inspector-free floating Player and Puck controls.
- Mid-playhead player rerouting that preserves the past and replaces only the selected player's future.
- Passes to players or open ice.
- Two-stage shot aiming, editable Shot Power, and editable puck Travel Time.
- Eased puck movement and deterministic board-following shot paths.
- Direct-drag Skate Time, Travel Time, Shot Power, Glow Time, and Display Time controls.
- Pinch zoom and pan on the rink.
- Enlarged Apple Pencil playhead acquisition.
- Freehand marker, straight and curved arrows, open and closed arrowheads, solid/dashed/dotted lines, and held-shape correction.
- Full Ice and camera-based Left/Right Half Ice views with permanent world coordinates.
- Play Options, independent Puck Routes, Copy & Reuse, Undo/Redo, responsive benches, and the left Board Setup drawer.

Storage and compatibility
-------------------------
Version 6.3 uses these browser-storage keys:

  botdHockeyCoachingAid.session.v6_3
  botdHockeyCoachingAid.playbook.v6_3

Version 6.2 session and playbook data migrate automatically on first load. Earlier migration fallbacks retained by Version 6.2 remain available.

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
- Glow on/off creation at exact playhead positions.
- Separate player and puck Glow intervals.
- Static Glow, Blink, color, and Blink Rate playback behavior.
- Direct mouse dragging of Glow Time and Display Time.
- Immediate reveal/hide of dependent Glow controls.
- Player/puck timeline clip rendering and selection.
- Actual pointer-drawn Telestration recording.
- Progressive drawing playback before, during, and after the action.
- Actual pointer-erased Telestration recording and timed disappearance.
- Static final-markup behavior when Telestration playback is disabled.
- Telestration DRAW/ERASE lane assignment and action selection.
- Undo/Redo restoration for Glow and Telestration actions.
- Play Option switching and Copy & Reuse preservation.
- Browser autosave and reload persistence.
- Version 6.2 permanent-Glow migration to Version 6.3 timeline clips.
- No page-level horizontal overflow at 1920 x 1080, 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- No uncaught runtime exceptions or browser-console errors in the release tests.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, touch-sized controls, Pencil-like pointer events, timeline slider dragging, marker drawing, and erasing were exercised through Chromium emulation.

Version history
---------------
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
