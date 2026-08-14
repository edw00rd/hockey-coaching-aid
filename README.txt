BOTD Hockey Coaching Aid v5.9
Creator: Nicholas Heller

Release focus
-------------
Version 5.9 replaces the Version 5.8 Full Ice/Half Ice coordinate conversion with a true camera model.

There is now one permanent 1000 x 600 Full Ice coordinate system for the play. Half Ice simply rotates the rink and crops the camera to the selected end. A player, goalie, puck, route waypoint, shot target, or telestration point never receives a different world position merely because the coach changed the view.

This is the same ice turned sideways—not a new half-rink layout and not the entire rink compressed into a smaller frame.

What's new in v5.9
------------------
1. Canonical Full Ice world coordinates
   - All player and staff setup positions are stored in Full Ice coordinates.
   - All recorded player movement points are stored in Full Ice coordinates.
   - All puck starting positions, possession events, pass data, shot targets, and alternate puck routes are stored in Full Ice coordinates.
   - Telestration strokes remain in those same coordinates.
   - Switching views changes only the SVG camera transform and viewport crop.
   - Full -> Half -> Full leaves the complete geometry byte-for-byte unchanged.
   - View changes are presentation controls and do not add an Undo/Redo transaction.

2. Real left-end and right-end Half Ice views
   - Selecting Half Ice shows one actual end of the existing full rink.
   - The visible end is rotated so its attacking direction runs from bottom to top.
   - The opposite goalie and all objects located exclusively on the other half are cropped from view instead of being relocated.
   - The center line remains at the bottom edge of the Half Ice frame, with a small allowance so the complete line paint remains visible.
   - Left End and Right End controls appear under Ice View while Half Ice is active.
   - The controls identify the team whose net is being shown.
   - On entry to Half Ice, the app recommends the end containing the selected timeline clip, selected player, puck, or predominant current action. The coach can switch ends at any time.

3. Exact rink relationships preserved
   - A player behind a blue line in Full Ice remains behind that same physical blue line in Half Ice.
   - Goalies remain in their original nets.
   - Goal lines, blue lines, faceoff circles, center-line paint, routes, and objects all rotate together.
   - A Full Ice route traveling toward the selected end appears bottom-to-top after rotation without its source coordinates being rewritten.
   - The Left End and Right End camera transforms are mathematical inverses of their display mapping.

4. Route tracing in Half Ice
   - Pointer and touch input are mapped through the inverse camera transform.
   - A route traced on the rotated Half Ice display is recorded at the correct location on the same Full Ice surface.
   - Reopening Whole Ice shows that route in its exact physical rink position.
   - Input is constrained to the currently visible half while Half Ice is active.

5. Correct token and puck orientation
   - Goalie, coach, and manager bodies rotate with the rink so their stripe geometry follows the ice orientation.
   - Their role lettering is counter-rotated to remain readable.
   - Circular skater tokens stay visually upright.
   - A right-handed carrier displays the puck on the upper-right side in the attacking Half Ice view.
   - A left-handed carrier displays the puck on the upper-left side.
   - The same handedness behavior works at either end.

6. One off-side model for both views
   - Full Ice and Half Ice now evaluate the same physical attacking blue-line plane in canonical world coordinates.
   - Half Ice no longer substitutes a separate synthetic horizontal boundary.
   - The puck must completely cross the attacking-zone edge of the blue line before it is in the zone.
   - The app's compact two-skate footprint proxy must be completely across before a player is treated as early.
   - The controlled puck carrier exception is retained when possession and control began before entry.
   - An early teammate produces the orange delayed warning.
   - Complete puck entry with an uncleared early teammate produces the red violation state.
   - Tagging up clears the pending state before a later legal entry.
   - Team A/right-end and Team B/left-end entries use mirrored world blue lines and produce the same result in Full and Half Ice.

   This remains a coaching-board approximation. The tokens do not model individually raised skates, body contact, pressure on defenders, every deflection, or every Rule 83 exception, so the indicator is not a replacement for an official or video review.

7. Version 5.8 recovery and compatibility
   - Version 5.8 sessions saved while Half Ice was active are detected during normalization.
   - The old Version 5.8 whole-rink-to-half-rink transform is reversed exactly once so the play returns to its original Full Ice positions.
   - The session may still open in Half Ice, but it now uses the camera model and a selected end.
   - Earlier native Half Ice templates are mapped into the right half of the canonical rink so their net, routes, and shot targets remain usable.
   - Version 5.9 metadata prevents already-canonical plays from being transformed again.
   - Storage fallback remains available for Versions 5.8, 5.7, 5.6, 5.5, 5.4, 5.3, 5.2, 5.1, and 5.0.

Version 5.8 interface cleanup retained
--------------------------------------
- No large MOVE FROM banner over the rink.
- No dashed blue action-anchor circle or screen-sweeping artifact.
- The selected-player Move context remains in the expanded timeline header.
- The blue toolbar chevron remains the single timeline show/hide control.
- Escape cancels an unfinished route trace without altering the timeline.

Other systems retained
----------------------
- Exact selected-player future-route replacement from any playhead frame.
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

Validation performed
--------------------
- JavaScript syntax validation with Node.js.
- Chromium initialization, console-error, and uncaught-runtime-error checks.
- 78 focused browser assertions covering camera geometry, migration, off-side behavior, interaction coordinates, orientation, UI state, and responsive layout.
- Verified that setup positions, recorded movement clips, puck routes, puck events, and drawings are unchanged across Whole -> Right Half -> Left Half -> Whole changes.
- Verified that the right goalie remains at world x 938 and the left goalie remains at world x 62 while only the selected end is visible.
- Verified that a player at world x 620 remains behind the right attacking blue line at world x 670 after the display is rotated.
- Verified center-line, blue-line, and goal-line spacing in the rotated camera.
- Verified actual pointer coordinates map back through both Half Ice camera transforms to the original world point.
- Verified right-handed upper-right and left-handed upper-left puck carrying at both ends.
- Verified goalie and staff bodies rotate with the rink while their lettering and skater tokens remain upright.
- Verified the populated 3-on-2 rush retains five movement clips and three puck events through all view changes.
- Verified legacy Half Ice templates map into the correct canonical end and retain valid net targets.
- Verified a simulated Version 5.8 Half Ice session returns all tested geometry to its pre-transform positions within 0.0001 board units.
- Verified early entry, complete puck crossing, controlled-carrier entry, tag-up clearing, and both attack directions produce identical indicator states in Full and Half Ice.
- Verified view changes do not add history entries.
- Verified one timeline toggle, no obsolete route HUD, no obsolete action anchor, no duplicate DOM IDs, and no page-level horizontal overflow.
- Responsive checks at 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Release preview generated at 1920 x 1080.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, touch-sized controls, pointer interactions, and responsive behavior were exercised through Chromium emulation.

Version history
---------------
5.9 - Canonical Full Ice world, true rotated/cropped left- and right-end Half Ice cameras, exact view-invariant positions and paths, inverse-camera route tracing, shared world-coordinate off-side logic, and Version 5.8 Half Ice recovery.
5.8 - Experimental coordinate-transform Full/Half Ice orientation, practical Half Ice off-side logic, unobstructed route tracing, timeline-header Move context, and one timeline toggle.
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
