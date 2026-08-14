BOTD Hockey Coaching Aid v5.8
Creator: Nicholas Heller

Release focus
-------------
Version 5.8 makes Full Ice and Half Ice two reversible orientations of the same play. Switching views now reorients the complete spatial state instead of merely changing the rink background or squeezing coordinates into a different frame. Recorded player movement, starting positions, puck locations and targets, every puck route in every play option, and telestration all remain aligned.

The release also adds a practical Half Ice off-side indicator and removes the route-editing UI that was obstructing the rink. The selected-player Move context now appears in the timeline header, where it identifies the timeline action without occupying the main drawing toolbar.

What's new in v5.8
------------------
1. Reversible Full Ice / Half Ice orientation
   - A rightward Full Ice route becomes an upward Half Ice route.
   - Vertical lane separation on Full Ice becomes horizontal lane separation on Half Ice.
   - The transformation applies to:
     * Every on-ice player, goalie, coach, and manager
     * Every recorded player-movement point
     * Puck starting position
     * Puck-event source and target coordinates
     * Every puck route attached to every play option
     * Telestration strokes
   - All play options are converted together, preventing Option 1 and Option 2 from silently using incompatible rink coordinate systems.
   - Switching back to Full Ice applies the inverse transformation. Routes and object positions survive a Full -> Half -> Full round trip without teleporting or being rebuilt from their starting frames.
   - The view switch is one Undo/Redo transaction.
   - Any active route trace, puck target mode, setup drag, or drawing gesture is safely canceled before the coordinate system changes.

2. Half Ice puck-side orientation
   - Half Ice uses an upward attacking orientation.
   - A left-handed player's carried puck is placed on the upper-left side of the token.
   - A right-handed player's carried puck is placed on the upper-right side.
   - The offset follows the player throughout playback and after route edits.

3. Half Ice goalie and staff orientation
   - Goalie, head-coach, and manager pieces rotate with the rink orientation.
   - Goalie pad stripes become horizontal in Half Ice rather than retaining their Full Ice vertical treatment.
   - Coach and manager center stripes rotate with their rectangular pieces.
   - Role-badge lettering remains upright and readable.
   - Circular skater pieces remain circular and do not receive an unnecessary shape rotation.

4. Practical Half Ice off-side indicator
   - Half Ice now evaluates the blue line instead of always reporting onside.
   - The attacking-zone edge of the visible blue line is used as the determining boundary.
   - The puck is considered in the zone only after the complete puck footprint has crossed that edge.
   - An attacker is considered completely across only after the rear edge of the app's two-skate footprint proxy has cleared the line.
   - An attacker whose rear-skate proxy remains on or above the blue-line plane remains onside.
   - The controlled puck carrier does not create an off-side call against themself when possession began before entry.
   - The attacking team remains associated with a pass, shot, or loose-puck flight after release.
   - An early attacker produces a warning; a complete puck entry with an uncleared attacker produces the violation state.
   - Returning all early attackers to the blue line clears the pending state before re-entry.
   - Full Ice off-side behavior remains active for both attack directions.

   This is an instructional coaching-board approximation. The app does not animate individual skates, raised skates, body contact, pressure on a defender, or every video-review exception, so the light is not intended to replace an official's judgment.

5. Unobstructed route tracing
   - Removed the large MOVE FROM banner that covered the top of the rink during route replacement.
   - Removed the dashed blue action-anchor circle and its screen-sweeping animation.
   - The selected player's exact start position is still preserved internally at the playhead splice.
   - The existing selected-player yellow timeline-focus ring remains available when a movement clip is selected.
   - Escape cancels an active trace without changing the timeline.

6. Timeline header cleanup
   - Moved the selected-player Move context pill from the main bottom toolbar to the top of the expanded timeline.
   - The pill continues to show the selected player and exact playhead time when space permits.
   - Removed the redundant collapse button beside Timeline Length.
   - The blue chevron in the main toolbar is now the single control for showing or hiding the timeline.

Off-side indicator states
-------------------------
Green  - Onside, no attacker is fully across ahead of the puck.
Orange - An attacker is fully across while the puck has not completed entry; the player must clear or the entry must be corrected.
Red    - The puck has completely entered while an uncleared attacker remains fully across.

Systems retained
----------------
- Exact selected-player route replacement from any playhead frame.
- Preservation of the selected player's route before the splice point.
- Independent player movement tracks with no overlapping clips on the same track.
- Always-available playback controls while the timeline is minimized.
- Previous/next global action navigation and player-specific clip navigation.
- Yellow player focus ring for a selected timeline clip.
- Animated target acquisition for pass and possession selection.
- Independent PLAY OPTION and PUCK ROUTE selection.
- Copy & Reuse play variations.
- Clean New board with every piece returned to the two team benches.
- Two ordered team benches and the collapsible Team Benches drawer.
- Classic skater, goalie, coach, manager, and bench-card designs.
- Set possession by tapping a player on the ice.
- Compact Pass Defaults, Shot Defaults, and Highlight disclosures.
- Flat puck silhouette, black dashed pass routes, and animated red-and-black shot routes.
- Return to bench in the player identity header.
- Context-aware Move After Current Path control.
- Puck-route replacement from the playhead.
- Collapsible side drawers, themes, languages, highlighting, playbook storage, and JSON transfer.
- Storage fallback from Versions 5.7, 5.6, 5.5, 5.4, 5.3, 5.2, 5.1, and 5.0.

Validation performed
--------------------
- JavaScript syntax validation with Node.js.
- Chromium initialization and runtime-error checks.
- 51 focused browser assertions covering the Version 5.8 geometry, off-side, UI, migration, and responsive changes.
- Verified Full Ice horizontal movement becomes Half Ice vertical movement.
- Verified two independent play options, all puck routes, puck source/target coordinates, and telestration transform together.
- Verified Full -> Half -> Full coordinate round trips preserve route geometry.
- Verified one Undo restores the pre-switch orientation and one Redo reapplies the transformed orientation.
- Verified goalie, coach, and manager pieces rotate while skater circles remain unchanged.
- Verified left-handed upper-left and right-handed upper-right puck-carry positions in Half Ice.
- Verified Half Ice early-entry warning, complete puck-entry violation, rear-skate blue-line-plane case, controlled-carrier case, tag-up clearing, and loose-puck dump/shot entry.
- Verified Full Ice off-side operation remains active after the new model is installed.
- Verified the MOVE FROM overlay and dashed blue action anchor do not render while tracing.
- Verified the Move context is located in the timeline header.
- Verified the redundant timeline-header collapse control is absent and the remaining toolbar chevron opens and closes the timeline.
- Verified Version 5.7 state normalizes into Version 5.8 without losing movement data and that Version 5.7 storage fallback keys are registered.
- Verified no duplicate DOM IDs, no uncaught runtime exceptions, and no browser error log entries.
- Responsive checks at 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Release preview generated at 1920 x 1080.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, touch-sized controls, pointer interactions, and responsive behavior were exercised through Chromium emulation.

Version history
---------------
5.8 - Reversible Full/Half Ice play orientation, Half Ice puck-side and staff/goalie orientation, practical Half Ice off-side logic, unobstructed route tracing, timeline-header Move context, and one timeline toggle.
5.7 - Always-available toolbar playback, circle-on-circle marker preview, timeline-selected player focus ring, animated target acquisition, and independent puck-route selection per play option.
5.6 - Tap-to-set possession, compact Inspector disclosures, revised puck silhouette, dashed pass notation, animated red-and-black shot notation, top-positioned Return to bench, and context-aware Move After Current Path.
5.5 - Two ordered team benches, bench drawer, simplified top toolbar, exact selected-player future-route replacement, route-only Move controls, and one timeline toggle.
5.4 - GPS-style player route replacement from the playhead, clean New board, and experimental category benches.
5.3 - Frame-accurate action revision workflow and action notation.
5.2 - Restored classic pieces and benches, canonical loading, safe non-overlapping timeline editing, and Copy & Reuse variations.
5.1 - Previous GitHub Pages baseline supplied for the Version 5.2 rebuild.

GitHub Pages deployment
-----------------------
Place these four files directly in the repository root:

index.html
README.txt
Preview.png
.nojekyll
