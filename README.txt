BOTD Hockey Coaching Aid v5.4
Creator: Nicholas Heller

Release focus
-------------
Version 5.4 turns player route editing into the GPS-style workflow requested by the coach:

Pause anywhere on the timeline, select a player, tap Move, and trace that player's new route from the player's exact current position. The movement before that frame is preserved. Everything later for that selected player is replaced. Other players' timelines stay untouched.

What's new in v5.4
------------------
1. Removed the visible "Keep later actions connected" workflow.
   - The app no longer presents that option to the coach.
   - Move edits now default to replacing the selected player's future movement only.

2. Reworked the player-edit workflow around Move.
   - The command bar now shows Move instead of Change Action.
   - The Inspector player button now shows Move from the current playhead time.
   - Double-clicking a player clip or using the Move command starts a route trace from the exact playhead frame.
   - A recording HUD confirms the selected player and the exact start time.

3. GPS-style route replacement.
   - If the playhead is inside an existing path, the path is split at the exact interpolated player position.
   - The prefix before the playhead is preserved.
   - The newly traced route begins from that exact position.
   - All future movement clips for only that player are removed.
   - The player cannot be at two places at once and does not teleport.
   - Other players keep their own independent timelines.

4. New now starts with a clean sheet of ice.
   - Pressing New clears all players, goalies, staff, routes, puck events, and drawings from the ice.
   - Rosters remain available on the benches.
   - The existing canonical deployment positions are still used when pieces are placed back onto the ice.

5. Multiple benches.
   - The top bench area is now split into Players, Goalies, and Staff.
   - Each bench contains both teams, using the existing team colors and card styling.
   - Placing a piece from the bench still uses the correct role-based starting location.

Still retained from v5.3/v5.2
-----------------------------
- Classic skater, goalie, coach, manager, and bench-card shapes.
- Canonical mirrored 5-on-5 setup when pieces are loaded from the bench or when an existing saved option already contains the lineup.
- Goalies load into their nets.
- Collapsible drawers and timeline.
- Independent player movement tracks.
- Non-overlapping movement clips.
- Puck route replacement from playhead.
- Copy & Reuse play options.
- Version 5.3, 5.2, 5.1, and 5.0 storage migration fallback.

Validation performed
--------------------
- JavaScript syntax validation with Node.
- Chromium runtime validation through DevTools Protocol document injection.
- Verified v5.4 initialization.
- Verified Players / Goalies / Staff bench rendering.
- Verified New produces zero on-ice objects.
- Verified bench cards remain available after New.
- Verified placing a player from the bench uses the canonical start position.
- Verified the Move command label appears for a selected player.
- Verified mid-route replacement preserves the pre-playhead prefix and removes the selected player's future movement.
- Verified no movement overlap after replacement.
- Verified Move recording starts at the exact playhead position with scope set to future replacement.
- Verified screenshot generation.

GitHub Pages deployment
-----------------------
Place these four files directly in the repository root:

index.html
README.txt
Preview.png
.nojekyll
