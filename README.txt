BOTD Hockey Coaching Aid v5.5
Creator: Nicholas Heller

Release focus
-------------
Version 5.5 refines the rink-first workspace around two team benches and makes a Move edit behave like rerouting a GPS track from an exact point in time.

Pause the play at any frame, select one player, and choose Move from the displayed timestamp. The new trace begins at that player's exact interpolated location. That player's route before the timestamp is preserved; only that player's future movement is replaced. No other player track is reset or rewritten.

What's new in v5.5
------------------
1. Two team benches
   - The bench area has returned to exactly two benches: one for each team.
   - Only pieces not currently on the ice appear on a bench.
   - Each team's bench follows a deterministic hockey lineup order:
       Starting goalie
       First-line forwards: LW, C, RW
       First defensive pair: LD, RD
       Second-line forwards
       Second defensive pair
       Third-line forwards
       Third defensive pair
       Additional forward lines or defensive pairs in the same sequence
       Backup goalie
       Head coach
       Manager
   - The order remains stable as pieces are placed on and returned from the ice.

2. Collapsible bench drawer
   - A full-width Team Benches header now hides or reveals both team benches together.
   - The drawer reports the current number of available pieces for each team.
   - Collapsing the benches returns vertical space to the rink.
   - The control exposes an expanded/collapsed state for keyboard and assistive-technology use.

3. Simplified top toolbar
   - Removed the top buttons that duplicated the left and right drawer tabs.
   - The top toolbar now retains only:
       BOTD playbook image, software title, and version
       New
       Save play
       Full-screen
   - The existing edge tabs remain the controls for opening Board Setup and Inspector.

4. Exact Move-from-playhead editing
   - The Inspector presents the selected player's command with the exact playhead time, such as Move from 0:01.3.
   - Starting Move captures that player's exact interpolated position before any timeline data is changed.
   - If the timestamp falls inside an existing route, that route is split at the precise frame.
   - The route prefix before the frame remains unchanged.
   - All later movement is removed only from the selected player's track.
   - The replacement trace starts at the captured position, preventing a jump or teleport.
   - Every other player's movement clips remain unchanged.
   - Puck events and setup positions remain unchanged by the player-route edit.
   - Movement clips can meet at a boundary but cannot overlap.
   - Cancel leaves the original timeline untouched.
   - A committed replacement is one Undo/Redo transaction.

5. Route-only movement controls
   - Removed the Skating Action choices and related Forward, Backward, Crossover, Glide, and Stop/Hold notation controls.
   - Player clips and timeline labels now use the single, direct Move concept.
   - Older files containing action metadata continue to load; their route geometry and timing are retained and displayed as Move clips.

6. One timeline visibility control
   - Removed the duplicate Timeline HIDE text control.
   - The bottom-toolbar chevron remains the single show/hide control for the timeline.

7. Clean New board retained
   - New still creates an empty sheet of ice with no players, goalies, or staff deployed.
   - Complete rosters remain available on the two ordered team benches.
   - Existing role-based default placement coordinates remain available when pieces are placed back on the ice.

Systems retained
----------------
- Classic skater, goalie, coach, manager, and bench-card shapes.
- Canonical mirrored deployment positions for pieces placed on the ice.
- Goalies placed in their proper nets.
- Independent player timelines and non-overlapping movement clips.
- Puck route editing from the playhead.
- Copy & Reuse play options.
- Collapsible side drawers and a collapsible full-width timeline.
- Rink themes, languages, display controls, presentation glow, playbook storage, and JSON transfer.
- Storage fallback and migration from Versions 5.4, 5.3, 5.2, 5.1, and 5.0.

Validation performed
--------------------
- JavaScript syntax validation with Node.js.
- Chromium initialization and runtime-error checks.
- Verified the requested top-toolbar controls and retained side tabs.
- Verified exactly two team benches and removal of the three category benches.
- Verified bench collapse/expand behavior and accessibility state.
- Verified New creates an empty ice surface and exposes all 22 roster entries per team.
- Verified the complete bench order, including starter and backup goalie labels and staff at the end.
- Verified exact interpolation at a 1.3-second mid-route edit point.
- Verified the actual Inspector button labeled Move from 0:01.3 starts at 1.3 seconds rather than resetting to zero.
- Verified starting Move does not mutate any movement track.
- Verified the selected route prefix is preserved and its old future is removed.
- Verified an actual pointer-drawn route starts at the exact edit anchor and commits on release without teleportation.
- Verified other-player tracks, puck events, and setup positions remain unchanged.
- Verified no overlapping movement clips after replacement.
- Verified removal of visible skating-action controls and generic Move timeline labels.
- Verified one Undo restores the complete pre-edit timeline.
- Verified Version 5.4 session migration to Version 5.5.
- Responsive browser checks at 1024 x 768, 820 x 1180, and 390 x 844.
- Release preview generated at 1920 x 1080.

Physical iPad and Apple Pencil hardware were not available for release validation. Tablet dimensions, responsive behavior, touch-sized controls, and pointer interactions were exercised in Chromium.

Version history
---------------
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
