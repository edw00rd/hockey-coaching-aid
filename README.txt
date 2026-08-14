BOTD Hockey Coaching Aid v5.10
Creator: Nicholas Heller

Release focus
-------------
Version 5.10 moves the Full Ice/Half Ice camera controls out of Board Setup and directly onto the rink. The coach can now change the camera without opening Settings, select the visible Half Ice end with one compact pill, and keep the Settings drawer focused on true setup choices.

The Version 5.9 camera model remains unchanged: the play always stays in one permanent 1000 x 600 Full Ice coordinate system. These controls rotate or crop the camera only. They never move a player, goalie, puck, route waypoint, shot target, or telestration point.

What's new in v5.10
-------------------
1. On-rink Full Ice/Half Ice control
   - The rink badge in the upper-left corner is now an interactive button.
   - In Full Ice it reads FULL ICE.
   - Selecting FULL ICE opens HALF ICE - RIGHT END, as requested.
   - In Half Ice the badge identifies the visible end as HALF ICE - LEFT END or HALF ICE - RIGHT END.
   - Selecting either Half Ice badge returns directly to FULL ICE.
   - The control remains available with the Board Setup drawer closed.

2. Compact Half Ice end selector
   - A LEFT/RIGHT pill appears directly above the Half Ice badge.
   - The selected white thumb sits on the left while the left end is visible and on the right while the right end is visible.
   - Tapping LEFT or the left half of the pill selects the left end.
   - Tapping RIGHT or the right half of the pill selects the right end.
   - Left Arrow and Right Arrow provide keyboard end selection.
   - The pill is hidden automatically in Full Ice because an end choice is not needed there.
   - The pill and badge remain inside the rink frame at desktop, tablet, and narrow mobile sizes.

3. Simplified Settings menu
   - Removed the Ice View card from Settings.
   - Removed the Half Ice End buttons from Settings.
   - Removed the Timeline card from Settings.
   - Settings now presents only Appearance & Language, Token Display, and Center-Ice Logo.
   - Routes, route display mode, playback, and timeline length remain available through the permanent bottom toolbar and timeline header.
   - Existing saved display and timeline values continue to load; hidden compatibility state is retained internally without presenting duplicate controls.

4. Centered goalie position badge
   - The goalie G now uses the exact center coordinates of its circular role badge.
   - Central SVG baseline alignment replaces the former vertical offset.
   - In Half Ice, the G counter-rotates around the actual center of the circle, so it remains centered instead of drifting when the rink turns.
   - The correction applies to both goalies in Full Ice and at either Half Ice end.

5. Version 5.9 compatibility
   - Version 5.9 sessions and playbooks are loaded automatically through the Version 5.10 storage fallback.
   - Existing Full Ice world coordinates, the selected view, the selected Half Ice end, routes, puck events, drawings, play options, and puck routes are preserved.
   - The migrated state is normalized to Version 5.10 without rewriting play geometry.
   - Storage fallback remains available for Versions 5.8 through 5.0 as in the prior release.

Camera behavior retained from v5.9
----------------------------------
- One canonical Full Ice world coordinate system for all play data.
- True rotated and cropped left-end and right-end Half Ice cameras.
- Exact player-to-line, goalie-to-net, and puck-to-route relationships across view changes.
- No geometry rewrite and no Undo/Redo transaction when changing the camera.
- Inverse-camera touch and pointer mapping for route tracing in Half Ice.
- Shared Full Ice world-coordinate off-side logic in both views.
- Correct rotated goalie and staff shapes with upright role lettering.
- Correct upper-left and upper-right carried-puck placement by player handedness.

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
- 74 focused interaction, geometry, layout, state-synchronization, and responsive assertions.
- A separate Version 5.9 storage-migration test preserving view, selected end, and complete play geometry.
- A separate multilingual Settings/control test in US English and Swedish.
- Verified the exact control sequence FULL ICE -> HALF ICE - RIGHT END -> FULL ICE.
- Verified LEFT and RIGHT pill selection by pointer and keyboard.
- Verified the pill thumb visually occupies the same side as the selected rink end.
- Verified Full Ice/Half Ice/end switching leaves setup positions, movement clips, puck routes, puck events, and drawings byte-for-byte unchanged.
- Verified both goalie G labels share the exact center of their role circles in Full Ice and rotated Half Ice.
- Verified only Appearance & Language, Token Display, and Center-Ice Logo remain visible in Settings.
- Verified removed Settings controls do not remain focusable or visible.
- Verified bottom Routes, route mode, and timeline Length controls still update the underlying state.
- Verified no duplicate DOM IDs.
- Responsive checks at 1920 x 1080, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Verified no page-level horizontal overflow and that the rink-view controls remain inside the rink at every tested size.
- Release preview generated at 1920 x 1080.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, touch-sized controls, pointer interaction, keyboard behavior, and responsive layout were exercised through Chromium emulation.

Version history
---------------
5.10 - On-rink Full/Half Ice badge, compact left/right Half Ice pill, simplified Settings menu, centered goalie G badge, and Version 5.9 storage migration.
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
