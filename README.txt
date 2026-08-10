BOTD HOCKEY COACHING AID — VERSION 5.3
Creator: Nicholas Heller
Release date: 2026-08-10

OVERVIEW

BOTD Hockey Coaching Aid is a standalone HTML5 hockey coaching board for desktop
browsers, iPad, touch, mouse, and Apple Pencil. Version 5.3 adds frame-accurate
player action revision to the continuous Version 5 timeline: a coach can play a
recorded sequence, pause at any moment, select a moving player, and replace or
reclassify that player's action from the exact paused position without changing
the route prefix that has already occurred.

The new Change Action workflow supports Forward, Backward, Crossover, Glide, and
Stop / Hold. A replacement can redraw only a chosen time window and reconnect the
later track, or replace that player's entire future from the playhead. Existing
movement clips are split by interpolating the exact point on the recorded
polyline. The track remains chronological and non-overlapping, the change is one
undoable transaction, and Cancel leaves the original timeline untouched.

Version 5.3 retains Version 5.2's classic bench cards and hockey-piece shapes,
canonical 5-on-5 setup, rink-first workspace, collapsible full-width timeline,
Record NEW Puck Route From Playhead, and independent Copy & Reuse play Options.
Players, goalies, staff objects, and the puck still share one master clock.

The complete application is contained in index.html. It uses no external
JavaScript libraries, fonts, server process, account, database, analytics
service, or network request. Nicholas Heller is acknowledged in the HTML source
and this README as the creator of the application, product concept, coaching
workflow, feature direction, and user experience.

GITHUB PACKAGE CONTENTS

BOTD_Hockey_Coaching_Aid_v5.3_GitHub.zip contains exactly these four current
files at its root, with no enclosing folder:

- index.html
  The complete Version 5.3 application and GitHub Pages entry point.
- README.txt
  Deployment instructions, operating guidance, Version 5.3 release notes,
  compatibility and migration notes, validation details, known limitations,
  and the complete detailed history from Version 0.1 through Version 5.3.
- Preview.png
  A 1920 x 1080 screenshot generated directly from this exact Version 5.3
  index.html.
- .nojekyll
  An empty marker telling GitHub Pages to publish the repository as a plain
  static site without Jekyll processing.

DEPLOYING TO GITHUB PAGES

1. Extract BOTD_Hockey_Coaching_Aid_v5.3_GitHub.zip.
2. Open the root of the repository used by GitHub Pages.
3. Upload index.html, README.txt, Preview.png, and .nojekyll.
4. Replace the prior versions of those files.
5. Commit to the branch configured under Settings > Pages.
6. Wait for the Pages deployment under the repository's Actions tab.
7. Reload the hosted app with Ctrl+F5 on Windows, or use a full refresh in
   Safari on iPad.

Do not upload the ZIP itself. GitHub Pages does not extract archives. The four
files must be directly in the repository root and the entry file must remain
named index.html.

RUNNING LOCALLY

Open index.html in a current version of Microsoft Edge, Google Chrome, Mozilla
Firefox, or Safari. A local file address and a GitHub Pages address are separate
browser-storage origins. Saved Version 5 plays do not move between those
locations automatically; use Playbook JSON export and import when transferring
between devices or addresses.

VERSION 5.3 RELEASE NOTES

FRAME-ACCURATE CHANGE ACTION WORKFLOW

- Added a persistent Change Action command to the compact bottom toolbar. It
  appears after an on-ice object or one of its movement clips is selected and
  continuously displays the current playhead time.
- While playback is running, tapping a moving player immediately pauses the play,
  selects that player, and retains the exact current playhead timestamp.
- Change Action opens at that exact timestamp rather than snapping to the start
  or end of the original clip.
- The editor states the original action and clip range, confirms that everything
  before the paused frame remains exact, and previews the effect of the chosen
  duration and replacement scope.
- The C keyboard shortcut opens Change Action for the selected player or clip
  when focus is not inside an input control.
- Double-clicking a movement clip opens the same frame-accurate editor.

ACTION VOCABULARY

Version 5.3 records one action type on each movement segment:

- Forward
  Normal forward skating along the recorded route.
- Backward
  Backward-skating notation along the newly traced or preserved route.
- Crossover
  Lateral or crossover skating notation for blue-line movement, gap control,
  side-to-side support, and similar coaching concepts.
- Glide
  A lower-effort coasting segment.
- Stop / Hold
  A stationary segment at the exact playhead position for a chosen duration.

Each action is identified in the expanded timeline, by a distinct route style,
and by a compact badge on the active player token. Legacy movement clips without
an action type are normalized to Forward without changing their route geometry
or timing.

CHANGING BOTH PATH AND ACTION

1. Play or scrub the sequence to the decision point.
2. Pause, or tap the moving player to pause automatically.
3. Select Change Action.
4. Choose Forward, Backward, Crossover, Glide, or Stop / Hold.
5. Choose the replacement duration.
6. Choose how the later track should be handled.
7. Select Trace New Route and draw the new path from the highlighted anchor.
8. Release the pointer or Pencil to commit the revision.

The replacement always starts at the selected player's exact interpolated
position at the playhead. The trace cannot alter the route that occurred before
that timestamp. The chosen duration controls how long the player takes to travel
the traced path; draw time does not determine playback duration.

CHANGING ACTION WHILE KEEPING THE CURRENT ROUTE

When a recorded movement crosses the playhead and a different non-stationary
action is selected, Keep Route applies the new action label to the chosen
portion of the existing polyline. The route, timing, speed along the route, and
later clips remain unchanged. This is useful when the player should follow the
same geometry but perform it backward, as a crossover, or as a glide.

REPLACEMENT SCOPES

KEEP LATER ACTIONS CONNECTED

- Replaces only the chosen playhead-to-end time window.
- Preserves the exact prefix before the playhead.
- Splits any original clip crossing either boundary.
- Keeps later clips at their original timestamps and durations.
- Translates the later route geometry as one connected sequence so the first
  later clip begins at the new endpoint without a position jump.
- Keeps action labels and timing on the later clips.
- Clamps translated points to the rink's legal drawing area.

REPLACE THIS PLAYER'S FUTURE

- Preserves the exact prefix before the playhead.
- Removes every later movement clip belonging to the selected player.
- Adds the newly traced action as that player's replacement future.
- Leaves all other object tracks and puck-event definitions unchanged.
- Holds the player at the new endpoint after the replacement action finishes
  until another action is added.

SAFE TIMELINE EDITING

- A player's movement clips may touch at boundaries but cannot overlap.
- Polyline slicing evaluates the precise route point at the split time.
- A replacement made in the middle of a clip creates a retained prefix and, when
  applicable, a reconnected suffix rather than stacking another clip over it.
- Stop / Hold creates a stationary two-point segment at the evaluated playhead
  position.
- Starting trace mode does not change timeline data. The edit is committed only
  when a valid route is released.
- Canceling the editor or trace mode restores the unchanged original timeline.
- One Undo restores the complete pre-revision player track. One Redo restores
  the complete revision.

PLAYBACK, INSPECTOR, AND VISUAL FEEDBACK

- The selected player's Inspector shows the active action at the playhead and a
  direct Change Action command even when the expanded timeline is hidden.
- The movement-clip Inspector exposes an action selector for notation-only
  changes and a Change From Playhead command for geometry changes.
- Timeline clips show the action name, symbol, start time, and end time.
- Forward, Backward, Crossover, and Glide routes use distinct line treatments.
  Stop / Hold displays a hold marker.
- A compact symbol on a moving token identifies non-default actions during
  playback.
- The exact edit anchor is highlighted on the rink while the action editor or
  route-tracing mode is active.
- The Change Action dialog remains usable at tested desktop, portrait tablet,
  and narrow phone dimensions; its body scrolls while the commit controls remain
  available.

PUCK AND MULTI-PLAYER BEHAVIOR

Changing one player's movement does not mutate another player's movement track.
Existing puck-event definitions are retained. When the edited player possesses
the puck, the puck continues to follow that player's recalculated stick position
until a release, pass, shot, or replacement puck event. The existing puck engine
re-evaluates lead, travel, collisions, and validity against the revised player
positions during playback.

VERSION 5.3 WORKFLOW

1. Build the initial play by recording paths and puck actions as before.
2. Press Play and watch the full sequence.
3. At the moment a read, route, or skating technique should change, tap the
   moving player or pause and select that player.
4. Press Change Action in the bottom command bar or Inspector.
5. Choose the action, duration, and replacement scope.
6. Keep the existing route or trace a new one from the exact paused position.
7. Replay the sequence and repeat at any later or earlier decision point.
8. Use Undo and Redo to compare fine-tuning choices safely.
9. Use Copy & Reuse when the alternative should become a separate play Option
   rather than replace the active Option.
10. Save the play to the Playbook and export JSON before moving to another
    browser, device, domain, or repository path.

RETAINED VERSION 5.2 FEATURES

- Classic wide bench cards and deterministic line/pair order.
- Circular skaters, vertical goalie-pad pieces, and rectangular HC/MGR pieces.
- Canonical mirrored 5-on-5 center-faceoff loading with goalies in their nets.
- Rink-first startup with both side drawers and the timeline minimized.
- Full-width collapsible timeline and compact bottom controls.
- Non-overlapping movement-track normalization and constrained clip timing.
- Record NEW Path From Playhead and Record NEW Path From Here entry points.
- Record NEW Puck Route From Playhead.
- Independent Copy & Reuse play Options with In and Out range markers.
- Responsive drawers, black animated selection ring, possession target triangle,
  Glow controls, themes, languages, telestration, offside display, Playbook, and
  JSON import/export.

STORAGE AND VERSION MIGRATION

Version 5.3 uses these browser-storage keys:

botdHockeyCoachingAid.session.v5_3
botdHockeyCoachingAid.playbook.v5_3

When no Version 5.3 session exists, the application first checks Version 5.2,
then Version 5.1, and finally Version 5.0 storage. Compatible teams, rosters,
on-ice setup, movement clips, puck-route takes, drawings, display settings,
appearance, Playbook entries, custom artwork, Glow settings, and play Options
are normalized into Version 5.3. Existing movement clips gain a Forward action
label when no action metadata is present. Geometry, timing, identities, and
Option independence are preserved during that normalization.

Existing Version 5.2 positions are not replaced by the fresh-board canonical
setup. Version 4 turn/action-lane data is still not migrated automatically
because it cannot be translated reliably into independent continuous movement
tracks and puck-route takes. Version 4 releases remain usable separately.

A browser's local file origin and a GitHub Pages origin are different storage
locations. Export Playbook JSON before changing domains, repository paths,
browsers, or devices.

KNOWN LIMITATIONS

- Physical iPad and Apple Pencil hardware was not available during release
  validation. Tablet dimensions, touch targets, and pointer behavior were tested
  with browser emulation.
- Forward, Backward, Crossover, Glide, and Hold are tactical timeline notation.
  Version 5.3 does not rotate a player's body graphic or simulate skate edges,
  hip orientation, acceleration curves, or biomechanical technique.
- Keep Later Actions Connected translates future route geometry as a group. If a
  translated point would leave the rink, that point is clamped to the legal
  drawing area; a route very near the boards can therefore change shape slightly.
- The timeline is limited to 60 seconds per play.
- Copy & Reuse copies the currently active puck route for the selected range into
  one new play Option. Other alternate puck-route takes remain with the source
  Option unless separately copied.
- Play Options are independent alternatives selected from a list; Version 5.3
  does not render a nested node-and-edge branch graph.
- The coach-oriented physics model is designed for tactical visualization, not
  officiating review or rigid-body scientific simulation.
- Live player collisions along curved, concurrently moving routes are sampled
  rather than solved continuously.
- Browser audio policies may require a direct user gesture before the first goal
  siren or other synthesized sound.
- Native fullscreen, vibration, file pickers, and Pencil secondary gestures vary
  by browser and operating-system support.
- Localization applies to the established application interface. New Version 5.3
  action-editor text is currently English, and user-entered names, imported
  content, and browser-generated system messages are not translated.

RELEASE VALIDATION

The final Version 5.3 release was exercised in headless Chromium with repeatable
checks covering:

- Version number, clean startup, and JavaScript syntax validation
- Version 5.2 classic-piece, canonical-loading, bench-order, and rink-first
  regression checks
- Legacy movement normalization to Forward without geometry loss
- Exact playhead interpolation and route-prefix preservation
- Replace This Player's Future behavior
- Keep Later Actions Connected behavior, timing preservation, and route
  reconnection without a position jump
- Stop / Hold creation at the evaluated playhead position
- Action-only relabeling while preserving current route and timing
- Dialog Cancel and route-trace Cancel with no timeline mutation
- Actual pointer-drawn replacement-route recording
- One-step Undo and Redo of a complete revision transaction
- Timeline action labels, route styles, and live token badges
- Movement-clip Inspector action editing
- Automatic pause and exact-frame retention when tapping a moving player
- No movement overlap after replacement
- Isolation of unrelated player tracks and puck-event definitions
- Copy & Reuse independence after action revision changes
- Record NEW Puck Route From Playhead regression behavior
- Migration from Version 5.2 storage to Version 5.3 keys
- Responsive 1366 x 1024, 1024 x 1366, 820 x 1180, 768 x 1024, and
  390 x 844 rendering checks
- Action-dialog bounds, footer availability, touch-control sizing, and absence of
  document-width overflow at the tested viewports
- Desktop 1920 x 1080 preview rendering
- PNG dimensions and decoding
- ZIP root paths, file names, and compressed-data integrity

No unexpected JavaScript runtime errors occurred in the exercised file-based
release workflows. Tests that inject the complete HTML with setContent report
expected localStorage security warnings because that synthetic document has no
storage origin; file-based migration and release smoke tests use a real file
origin and passed.

COMPLETE DETAILED VERSION HISTORY

VERSION 0.1 — INITIAL STANDALONE HTML5 MVP

- Created a standalone single-file HTML application for desktop browsers.
- Added whole-ice and half-ice rink backgrounds.
- Added editable team names, primary colors, and trim colors.
- Added uploadable center-ice and Team Playbook images.
- Added editable rosters with optional number, name, position, goalie status,
  and active-player selection.
- Added distinct skater and goalie tokens.
- Added team benches and placement of active players onto the rink.
- Added explicit puck-possession state.
- Added sequential Move, Pass, Shoot, and Line switch actions.
- Captured Move timing from the speed used to draw each skating path.
- Added global playback-speed controls.
- Added flat and saucer passes with automatic duration and receiver attachment.
- Added direct-lane obstruction checks and best-available single-bank pass
  routing around players, goalies, boards, and nets.
- Made shots stop at the first intersected player; goalie contact attached the
  puck to the goalie in this original release.
- Added freehand multicolor drawing, adjustable width, undo, redo, whole-stroke
  erasing, and clear-all.
- Added browser-local Team Playbook saving and portable JSON import/export.
- Added mouse, touch, and Apple Pencil Pointer Events support.

VERSION 0.2 — TURN-BASED ANIMATION AND WORKSPACE REDESIGN

- Added two complete 20-player sample rosters with funny names, numbers,
  positions, and two goalies per team.
- Hid player labels on rink tokens by default.
- Added collapsible left setup drawer, right Play Animator drawer, and animation
  timeline.
- Reworked half ice into a north-south portrait presentation.
- Added a turn builder for simultaneous player actions.
- Allowed multiple players to Move during the same turn while a Pass or Shoot
  ran.
- Added moving-receiver lead calculation for passes.
- Added Stop-at-playhead editing and alternate outcome branching.
- Added canonical reusable turns such as T1, T2, T3, T1, T2, T4.
- Added Reuse and Copy & edit controls for turns.
- Added route modes for Show all, Ahead; erase behind, and Hidden.
- Allowed a loose puck to be dragged to a starting location before animation.
- Reserved incoming line-change players to prevent duplicate simultaneous
  substitutions.
- Added normalization of Version 0.1 JSON data into the turn format.

VERSION 0.2.1 — POSSESSION PATCH AND LARGER HALF ICE

- Allowed possession to change while a turn was being built.
- Allowed any on-ice player to take or steal the puck.
- Added Make loose so the puck could remain unpossessed between turns.
- Made a possession-only turn valid.
- Enabled Pass and Shoot immediately for the new carrier.
- Removed an invalid Pass or Shoot automatically if possession changed.
- Stored possession changes as turn events for playback, copying, reuse,
  playbook saving, and JSON export/import.
- Recalculated portrait half ice from live workspace dimensions and expanded it
  to the maximum practical height.
- Refit half ice after window resizing and drawer changes.

VERSION 3.0 — BOTD BRANDING, NAMED PLAYBOOKS, AND PUCK PHYSICS

- Renamed the product BOTD Hockey Coaching Aid.
- Acknowledged Nicholas Heller as creator in source notes and metadata.
- Added the supplied BOTD default center-ice and playbook artwork.
- Added custom playbook naming and name-aware export behavior.
- Changed the starting teams to blue/white DAWGS and white/red WILDCATS.
- Added spinning shot and saucer-puck visuals.
- Added timed shot trajectories, motion streaks, skater block rebounds, goalie
  saves, flat-board reflections, angle-dependent energy retention,
  power-dependent travel, and multi-board ricochet support.
- Extended collision checks over post-board shot paths.
- Removed the player-deletion confirmation prompt.
- Changed release packaging to a TXT README with the full cumulative history.

VERSION 3.1 — LOOSE GOALIE REBOUNDS, ROUNDED RIMS, AND CORE PLAYBOOK

- Changed goalie shot contact from automatic possession to a loose-puck block
  with a visible rebound.
- Added rounded-board tracks and corner-following rim-around shot physics.
- Kept steep-angle impacts as reflected banks.
- Added captain and alternate-captain toggles, persistence, and selection-card
  badges.
- Made Ahead; erase behind the default route mode for new boards and samples.
- Named the default collection BOTD Playbook.
- Seeded three three-turn core plays: whole-ice 5v5, portrait half-ice 5v5, and
  whole-ice 2v1.
- Added goalie trapezoid diagonal markings to whole and half ice.
- Visibly grayed and disabled unavailable playback controls until a turn was
  completed.
- Added Version 3.1 storage migration and cumulative release validation.

VERSION 3.2 — NET-CONTAINED GOALS, GOAL SIREN, AND RINK CORRECTIONS

- Added goal-line and goal-mouth detection for recorded shots.
- Stopped scoring shots inside the net so they no longer bounce from the end
  boards back onto the ice.
- Preserved pre-goal skater and goalie collision priority and loose rebounds.
- Added an illuminated red goal lamp, rink flash, scoring-team GOAL! panel,
  browser-generated goal siren, optional vibration, and timeline event tracking.
- Corrected goalkeeper restricted-area markings to NHL Rule 1.8 proportions:
  22 feet at the goal line and 28 feet at the end boards.
- Made Whole ice the default view for fresh sessions and new boards.
- Added Version 3.2 storage keys, Version 3.1 playbook migration, goal metadata,
  updated validation, and cumulative release documentation.

VERSION 3.3 — PASSING ON THE MOVE AND REVERSIBLE PLAYHEAD

- Replaced the single per-player action restriction with independent Skating and
  Puck lanes.
- Allowed Move plus Pass and Move plus Shoot for the same player in one turn.
- Added timed puck release from the carrier's recorded Move route.
- Added At start, At end, Set from playhead, range-slider, and draggable orange
  release-marker controls.
- Added a turn-preview playhead for choosing a release moment before committing
  the turn.
- Recalculated the pass source from the moving passer's timed position.
- Recalculated the endpoint to lead a moving receiver at the puck arrival time.
- Kept possession with the passer until release, made the puck loose in flight,
  and allowed both skaters to continue moving independently.
- Added moving-player obstruction sampling for calculated pass routes.
- Restricted automatic bank passes to candidates whose second leg is no longer
  than the first leg.
- Retained a straight pass when no bank satisfies that rule.
- Made an obstructed straight-pass fallback stop at the blocker and finish loose.
- Added true forward-and-backward playback-slider scrubbing with complete state
  reconstruction.
- Prevented the goal siren from repeating while the user scrubs across a goal,
  while retaining the visual goal state.
- Hid dotted player and turn-selection rings during playback and active
  scrubbing, restoring them after Stop.
- Added Version 3.3 browser-storage keys and migration from earlier sessions and
  playbooks.
- Updated the standalone package, 1920 x 1080 preview, TXT documentation,
  cumulative version history, and release validation.


VERSION 3.4 — PLAYBACK DOCK, DISPLAY OPTIONS, AND PLAYER COLORS

- Kept Play / Stop, Restart, reversible scrubbing, speed, and Recorded routes
  available in the bottom toolbar when Play Animator is hidden.
- Added responsive dock behavior for desktop drawers and iPad-sized overlay
  drawers.
- Split rink-token display into independent Names, Numbers, Positions, and
  Leadership roles checkboxes.
- Added separate captain and alternate badges to rink tokens when Leadership is
  enabled.
- Added optional per-player primary and trim color overrides to every roster
  entry.
- Allowed player colors to be changed before or after loading a bench, with
  immediate updates throughout the editor.
- Added Team reset behavior so either or both player colors can return to live
  team-color inheritance.
- Persisted player colors and display options in sessions, saved plays,
  playbooks, copied data, and JSON.
- Added Version 3.4 storage keys and migration from Version 3.3 and earlier.
- Updated the standalone package, preview, TXT documentation, cumulative
  history, and release validation.


VERSION 3.5 — AUTOMATIC TURNS, SPEED, TOUCH TARGETING, AND PLAYER GLOW

- Included every on-ice player and goalie automatically when starting a turn.
- Removed the manual turn-participant selection step.
- Added green pending-action rings and orange puck-lane-ready rings.
- Added per-Move speed adjustment from 0.25x through 3.00x with quick presets.
- Preserved route geometry while rescaling timed path points and action duration.
- Recalculated puck-release geometry after movement-speed changes.
- Changed shot targeting to press-drag-release for mouse, touch, and Apple Pencil.
- Added a transparent shot-direction arrow and target reticle during dragging.
- Added separate Ignore defense controls for Pass and Shoot.
- Made Ignore defense on by default for Pass and off by default for Shoot.
- Added per-player Glow, color selection, brightness, blinking, and blink rate.
- Added persisted glow profile fields to sessions, plays, playbooks, and JSON.
- Added a route-mode selector to the bottom toolbar when both side drawers are
  hidden.
- Capitalized Teams & Rink and moved the rink-mode selector above the team cards.
- Changed fresh defaults to green/black DAWGS and pink/yellow FLAMINGOS.
- Added Flip Primary / Trim to both team cards.
- Added top-bar and bottom-toolbar full-screen focus controls with a browser-API
  fallback layout.
- Added Version 3.5 storage keys and migration from Version 3.4 and earlier.
- Updated the GitHub Pages upload package, standalone package, 1920 x 1080 PNG
  preview, TXT documentation, cumulative history, and release validation.

VERSION 3.6 — DIRECT ROUTES, TURN HIGHLIGHTS, STAFF, AND LIVE TELESTRATION

- Removed + New Turn, Move, and Start turn here from the normal authoring flow.
- Started a turn automatically when the first route or action is authored.
- Replaced Move-button recording with direct dragging of the selected rink token.
- Allowed stationary Pass, Shoot, Glow, possession, Line switch, and Whistle actions.
- Removed skating-speed and puck-release quick presets while retaining precision
  sliders and the draggable release marker.
- Moved Glow, brightness, blinking, color, and blink rate from persistent player
  profiles into turn-scoped Highlight actions.
- Added Undo Last Action for an unfinished turn alongside Undo Last Turn.
- Allowed Pencil and Erase telestration to continue as an overlay during playback.
- Added best-effort Apple Pencil secondary/double-tap cycling among Select, Pencil,
  and Erase when the browser exposes the hardware gesture.
- Added reflective inner-net side walls and a soft back-net stop after a goal.
- Added Coach, Manager, and Referee / Official roles with square striped tokens and
  a Whistle timeline action.
- Reduced fresh default rosters to 10 skaters, 2 goalies, 1 coach, and 1 manager.
- Added the requested favorite names and additional cartoon-style roster names.
- Set exact fresh colors to DAWGS #00FC05 / #000000 and FLAMINGOS #F100F3 /
  #FEFE00.
- Rebuilt Teams color editing around diagonal split swatches and compact swap arrows.
- Rebuilt Roster cards with clearer identity, Role, color, and leadership groups.
- Limited Alternate captains to two per team.
- Kept Goalie leadership selectable but visually muted and protected by a tendy
  confirmation warning.
- Added Version 3.6 storage keys and migration from Version 3.5 and earlier.
- Updated standalone and GitHub Pages ZIPs, TXT documentation, cumulative history,
  PNG preview, responsive checks, and release validation.


VERSION 4.0 — PLAYER-CENTERED AUTHORING AND TIMELINE-ONLY ANIMATOR

- Moved Selected Player identity, possession, turn glow, Skating lane, and Puck
  lane controls into a popover anchored beside the selected rink token.
- Moved skating-speed, Pass, Shoot, Line Switch, Whistle, and puck-release
  controls into player-relative popovers and option sheets.
- Kept the selected-player workflow available in app-level focus mode and made
  the popover scrollable and viewport-aware on iPad.
- Reduced the Play Animator drawer to the Animation Timeline and timeline
  management controls.
- Removed green status/check messages from the Play Animator drawer.
- Added a SETTINGS tab beside PLAYBOOK.
- Moved Ice View, Token Display, and Center-Ice Logo into SETTINGS.
- Moved Playbook Logo into the PLAYBOOK tab.
- Replaced the bottom marker-color row with one marker swatch that opens a unified
  color and width window.
- Kept the last marker color and made black the fresh default.
- Allowed Pencil and Erase telestration during active playback and while paused
  at an intermediate playhead position.
- Added bottom-toolbar Undo Last Action, Undo Last Turn, Done Turn, and Cancel
  controls beside playback.
- Retained reversible scrubbing, playback speed, recorded routes, and route mode
  in the bottom command center.
- Added an opaque isolated iPad workspace layer to prevent duplicated or exposed
  background when the Play Animator drawer is hidden.
- Added Version 4.0 browser-storage keys and migration from Version 3.6 data.
- Updated the GitHub Pages package, cumulative TXT README, repository README,
  release preview, package integrity checks, and deployment instructions.


VERSION 4.1 — CONTEXTUAL PLAYER DRAWER, OFFSIDE LIGHT, AND PENCIL RELIABILITY

- Stopped bench placement from automatically selecting the newly placed object.
- Required direct rink-token selection before opening Player Actions.
- Replaced the rink-anchored Version 4.0 popover with a dedicated right-side
  Player Actions drawer.
- Kept programmatic selection changes from opening the drawer unexpectedly.
- Simplified Player Actions so unavailable controls are removed rather than
  displayed as clutter.
- Kept Possession visible as the primary state control.
- Hid the Puck lane until the selected player possesses the puck.
- Hid and directly guarded Line Switch while the selected player has possession.
- Removed a contradictory Line Switch action when that player subsequently takes
  possession.
- Hid Line Switch when no eligible bench replacement exists.
- Kept Pass visible but gray and disabled when only one eligible player is on the
  ice, then unlocked it automatically when a receiver becomes available.
- Reduced turn highlight controls to one Glow button opening a nested editor for
  enablement, color, brightness, blinking, and blink rate.
- Added a discreet upper-right onside/offside status light with a green onside
  state, dark-yellow offside state, mouse-hover description, and accessible text.
- Added Team A/right and Team B/left whole-ice attacking-direction inference and
  a single-zone half-ice calculation.
- Excluded Coach, Manager, and Official staff objects from offside calculation.
- Animated the selected-player dashed ring with fluid changing speed.
- Added a short browser-local "vroom vroooom" selection sound and stopped the
  wheel once route tracing begins.
- Rebuilt live drawing around capture-phase Pointer Events to prevent alternating
  Apple Pencil contacts during playback.
- Added explicit stale-pointer, lost-capture, pointer-cancel, coalesced-sample,
  and short palm-rejection handling for live telestration.
- Added Version 4.1 browser-storage keys and migration from Version 4.0 and the
  earlier supported release families.
- Updated the GitHub-ready three-file package, exact internal filenames,
  cumulative README, Version 4.1 preview, automated interaction checks, and ZIP
  integrity validation.



VERSION 4.2 — STRUCTURED LINES, TAG-UP OFFSIDE, AND TIMED STAFF CUES

- Added four complete forward lines per team with LW, C, and RW assignments on
  Lines 1 through 4.
- Added three complete defense pairs per team with LD and RD assignments on
  Pairs 1 through 3.
- Expanded fresh rosters to 18 skaters, 2 goalies, 1 coach, and 1 manager per
  team while preserving the requested cartoon-style names and exact team colors.
- Made a fresh game open as a complete 5-on-5 center-ice faceoff with both first
  forward lines, first defense pairs, starting goalies, and a loose puck.
- Added editable Line assignment and RH/LH handedness controls to roster cards.
- Made an attached puck render on the player's selected carrying side.
- Reordered bench members as Forward Line 1, Defense Pair 1, Forward Line 2,
  Defense Pair 2, Forward Line 3, Defense Pair 3, Forward Line 4, goalies, and
  staff.
- Rebuilt Line Switch candidate order around the acting player's position and
  cyclic next-line rotation, followed by the remaining position groups and
  goalies.
- Excluded coaches, managers, and officials from Line Switch candidates and hid
  Line Switch for staff.
- Added Send to bench as a turn-level skating action with possession release and
  playback reconstruction.
- Hid Skating Lane controls after a route is traced and replaced them with the
  skating-speed editor.
- Stacked skating-speed and puck-release/turn-preview sliders for moving Pass and
  Shoot actions.
- Reduced Glow to an immediate checkbox plus adjacent advanced-settings gear.
- Made no-possession Glow default to the player's primary color, with cyan as the
  white-primary fallback.
- Made Glow default to blinking green when the player's team has possession and
  blinking red when the opposing team has possession.
- Moved the offside light outside the upper-right rink edge and added a SETTINGS
  checkbox to show or hide it.
- Added a stateful delayed-offside/tag-up tracker with green onside, orange early-
  entry warning, blinking-red puck-entry infraction, tag-up reset, and legal
  re-entry behavior.
- Disabled Captain and Alternate controls for coaches and managers and normalized
  incompatible imported staff leadership values off.
- Removed the persistent MAX 2 A warning and added an information dialog when a
  third Alternate is attempted.
- Retained visually muted but selectable goalie leadership with the existing
  tendy confirmation.
- Converted Whistle into a timed turn action with a release slider usable during
  a movement route or a stationary turn.
- Added an inline Whistle timing editor after the action is authored.
- Added a cute side-to-side staff shake with rapid black/white token swaps at the
  whistle moment.
- Ensured late stationary whistle timing extends the turn duration sufficiently.
- Enforced deterministic turn action ordering: possession, movement, line/bench,
  puck or whistle event, then Glow.
- Added Version 4.2 browser-storage keys and migration from Version 4.1, Version
  4.0, and earlier supported release families.
- Updated the GitHub-ready package to contain exactly index.html, README.txt,
  Preview.png, and .nojekyll at the ZIP root.
- Added a current 1920 x 1080 preview, complete cumulative README, detailed
  release verification, package integrity checks, and deployment instructions.

VERSION 4.3 — ORDERED PUCK COLLECTION, INDEPENDENT LANE TIMING, AND QUICK SETUPS

- Changed fresh boards and the New command so nobody begins on the ice.
- Added four BOTD Playbook quick setups: 5v5 center faceoff, 3v3 center faceoff,
  3v2 rush, and 2v1 rush, with a goalie included for each team.
- Made possession selection the first authoring decision for a new loose-puck
  pickup.
- Hid and locked the possession control as soon as movement tracing began.
- Treated movement without an armed pickup as a decision not to take new loose-
  puck possession during that turn.
- Calculated delayed puck pickup at the closest projected point on the player's
  timed skating polyline.
- Kept the puck loose until the calculated pickup timestamp and attached it only
  after the player reached that point.
- Recalculated pickup timing whenever the skating-speed multiplier changed.
- Prevented Pass or Shot release from being trimmed earlier than pickup.
- Required a recorded Skating Lane before a newly authored Pass or Shot.
- Added adjustable Shot power alongside release and preview timing.
- Added adjustable Pass puck speed/power alongside release, sauce, defense, and
  preview timing.
- Grouped independent Skating Lane and Puck Lane sliders in one Player Actions
  timing workspace until Done Turn.
- Added carry-forward Glow state so a highlight remains active in later turns
  until explicitly unchecked.
- Restored glow state correctly when an unfinished turn is canceled.
- Normalized the initial offside frame so a play begins green or, at worst,
  orange instead of immediately blinking red.
- Rotated the center image 90 degrees and clipped it to the visible half-center
  area in portrait Half Ice.
- Added Version 4.3 browser-storage keys and migration from Version 4.2 sessions,
  Playbooks, and user-created plays.
- Rebuilt the release preview from the final Version 4.3 HTML and updated the
  GitHub package to contain exactly index.html, README.txt, Preview.png, and
  .nojekyll at the archive root.
- Added repeatable Chromium validation for ordered authoring, delayed pickup,
  lane trimming, pass/shot power, glow persistence, quick setups, offside
  initialization, half-ice artwork, responsive layout, and runtime errors.

VERSION 4.4 — PLAYER-RELATIVE HANDEDNESS, START-OF-TURN PUCK RIGHTS, AND EXPANDED PLAYBOOK

- Corrected attached-puck orientation so RH/LH is measured from each player's
  perspective and relative to that team's attacking direction.
- Applied the same attack-vector puck offset to displayed possession, Pass
  source points, Shot source points, and receiver stick-side targets.
- Made Glow blink by default while retaining the existing primary-color, cyan,
  friendly-possession green, and opponent-possession red defaults.
- Replaced Version 4.3's route-before-possession lock with a persistent possession
  control that remains available before and after movement.
- Added explicit start-of-turn possession rights: only a player who begins the
  turn with the puck may Pass or Shoot in that turn.
- Allowed non-starting carriers to Move and take possession during a turn while
  deferring their Puck Lane until the next turn.
- Preserved closest-vector-point pickup timing for a player who collects the puck
  after movement.
- Added nearby stationary pickup support while rejecting unresolved distant
  stationary collections at Done Turn.
- Allowed a start-of-turn carrier to create a stationary Pass or Shot before a
  skating route exists.
- Allowed a skating route to be added after a Pass or Shot and automatically
  expanded release timing across that route.
- Allowed start-of-turn possession to be dropped or restored after movement has
  already been authored.
- Removed contradictory Pass or Shot actions automatically when possession is
  dropped or scheduled to transfer to another player.
- Kept Skating and Puck Lane controls independently adjustable until Done Turn.
- Updated the Player Actions drawer to show only rights that apply to the
  player's start-of-turn state.
- Renamed active Puck Speed labels and descriptions to Pass Speed.
- Added a fifth quick setup: 5v4 Power Play.
- Retained 5v5 and 3v3 center faceoffs plus 3v2 and 2v1 rush quick setups, all
  with both starting goalies.
- Added five animated core coaching-board plays: Strong-Side Breakout, D-to-D
  Neutral-Zone Regroup, 1-2-2 Forecheck, Half-Ice Low-to-High Overload Cycle,
  and Half-Ice Box + 1 Defensive-Zone Coverage.
- Ensured every generated core-play turn contains no more than one puck action.
- Added separate Quick setup and Core play visual markers in BOTD Playbook.
- Added Version 4.4 browser-storage keys with migration from Version 4.3 while
  preserving user-created Playbook entries.
- Kept fresh and New boards empty so the coach chooses between manual placement
  and a quick or core template.
- Added repeatable diagnostics for handedness quadrants, possession rights,
  delayed pickup, lane eligibility, Playbook inventory, and sample loading.
- Rebuilt Preview.png from the final Version 4.4 index.html and packaged exactly
  index.html, README.txt, Preview.png, and .nojekyll at the ZIP root.

VERSION 5.0 — SINGLE TIMELINE, PUCK DIRECTOR, AND ALTERNATE ROUTE TAKES

- Replaced the turn-based editor with one continuous timeline.
- Removed turn completion, canonical turn reuse, and per-player puck lanes from
  active Version 5 authoring.
- Added player-specific movement tracks that can overlap in time.
- Made players, goalies, coaches, and managers movement-only objects.
- Added timed movement clips with draggable timeline position, editable start,
  and editable duration.
- Added start, previous action, 0.1-second backward step, Play/Pause, 0.1-second
  forward step, next action, and end transport controls.
- Added a directly draggable and fully reversible timeline playhead.
- Moved Possess, Pass, Drop, and Shot ownership to the puck itself.
- Added the Puck Director inspector.
- Added timeline event chips for possession, passes, drops, and shots.
- Made puck-event chips directly draggable to retime release and possession.
- Added event-specific timing and target controls.
- Added moving-receiver lead calculation from the shared player timeline.
- Preserved Pass Speed, sauce, shot power, and Ignore Defense options.
- Added live puck directing while recorded skating routes play.
- Made a live tap on a player create possession or a pass at that instant.
- Made a live tap on open ice create a shot to that location.
- Processed live puck taps on pointer-down to remain reliable during SVG animation.
- Added multiple alternate puck-route takes sharing the same player movement.
- Added blank-take creation, take duplication, take deletion, take clearing, and
  New Take + Direct from Start.
- Added possession bands and puck-flight spans to the timeline.
- Marked overlapping in-flight puck events invalid instead of silently executing
  impossible sequences.
- Retained coaching-oriented pass banks, defense collisions, goalie/player
  blocks, net-contained goals, GOAL presentation, puck spin, and local audio.
- Retained whole-ice and portrait half-ice boards, custom center artwork,
  rotated/cropped half-ice logo treatment, team and roster editing, benches,
  drawing, route display, offside light, fullscreen mode, playbook artwork, and
  JSON backup.
- Replaced the Version 4 turn-based Playbook with ten native Version 5 timeline
  templates: five quick setups and five continuous core plays.
- Started Version 5 with fresh storage keys and intentionally did not migrate
  Version 4 turn/action-lane data.
- Reduced browser-storage use by keeping default embedded artwork out of saved
  session JSON.
- Generated Preview.png from the final Version 5.0 index.html.
- Packaged exactly index.html, README.txt, Preview.png, and .nojekyll at the ZIP
  root.


VERSION 5.1 — RESPONSIVE DRAWERS, PRESENTATION TARGETING, THEMES, AND LANGUAGES

- Removed both side-drawer close-X buttons and replaced them with persistent edge
  handles.
- Made the rink refit and expand when Board Setup, Inspector, or both are hidden.
- Preserved overlay drawer behavior at tablet widths.
- Added true timeline minimization and made the rink use the released vertical
  space.
- Made the timeline span and rescale to the complete viewport width.
- Added responsive seconds-to-pixels calculation and adaptive tick intervals.
- Replaced the white selected-object ring with a black high-contrast ring.
- Added a variable-speed “vroom vroooom” ring animation with reduced-motion
  support.
- Replaced the possession target select field with a large on-ice player list.
- Added a red rink targeting triangle for the hovered, focused, or selected
  possession target.
- Added persistent player Glow controls with color, brightness, blink, and rate.
- Added matching puck Glow controls and saved puck-glow state.
- Fixed the paused puck jumping to the upper-left SVG origin by separating puck
  translation and rotation into nested groups.
- Added a last-valid puck-position safeguard and paused-spin behavior.
- Added Light and Dark themes, with Light as the default.
- Enlarged controls and adopted a USA Hockey-inspired navy, blue, red, white, and
  ice-blue visual system without representing an official affiliation.
- Added Settings language support for US English, Canadian English, Swedish,
  Finnish, and Russian.
- Added playful Canadian-English “eh” interface text and a center-ice maple leaf.
- Kept user-entered names and imported Playbook content unchanged by language
  selection.
- Added Version 5.1 browser-storage keys and migration from Version 5.0.
- Retained all ten continuous-timeline templates and existing Version 5 movement,
  puck directing, alternate takes, physics, telestration, offside, Playbook, and
  JSON features.
- Generated a new 1920 x 1080 Preview.png from the final Version 5.1 application.
- Packaged exactly index.html, README.txt, Preview.png, and .nojekyll at the ZIP
  root.


VERSION 5.2 — CLASSIC PIECES, SAFE PATH REPLACEMENT, AND REUSABLE PLAY OPTIONS

- Restored the classic wide bench cards with player name, number, position,
  handedness, and forward-line or defensive-pair information.
- Restored circular skater pieces with thick team-color trim and separate
  position badges.
- Restored rectangular head-coach and manager pieces with horizontal center bars
  and HC/MGR badges.
- Restored vertical goalie-pad pieces with a G badge and placed both starting
  goalies in the correct nets.
- Added a deterministic 5-on-5 center-faceoff setup with C, upper wing, lower
  wing, upper defense, and lower defense loading in the requested mirrored order.
- Loaded head coaches and managers into their requested center-ice staging
  positions while preserving movement editing for all object types.
- Reordered each bench deterministically by forward line and defensive pair, with
  C, LW, RW, LD, and RD sequence inside each group.
- Made the fresh workspace rink-first by starting both side drawers and the
  timeline minimized.
- Added a prominent Timeline drawer control to the bottom command bar while
  retaining the existing compact transport, route, drawing, undo, and fullscreen
  controls.
- Added Record NEW Path From Playhead, preserving the route prefix through the
  exact playhead and replacing that object's future movement.
- Added Record NEW Path From Here, continuing from the selected or applicable
  clip endpoint and replacing only that object's later movement.
- Added polyline interpolation and clip splitting so a replacement made inside a
  movement clip preserves the exact prefix rather than snapping to a waypoint.
- Enforced non-overlapping movement tracks during normalization, recording,
  timeline dragging, and Inspector timing edits.
- Added Record NEW Puck Route From Playhead with exact puck-position or
  possession seeding and safe truncation of an in-progress puck flight.
- Added timeline In and Out markers plus Copy & Reuse.
- Made Copy & Reuse capture every on-ice object's position at the selected range
  start, trim and shift intersecting movement clips, seed the active puck state,
  copy active-route puck events, and create an independent play Option.
- Added an Option selector and option deletion controls to the full-width
  timeline. Editing a copied Option no longer changes its source Option.
- Added Version 5.2 browser-storage keys and migration from Version 5.1, with a
  Version 5.0 fallback retained for users upgrading across two releases.
- Preserved Version 5.1 responsive drawers, black animated selection ring,
  possession target triangle, Glow controls, themes, languages, paused-puck fix,
  telestration, offside display, Playbook, and JSON import/export.
- Rebuilt Preview.png from the final Version 5.2 application.
- Packaged exactly index.html, README.txt, Preview.png, and .nojekyll at the ZIP
  root.

VERSION 5.3 — FRAME-ACCURATE PLAYER ACTION REVISION

- Added Change Action to the persistent bottom command bar for the selected
  player or movement clip.
- Made tapping a moving player during playback pause immediately while retaining
  the exact playhead timestamp.
- Added an action editor that opens at the exact interpolated player position.
- Added Forward, Backward, Crossover, Glide, and Stop / Hold movement metadata.
- Added selectable action durations and quick duration controls.
- Added Keep Later Actions Connected, preserving later clip times while
  translating future geometry to reconnect at the new endpoint.
- Added Replace This Player's Future, preserving the exact prefix and removing
  only the selected player's later clips.
- Added Keep Route action changes for reclassifying a segment without changing
  its path, timing, speed, or later movement.
- Added route tracing from a highlighted playhead anchor with commit-on-release
  and cancel-without-mutation behavior.
- Added exact clip splitting at both replacement boundaries.
- Preserved the no-overlap invariant after all action revisions.
- Made each revision one Undo/Redo transaction.
- Added timeline action names and symbols, differentiated route notation, hold
  markers, and active-token action badges.
- Added current-action information and Change From Playhead controls to the
  Inspector.
- Added double-click and C-key access to the action editor.
- Normalized Version 5.2 clips without action metadata to Forward.
- Added Version 5.3 storage keys and migration fallback through Versions 5.2,
  5.1, and 5.0.
- Updated Playbook export filenames to identify Version 5.3.
- Retained and regression-tested Copy & Reuse, puck-future replacement, classic
  pieces, canonical setup, responsive drawers, full-width timeline, Playbook,
  themes, languages, and GitHub Pages packaging.
- Generated Preview.png from the final Version 5.3 application.
- Packaged exactly index.html, README.txt, Preview.png, and .nojekyll at the ZIP
  root.

END OF README
