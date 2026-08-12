BOTD Hockey Coaching Aid v5.7
Creator: Nicholas Heller

Release focus
-------------
Version 5.7 keeps the complete playback transport available while the timeline is minimized, makes timeline selection easier to identify on the ice, improves targeting feedback, and lets each play option use its own selected puck route.

The normal rink-first workspace remains intact. A coach can now play, pause, rewind, step, jump between actions, and change playback speed without opening the timeline. Expanding the timeline exposes PLAY OPTION and PUCK ROUTE side by side, so combinations such as Option 1 / Puck Route B and Option 2 / Puck Route A remain independent.

What's new in v5.7
------------------
1. Always-available playback transport
   - Moved the complete transport from the expanded timeline into the main bottom toolbar.
   - The controls remain available while the timeline is minimized.
   - Controls are right-aligned immediately to the left of the Routes checkbox.
   - Included controls:
     * Go to start
     * Rewind one second
     * Previous action
     * Step back 0.1 seconds
     * Play / pause
     * Step forward 0.1 seconds
     * Next action
     * Go to end
     * Playback speed
   - The current time code remains beside the transport when horizontal space allows.

2. Circle-on-circle marker selector
   - Replaced the previous marker preview with two concentric circles.
   - The large outer circle displays the selected marker color.
   - The smaller inner circle changes diameter to represent the selected brush width.
   - Color and width update live while the marker dialog is open.
   - The accessible label reports both the color value and line width.

3. Timeline-to-player focus indicator
   - Selecting a player's movement clip on the timeline now adds a yellow ring around that player on the ice.
   - The ring follows the player's interpolated position at the current playhead frame.
   - This makes the selected track clear when names, numbers, or positions are hidden.
   - The indicator is visual only and does not alter movement, possession, or clip timing.

4. Animated target acquisition
   - Upgraded the pass and possession targeting triangle into an animated target-lock treatment.
   - The effect combines an acquiring triangle, rotating scan pattern, and center lock dot.
   - The lock follows the player currently under the pointer while a tap-player command is active.
   - Reduced-motion systems receive a clear static lock treatment.

5. PLAY OPTION and PUCK ROUTE pairing
   - Added a PUCK ROUTE dropdown directly beside the PLAY OPTION dropdown.
   - The dropdown uses the existing puck-route data rather than creating a second route system.
   - Each play option preserves its own active puck route.
   - Switching from Option 1 / Puck Route B to Option 2 / Puck Route A and back restores the correct route for each option.
   - The + Puck route command creates and activates the next route for the current play option.
   - A newly copied play option begins with Puck Route A, making route naming predictable within every option.

Systems retained
----------------
- Exact selected-player route replacement from any playhead frame.
- Independent player movement tracks and non-overlapping movement clips.
- Clean New board with all pieces returned to the two team benches.
- Two ordered team benches and the collapsible Team Benches drawer.
- Classic skater, goalie, coach, manager, and bench-card shapes.
- Set possession by tapping a player on the ice.
- Compact Pass Defaults, Shot Defaults, and Highlight disclosures.
- Flat puck silhouette, black dashed pass routes, and animated red-and-black shot routes.
- Return to bench in the player identity header.
- Context-aware Move After Current Path control.
- Puck-route replacement from the playhead.
- Copy & Reuse play options.
- Collapsible side drawers and full-width timeline.
- Themes, languages, display controls, highlighting, playbook storage, and JSON transfer.
- Storage fallback from Versions 5.6, 5.5, 5.4, 5.3, 5.2, 5.1, and 5.0.

Validation performed
--------------------
- JavaScript syntax validation with Node.js.
- Chromium initialization and runtime-error checks.
- 42 focused browser assertions covering the Version 5.7 interaction and layout changes.
- Verified all requested transport controls are inside the main toolbar and remain visible while the timeline is collapsed.
- Verified rewind, start, end, 0.1-second stepping, previous/next action, play/pause, and playback speed behavior.
- Verified the transport remains immediately left of Routes at desktop and tablet widths.
- Verified the marker selector uses a circular outer color preview and a smaller circular width preview.
- Verified the inner marker circle changes size as brush width changes and that color and width commit together.
- Verified a timeline clip selection creates a yellow focus ring around the correct player.
- Verified the focus ring follows the player's exact interpolated playhead position.
- Verified the target lock contains the animated acquisition triangle, scan layer, and lock dot.
- Verified PUCK ROUTE is directly adjacent to PLAY OPTION.
- Verified new routes appear in the route dropdown and become active.
- Verified Option 1 / Puck Route B and Option 2 / Puck Route A remain independently selected when switching options.
- Verified newly copied options begin with Puck Route A.
- Verified there are no duplicate DOM IDs and no runtime errors after the complete interaction sequence.
- Verified Version 5.6 session migration into Version 5.7, including marker settings, playbook name, and movement data.
- Responsive checks at 1366 x 1024, 1024 x 768, 820 x 1180, and 768 x 1024.
- Release preview generated at 1920 x 1080.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, pointer interactions, touch-sized controls, and responsive behavior were exercised in Chromium.

Version history
---------------
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
