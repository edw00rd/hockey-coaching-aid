BOTD Hockey Coaching Aid v5.6
Creator: Nicholas Heller

Release focus
-------------
Version 5.6 makes puck direction faster to use, reduces Inspector clutter, and gives passes and shots clearer tactical notation on the ice.

The possession workflow now matches the existing tap-target workflow used for passes: choose Set possession, then tap the intended player directly on the rink. Pass, shot, and highlight settings remain available without occupying the Inspector until they are needed.

What's new in v5.6
------------------
1. Tap-to-set possession
   - Removed the scrollable player list from the Puck Director Inspector.
   - Replaced it with one Set possession · tap player command.
   - Selecting the command does not create an event immediately.
   - The next eligible on-ice player tapped becomes the possession target at the current playhead time.
   - The targeting mode clears after the player is selected.
   - Coaches and managers are excluded from possession targeting.

2. Compact Inspector disclosures
   - Pass Defaults is now an expandable section.
   - Shot Defaults is now an expandable section.
   - Highlight is now an expandable section for both players and the puck.
   - Sections begin collapsed to recover vertical space.
   - Each section uses a > indicator when closed and a V indicator when open.
   - Expanded state is retained while the Inspector rerenders during the current session.
   - Disclosure controls expose their expanded/collapsed state for keyboard and assistive-technology use.

3. Revised puck silhouette
   - Replaced the oval/football-like puck drawing with a flatter rectangular side profile.
   - Removed the curved top line.
   - Added subtle straight edge details and a shadow so the puck remains visible over the ice and center logo.
   - Updated the puck identity icon in the Inspector to use the same flatter visual language.

4. Clear pass and shot notation
   - Pass routes now use a black dashed line with a black directional arrow.
   - Shot routes now use an animated alternating red-and-black dashed line.
   - The shot arrowhead carries the same red-and-black treatment.
   - Pass and shot styling remains distinct from each player's team-colored movement route.
   - Systems requesting reduced motion receive the same shot pattern without animation.

5. Player Inspector refinements
   - Moved Return to bench into the top player identity card beside the player's name and lineup information.
   - Move After Current Path is disabled and visibly grayed out when the selected player has no recorded movement path.
   - The command becomes available automatically after that player has at least one movement clip.
   - Move from the current playhead remains available for creating the player's first path.

Systems retained
----------------
- Two ordered team benches and the collapsible Team Benches drawer.
- Clean New board with no pieces deployed.
- Simplified top toolbar and side-drawer edge tabs.
- Exact selected-player route replacement from any playhead frame.
- Independent player timelines and non-overlapping movement clips.
- Puck route replacement from the playhead.
- Alternate puck takes and Copy & Reuse play options.
- Classic skater, goalie, coach, manager, and bench-card shapes.
- Canonical role-based placement positions and goalies in their nets.
- Collapsible side drawers and full-width timeline.
- Rink themes, languages, display controls, presentation highlighting, playbook storage, and JSON transfer.
- Storage fallback from Versions 5.5, 5.4, 5.3, 5.2, 5.1, and 5.0.

Validation performed
--------------------
- JavaScript syntax validation with Node.js.
- Chromium initialization and runtime-error checks.
- 56 focused browser assertions covering the Version 5.6 changes and responsive rendering.
- Verified the possession player list is absent.
- Verified Set possession · tap player creates no event until an on-ice player is tapped.
- Verified the resulting possession event targets the tapped player and targeting mode then clears.
- Verified Pass Defaults, Shot Defaults, and Highlight begin collapsed and expand with > / V indicators.
- Verified disclosure state survives Inspector rerenders during the session.
- Verified the rink puck uses a flat rectangular body and contains no curved top path.
- Verified the Inspector puck icon is wider than it is tall and no longer uses a football-like oval.
- Verified pass paths render as black dashed routes.
- Verified shots render as separate red and black dashed layers with continuous animation and a two-tone arrowhead.
- Verified Return to bench is inside the top player identity card.
- Verified Move After Current Path is disabled with no movement clips and enabled after a clip is recorded.
- Verified no runtime errors after the complete interaction sequence.
- Responsive checks at 1366 x 1024, 1024 x 768, 820 x 1180, 768 x 1024, and 390 x 844.
- Release preview generated at 1920 x 1080.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, responsive behavior, touch-sized controls, and pointer interactions were exercised in Chromium.

Version history
---------------
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
