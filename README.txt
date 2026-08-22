BOTD Hockey Coaching Aid v6.0
Creator: Nicholas Heller

Release focus
-------------
Version 6.0 replaces the permanent right-side Inspector with direct, temporary controls on the rink. The workspace stays quiet until the coach selects a player or the puck; only the actions that can be used at that moment appear beside the selected object, and those controls disappear as soon as the next step begins.

The ordered team benches, left Board Setup drawer, permanent drawing/playback toolbar, expandable timeline, Full Ice/Half Ice camera system, play options, and puck routes remain in place.

What's new in v6.0
------------------
1. Inspectorless rink-first workspace
   - The right Inspector drawer has been removed from the visible application.
   - The right-side drawer tab has been removed.
   - No replacement command dock permanently occupies rink width or toolbar space.
   - Tapping blank ice, resuming playback, moving the playhead, or beginning an action dismisses temporary contextual controls.
   - Floating controls remain upright and are clamped inside the visible rink in Full Ice and either Half Ice end.

2. Floating player controls
   - Selecting an on-ice player pauses playback at the exact current frame when necessary.
   - Two controls appear beside that player: Move and Return to bench.
   - Move immediately hides the controls and begins route tracing from the player's exact playhead position.
   - Everything before the playhead remains unchanged.
   - Only the selected player's future movement is replaced.
   - Other player tracks and puck routes remain untouched.
   - The replacement route is stored as a non-overlapping clip and cannot teleport the player at the splice.
   - Return to bench removes the player from the ice, restores the bench card in its ordered location, and remains reversible with Undo.

3. Floating puck controls
   - Selecting the puck reveals only Pass and Shoot.
   - There is no Drop command.
   - The controls disappear immediately after Pass or Shoot is selected.
   - At time zero, the center puck may also be dragged directly onto a player to establish starting possession.

4. One Pass action for players and open ice
   - Pass may target an eligible player or any open-ice point.
   - Passing to a player creates a black dashed pass route and transfers possession on arrival.
   - Passing to open ice sends the puck to that world coordinate and leaves it loose on arrival.
   - A short pass beside or behind the carrier provides the practical drop-pass behavior without a separate Drop control.
   - Existing pass-speed, sauce, and defensive-interception data remain supported.

5. Aim-and-power Shot workflow
   - Shoot opens a temporary aiming interface attached to the puck.
   - The aiming preview uses the animated red-and-black shot treatment.
   - A compact floating slider selects power from 10% through 100%.
   - The preview updates as aim and power change.
   - The shot is committed only when the temporary Shoot confirmation is selected.
   - Cancel or Escape leaves the puck route unchanged.

6. Deterministic board-following shots
   - A shot is never allowed to travel outside the rink boundary.
   - When its projected route reaches the boards, the preview identifies the exact contact point.
   - Remaining travel follows the rink perimeter in the direction implied by the incoming shot.
   - Rounded corners are sampled as part of the same wall path.
   - Remaining travel is reduced after board contact, creating a repeatable coaching-board representation of rims, hard-arounds, and banked shots.
   - This is a deterministic diagram model rather than a full puck-friction or collision physics simulation.

7. Timeline-header precision controls
   - Selecting a movement clip still places the yellow identification ring around its player on the ice.
   - Clip-specific controls now live in the timeline header rather than an Inspector.
   - Available clip tools include Move from the current playhead, Continue after clip, Start, Duration, Preview, and Delete.
   - Puck-event tools include Time, Set playhead, Retarget/Edit shot, and Delete.
   - Direct rink controls and precision timeline controls do not appear at the same time.

8. Clean New workflow
   - New opens a blank Full Ice surface.
   - The puck starts at center ice.
   - No players, goalies, coaches, or managers begin on the ice.
   - Both complete ordered team benches are visible.
   - The timeline begins minimized.
   - Coaches may deploy exactly the personnel they need, then hide the benches without changing the play.

Systems retained
----------------
- Two ordered team benches with the established goalie, line, defense-pair, backup-goalie, and staff sequence.
- Collapsible Team Benches drawer.
- Left Board Setup drawer and its Teams, Roster, Settings, and Playbook tools.
- Always-available drawing, Undo/Redo, playback, speed, route-display, and timeline-toggle controls.
- Independent movement tracks for every player.
- Exact selected-player route replacement from any playhead frame.
- No overlapping movement clips on one player's track.
- Independent PLAY OPTION and PUCK ROUTE combinations.
- Copy & Reuse play variations.
- Black dashed pass routes and animated red-and-black shot routes.
- Animated selection and target-acquisition feedback.
- One permanent Full Ice world coordinate system.
- Rotated and cropped left-end and right-end Half Ice cameras with inverse-camera pointer mapping.
- Shared Full Ice/Half Ice off-side evaluation.
- Classic skater, goalie, coach, manager, puck, and bench-card designs.
- Light and dark themes, languages, token labels, highlighting, center logo, playbook storage, JSON import/export, and full-screen mode.

Compatibility and storage
-------------------------
- Version 6.0 uses these browser-storage keys:
  botdHockeyCoachingAid.session.v6_0
  botdHockeyCoachingAid.playbook.v6_0
- Version 5.10 session and playbook data migrate automatically on first load.
- Earlier migration fallbacks retained by Version 5.10 remain available.
- Existing player geometry, movement clips, play options, puck routes, puck events, drawings, selected camera view, and selected Half Ice end are preserved during migration.
- Previously saved Drop events remain readable for playback compatibility, but Version 6.0 does not present a Drop creation control.

Quick start
-----------
1. Select New for a clean rink, center puck, and two full benches.
2. Select bench cards to place the desired players, goalies, or staff on the ice.
3. Hide the benches when more rink space is desired.
4. Select a player and choose Move, then trace the skating route.
5. Select the puck and choose Pass, then tap a player or an open-ice point.
6. Select the puck and choose Shoot, aim on the ice, set power, and confirm.
7. Use the always-visible playback controls to review the play.
8. Pause at any frame, select a player, and choose Move to replace only that player's future.
9. Expand the timeline for exact clip timing, puck-event editing, alternate play options, and alternate puck routes.

Validation performed
--------------------
- JavaScript syntax validation with Node.js.
- Chromium initialization, console-error, warning, and uncaught-runtime-error checks.
- 30 automated release scenario groups passed across core behavior, real pointer interaction, migration, and regression coverage.
- Verified a clean first load and New with no on-ice personnel, one center puck, complete benches, and a minimized timeline.
- Verified actual bench-card pointer clicks deploy players.
- Verified actual player taps reveal exactly Move and Return to bench.
- Verified actual Move-button selection and pointer tracing commit a replacement route.
- Verified exact mid-clip prefix preservation, no teleport at the splice, no same-track overlap, and no changes to other player tracks.
- Verified actual Return-to-bench selection and one-step Undo restoration.
- Verified actual puck selection reveals exactly Pass and Shoot.
- Verified directed passes transfer possession on arrival.
- Verified open-ice passes end with a loose puck and no visible Drop or Shoot-to-ice legacy control.
- Verified shot aiming, power changes, animated two-layer preview, board contact, perimeter following, and committed-playback path agreement.
- Verified dragging the starting puck onto a player establishes possession.
- Verified timeline clip and puck-event controls operate without opening an Inspector.
- Verified independent play options and puck routes retain pass-to-space and shot events.
- Verified Version 5.10 session and playbook migration.
- Verified Full Ice/Half Ice/Full Ice camera changes preserve world geometry exactly.
- Verified dark-theme and reduced-motion presentation.
- Verified no duplicate DOM IDs.
- Responsive checks at 1920 x 1080, 1024 x 768, 820 x 1180, and 390 x 844.
- Verified no page-level horizontal overflow and that floating controls remain inside the visible rink.
- Release preview generated at 1920 x 1080.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, touch-sized controls, mouse/pointer gestures, route tracing, puck dragging, and responsive behavior were exercised through Chromium emulation.

Version history
---------------
6.0  - Rink-first floating player and puck controls, visible Inspector removal, unified Pass targeting, aim-and-power Shoot, deterministic board-following shots, timeline-header precision editing, and clean center-puck New workflow.
5.10 - On-rink Full/Half Ice badge, compact left/right Half Ice pill, simplified Settings menu, centered goalie G badge, and Version 5.9 storage migration.
5.9  - Canonical Full Ice world, true rotated/cropped left- and right-end Half Ice cameras, exact view-invariant positions and paths, inverse-camera route tracing, shared world-coordinate off-side logic, and Version 5.8 Half Ice recovery.
5.8  - Experimental coordinate-transform Full/Half Ice orientation, practical Half Ice off-side logic, unobstructed route tracing, timeline-header Move context, and one timeline toggle.
5.7  - Always-available toolbar playback, circle-on-circle marker preview, timeline-selected player focus ring, animated target acquisition, and independent puck-route selection per play option.
5.6  - Tap-to-set possession, compact Inspector disclosures, revised puck silhouette, dashed pass notation, animated red-and-black shot notation, top-positioned Return to bench, and context-aware Move After Current Path.
5.5  - Two ordered team benches, bench drawer, simplified top toolbar, exact selected-player future-route replacement, route-only Move controls, and one timeline toggle.
5.4  - GPS-style player route replacement from the playhead, clean New board, and experimental category benches.
5.3  - Frame-accurate action revision workflow and action notation.
5.2  - Restored classic pieces and benches, canonical loading, safe non-overlapping timeline editing, and Copy & Reuse variations.
5.1  - Previous GitHub Pages baseline supplied for the Version 5.2 rebuild.

GitHub Pages deployment
-----------------------
Place these four files directly in the repository root:

index.html
README.txt
Preview.png
.nojekyll
