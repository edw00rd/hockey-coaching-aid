BOTD Hockey Coaching Aid v6.6
Creator: Nicholas Heller

Release focus
-------------
Version 6.6 corrects the natural playback stopping point, installs the supplied BOTD dog tag and BEWARE OF THE DAWG sign as the built-in artwork, and establishes the requested Token Display defaults for new sessions.

What's new in v6.6
------------------
1. Glow and Blink no longer extend playback
   - Playback stops at the end of the last real play action even when a Glow or Blink interval continues farther down the timeline.
   - Player movement clips, puck events, pass/shot arrival times, and enabled timed Telestration actions still determine the natural stopping point.
   - A long Glow/Blink interval can remain available for editing, but it does not force the play to run through unused timeline time.
   - Static Telestration does not extend playback. Timed Telestration counts only while its timeline playback feature is enabled.
   - Pressing Play while the playhead is already at the natural end restarts the play from zero, as before.

2. New default playbook artwork
   - The supplied metallic B.O.T.D. dog tag is now the default playbook logo.
   - The application header uses the same playbook artwork.
   - Uploading a custom playbook logo continues to replace the default and is reflected in the header.
   - Existing saved custom playbook logos are preserved during migration.

3. New default center-ice artwork
   - The supplied BEWARE OF THE DAWG sign is now the built-in center-ice logo.
   - It is used in Full Ice and in both camera-based Half Ice views.
   - Existing saved custom center-ice artwork remains unchanged.
   - Use the existing Center-Ice Logo controls to upload another image, change opacity, or restore the BOTD default.

4. Requested Token Display defaults
   New sessions and newly initialized boards use:

     Names          Off
     Numbers        Off
     Positions      On
     Leadership     Off
     Offside light  On

   Existing users' explicitly saved Token Display preferences are preserved when upgrading from Version 6.5.

Core systems retained
---------------------
- Blank New board with one puck at center ice and two complete ordered benches.
- Inspector-free floating Player and Puck controls.
- Player Move editing from the exact playhead position.
- Passes to players or open ice.
- Shot aiming, editable Shot Power, editable Travel Time, wall-following paths, and board/net ricochets.
- Editable Skate Time with direct mouse, finger, and Apple Pencil-like dragging.
- Timeline-based Glow/Blink intervals.
- Optional timed Telestration with DRAW/ERASE clips and Display Time editing.
- Pinch zoom and pan on the rink.
- Enlarged timeline-playhead acquisition for Pencil input.
- Freehand marker, held-shape correction, arrows, and solid/dashed/dotted lines.
- Apple Pencil-like double-tap switching between Marker and Eraser.
- Full Ice and camera-based Left/Right Half Ice views with permanent world coordinates.
- Play Options, independent Puck Routes, Copy & Reuse, Undo/Redo, responsive benches, and the left Board Setup drawer.

Storage and compatibility
-------------------------
Version 6.6 uses these browser-storage keys:

  botdHockeyCoachingAid.session.v6_6
  botdHockeyCoachingAid.playbook.v6_6

Version 6.5 session and playbook keys are the first migration fallback. The earlier fallbacks retained by Version 6.5 remain available.

The migration updates the standard playbook name from "BOTD Playbook v6.5" to "BOTD Playbook v6.6" while preserving play geometry, rosters, teams, movement, puck routes, drawings, Glow/Blink intervals, timed Telestration, custom artwork, and saved display preferences.

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
- Version, title, and visible subtitle checks.
- Exact default Token Display state checks.
- Embedded dog-tag and center-logo data decoding.
- Header, playbook-panel, Full Ice, and Half Ice artwork synchronization.
- Playback-end calculation with a movement ending at 1.4 seconds and a Glow/Blink interval continuing to 12 seconds.
- Actual requestAnimationFrame playback stopping at 1.4 seconds in that scenario.
- Timed Telestration included only while enabled.
- Version 6.5 state normalization and preservation of explicit display preferences.
- Glow/Blink during moving player and puck playback.
- Full-duration Pass and Shot timeline blocks.
- Live Travel Time resizing.
- Conditional Telestration-track visibility.
- Responsive-layout checks at 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Browser runtime, console-error, and page-overflow checks.

Physical iPad and Apple Pencil hardware were not available for this release validation. Existing Pencil-oriented interaction code remains unchanged from the previously tested Version 6.5 behavior.
