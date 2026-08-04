BOTD HOCKEY COACHING AID — VERSION 5.0
Creator: Nicholas Heller
Release date: 2026-08-04

OVERVIEW

BOTD Hockey Coaching Aid is a standalone HTML5 hockey coaching board for desktop
browsers, iPad, touch, mouse, and Apple Pencil. Version 5.0 replaces the former
turn-based authoring model with one continuous timeline shared by every player
movement and every puck event.

Players now own movement tracks only. The puck owns possession, passes, drops,
and shots. A coach can record all skating routes first, play those routes, and
tap players or open ice to direct the puck in real time. Puck-event chips can be
dragged along the timeline afterward to adjust release and possession timing
without redrawing a player's skating path.

The complete application is contained in index.html. It uses no external
JavaScript libraries, server process, account, database, analytics service, or
network request. Nicholas Heller is acknowledged in the HTML source and this
README as the creator of the application, product concept, coaching workflow,
feature direction, and user experience.

GITHUB PACKAGE CONTENTS

BOTD_Hockey_Coaching_Aid_v5.0_GitHub.zip contains exactly these four updated
files at its root, with no enclosing folder:

- index.html
  The complete Version 5.0 application and GitHub Pages entry point.
- README.txt
  Deployment instructions, operating guidance, Version 5.0 release notes,
  compatibility notes, validation details, known limitations, and the complete
  detailed history from Version 0.1 through Version 5.0.
- Preview.png
  A 1920 x 1080 screenshot generated from this exact Version 5.0 index.html.
- .nojekyll
  An empty marker telling GitHub Pages to publish the repository as a plain
  static site without Jekyll processing.

DEPLOYING TO GITHUB PAGES

1. Extract BOTD_Hockey_Coaching_Aid_v5.0_GitHub.zip.
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

VERSION 5.0 RELEASE NOTES

SINGLE CONTINUOUS TIMELINE

- Removed the turn builder, turn completion workflow, canonical turn reuse, and
  per-turn action lanes from active authoring.
- Added one continuous time ruler shared by all movement clips and puck events.
- Added a dedicated player row for every on-ice object and a dedicated puck row.
- Added a draggable playhead and direct scrubbing from the ruler or any track.
- Added start, previous action, back 0.1 second, Play/Pause, forward 0.1 second,
  next action, and end controls.
- Added direct timeline-length editing from 4 through 60 seconds.
- Kept reversible playback at multiple speed settings.

PLAYER MOVEMENT TRACKS

- Players, goalies, coaches, and managers now own movement only.
- Selecting a rink token opens a Player Movement inspector rather than a puck-
  action or possession panel.
- Record Path creates a movement clip beginning at the current playhead.
- The real time used to trace a route becomes the initial movement duration.
- Each movement clip has independently editable start time and duration.
- Movement clips can be dragged horizontally along the timeline.
- Multiple players can move simultaneously because clips overlap on the same
  master clock.
- A player can have more than one non-destructive movement clip.
- Adding a bench object to the ice still does not open its inspector; the user
  must select the rink token directly.

PUCK DIRECTOR

- Selecting the puck opens the new Puck Director.
- The puck, rather than a player, owns Possess, Pass, Drop, and Shot events.
- Set Possession assigns the puck to any eligible on-ice player at the current
  playhead.
- Pass creates a receiver-targeted event from the current carrier.
- Shot targets any open-ice or net location.
- Drop releases an attached puck at the selected timeline time.
- The Pass Speed, sauce, and Ignore Defense defaults remain adjustable.
- Shot power and Ignore Defense remain adjustable.
- Selecting a puck-event chip opens a precise event inspector.
- Puck-event chips can be dragged directly along the timeline.
- Event-time sliders provide a second fine-adjustment method.
- Pass geometry and moving-receiver lead calculations update whenever the event
  time or player movement changes.
- A puck event that overlaps an earlier in-flight puck is marked invalid rather
  than silently producing an impossible sequence.

LIVE PUCK DIRECTING

- Direct Live from Playhead plays the recorded skating routes while accepting
  rink taps as puck decisions.
- Tapping a player while the puck is loose creates possession at that instant.
- Tapping another player while the puck is possessed creates a pass at that
  instant.
- Tapping open ice creates a shot to that location.
- Pointer-down processing is used during live playback so continuously rendered
  SVG tokens cannot swallow every-other Apple Pencil or touch contact.
- The coach can pause, scrub, drag event chips, change timing, and replay without
  changing player movement.

ALTERNATE PUCK ROUTE TAKES

- Player movement is shared across independent puck-route takes.
- + Puck Take creates a blank alternative without redrawing skating paths.
- Copy duplicates the active puck take for variation editing.
- New Take + Direct from Start creates a blank take and immediately begins live
  puck directing from the beginning.
- The active take can be selected from both the Puck Director and timeline.
- Deleting or clearing a puck take never deletes player movement.

PUCK SIMULATION

- Pass arrival leads a moving receiver from that receiver's timeline position.
- Pass speed changes travel time without changing skating routes.
- Saucer passes retain a distinct in-flight presentation.
- When Ignore Defense is off, the puck checks skater and goalie intersections.
- An obstructed pass can use a one-bank path only when its second leg is no
  longer than its first leg; otherwise it attempts the direct path.
- Shot power changes travel speed.
- Player and goalie blocks leave the puck loose.
- Shots entering the goal mouth remain inside the net and trigger the visual
  GOAL presentation and browser-local siren.
- Puck travel, possession bands, pass spans, and event validity are reconstructed
  at every scrubbed timeline position.

DRAWING AND PRESENTATION

- Select, Pencil, and Erase remain in the bottom command bar.
- Marker color uses the same Grid, Spectrum, and RGB Sliders workflow used for
  team and player colors.
- Marker width is edited in the same marker window.
- Consecutive mouse, touch, or Apple Pencil strokes can be drawn while playback
  is running or paused.
- Recorded routes can be shown in full, shown ahead while erasing behind, or
  hidden.
- Player presentation glow remains available as a visual highlight independent
  of puck ownership.
- Full-screen focus mode, collapsible drawers, token display settings, custom
  center artwork, playbook artwork, team colors, roster editing, RH/LH player
  information, offside light, and JSON backup remain available.

REWRITTEN VERSION 5 PLAYBOOK

The Version 4 turn-based playbook is not imported into Version 5. Version 5 ships
with ten newly generated continuous-timeline templates:

Quick setups:
1. 5v5 Center Faceoff
2. 3v3 Center Faceoff
3. 5v4 Power Play
4. 3v2 Rush
5. 2v1 Rush

Continuous-timeline core plays:
1. Strong-Side Breakout
2. D-to-D Neutral-Zone Regroup
3. 1-2-2 Forecheck
4. Half-Ice Low-to-High Overload Cycle
5. Half-Ice Box + 1 Defensive-Zone Coverage

The quick setups provide ready-made on-ice personnel and geometry. Core plays
include overlapping movement clips and puck events that demonstrate the Version
5 timeline. They can be replayed, scrubbed, retimed, copied into alternative puck
takes, or saved as user plays.

VERSION 5.0 WORKFLOW

1. Place players from the benches or load a Version 5 template.
2. Select a player directly on the rink.
3. Set the playhead to that player's desired start time.
4. Select Record Path and trace the route.
5. Repeat for every player. Overlapping clips move simultaneously.
6. Select the puck.
7. Set initial possession at the current time, or select Direct Live.
8. During Direct Live, tap players for possession or passes and open ice for a
   shot.
9. Pause and drag puck-event chips to fine-tune timing.
10. Select movement clips to trim their start and duration.
11. Create additional puck takes to demonstrate alternate decisions while
    preserving all skating routes.
12. Play, step, scrub, draw, and present the completed play.
13. Save to the Version 5 Playbook and export JSON for backup.

STORAGE AND COMPATIBILITY

Version 5.0 uses new storage keys:

- botdHockeyCoachingAid.session.v5_0
- botdHockeyCoachingAid.playbook.v5_0

Version 4.4 sessions and Playbook entries are not migrated automatically because
the former turn/action-lane structure cannot be translated reliably into the new
continuous player-track and puck-take architecture. Version 4.4 remains usable as
a separate historical release. Rebuild important Version 4 plays in Version 5,
or retain screenshots and JSON exports as reference.

Default embedded BOTD artwork is not duplicated into browser storage. Custom
uploaded images are resized locally before persistence. Local browser storage is
per browser and per website origin; it is not a shared team database.

KNOWN LIMITATIONS

- Puck and collision physics are coaching-oriented tactical approximations, not a
  full rigid-body simulation.
- A puck event cannot begin while an earlier puck flight is still active. The
  event is marked invalid until retimed.
- Moving-player collision checks use short time samples rather than infinitesimal
  continuous collision detection.
- Bank-pass selection uses straight wall segments and one bounce.
- Alternate puck takes share player movement but do not branch roster or setup
  geometry.
- Offside tracking is a token-based teaching indicator, not an officiating or
  video-review system.
- Apple Pencil secondary/double-tap exposure depends on iPadOS and Safari. The
  visible toolbar remains the reliable tool-selection fallback.
- GitHub Pages supplies static hosting only. It does not provide user accounts,
  cloud synchronization, permissions, or a shared database.

VALIDATION PERFORMED

The final Version 5.0 build was checked with Chromium automation for:

- JavaScript syntax and application startup.
- Empty fresh-board state.
- Ten rewritten Playbook templates.
- Bench placement without automatic inspector opening.
- Direct rink selection and Player Movement inspector opening.
- Timed route recording and timeline clip creation.
- Overlapping movement clips.
- Movement-clip timing controls.
- Puck possession, pass, shot, and drop reconstruction.
- Moving-receiver pass prediction.
- Direct timeline dragging of puck events.
- Alternate puck takes that preserve movement.
- Live possession and pass taps during active playback.
- Half-Ice portrait rendering and rotated/cropped center artwork.
- Two consecutive drawing contacts while playback was active.
- Bidirectional scrub and 0.1-second step controls.
- 1920 x 1080 preview generation.
- 1194 x 834 responsive layout without document overflow.
- Console and runtime error monitoring.
- ZIP root filenames and compressed-data integrity.

Physical iPad and Apple Pencil hardware was not available in the build
environment; tablet dimensions and pointer behavior were browser-emulated.

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


END OF README
