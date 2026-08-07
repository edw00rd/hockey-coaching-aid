BOTD HOCKEY COACHING AID — VERSION 5.1
Creator: Nicholas Heller
Release date: 2026-08-06

OVERVIEW

BOTD Hockey Coaching Aid is a standalone HTML5 hockey coaching board for desktop
browsers, iPad, touch, mouse, and Apple Pencil. Version 5.1 preserves the Version
5 continuous-timeline model while substantially refining the workspace for live
presentation, tablet use, and rapid puck-route authoring.

Players own movement clips on one shared timeline. The puck owns possession,
passes, drops, and shots on that same clock. The coach can record skating first,
play or scrub the routes, direct the puck by selecting players or open ice, and
then retime movement clips and puck events without redrawing the play.

The complete application is contained in index.html. It uses no external
JavaScript libraries, fonts, server process, account, database, analytics
service, or network request. Nicholas Heller is acknowledged in the HTML source
and this README as the creator of the application, product concept, coaching
workflow, feature direction, and user experience.

GITHUB PACKAGE CONTENTS

BOTD_Hockey_Coaching_Aid_v5.1_GitHub.zip contains exactly these four current
files at its root, with no enclosing folder:

- index.html
  The complete Version 5.1 application and GitHub Pages entry point.
- README.txt
  Deployment instructions, operating guidance, Version 5.1 release notes,
  compatibility and migration notes, validation details, known limitations,
  and the complete detailed history from Version 0.1 through Version 5.1.
- Preview.png
  A 1920 x 1080 screenshot generated directly from this exact Version 5.1
  index.html.
- .nojekyll
  An empty marker telling GitHub Pages to publish the repository as a plain
  static site without Jekyll processing.

DEPLOYING TO GITHUB PAGES

1. Extract BOTD_Hockey_Coaching_Aid_v5.1_GitHub.zip.
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

VERSION 5.1 RELEASE NOTES

RESPONSIVE DRAWER WORKSPACE

- Removed the close-X controls from both side panels.
- Converted Board Setup and Inspector into persistent edge-operated drawers.
- Added visible left- and right-edge handles that remain available after a
  drawer is collapsed.
- Made the rink automatically refit after either drawer opens or closes.
- Allowed the rink to expand through the released horizontal space when one or
  both drawers are hidden.
- Preserved overlay-drawer behavior at tablet widths so opening a panel does not
  permanently compress the rink.
- Kept the top-left and top-right drawer buttons synchronized with the edge
  handles.
- Replaced the drawing-clear X glyph with a distinct clear-telestration symbol
  so no remaining X appears to be a panel-close control.

MINIMIZABLE, FULL-WIDTH TIMELINE

- Added true timeline minimization rather than a reduced-height collapsed state.
- Kept a toolbar control available to restore the timeline after it is hidden.
- Expanded the rink vertically when the timeline is minimized.
- Made the timeline dock occupy the full viewport width, independently of side-
  drawer state.
- Recalculated seconds-to-pixels from the live timeline-body width.
- Used adaptive tick spacing so long timelines remain legible on narrower
  screens.
- Re-rendered the timeline automatically after viewport, drawer, and timeline
  size changes.
- Preserved movement-clip dragging, puck-event dragging, reversible scrubbing,
  transport controls, and alternate puck-route takes.

SELECTED-OBJECT PRESENTATION

- Changed the selected-player and selected-puck dashed ring to black for clear
  contrast against white ice.
- Replaced constant-speed ring rotation with a variable-speed “vroom vroooom”
  animation that accelerates and eases during each cycle.
- Kept reduced-motion browser preferences respected by disabling the decorative
  animation when requested by the operating system.
- Added a player Glow control to the Player Movement inspector.
- Added a separate puck Glow control to Puck Director.
- Added independently adjustable glow color, brightness, blink enablement, and
  blink rate for both player tokens and the puck.
- Preserved player glow profiles in saved state and Playbook JSON.
- Added a saved global puck-glow profile to Version 5.1 state.

POSSESSION-TARGET VISIBILITY

- Replaced the compact possession select field with a large scrollable list of
  on-ice players.
- Added team-color dots and team names to each possession choice.
- Added a red targeting triangle around the matching rink token whenever a
  possession choice is hovered, keyboard-focused, or selected.
- Kept the triangle visible for the selected target even when token names,
  numbers, positions, and leadership labels are hidden.
- Retained the same target marker while retargeting an existing possession or
  pass event.

PAUSED-PUCK POSITION CORRECTION

- Fixed the intermittent paused puck jump to the SVG origin in the upper-left
  corner.
- Separated puck translation from puck-spin rotation into nested SVG groups.
- Applied translation only to the outer puck group and spin only to the inner
  puck artwork.
- Added a last-valid-position guard for non-finite transient geometry.
- Stopped cosmetic puck spin while paused without changing the puck's calculated
  timeline position.

LIGHT AND DARK APPEARANCE

- Added a Settings appearance selector with Light and Dark modes.
- Made Light mode the default for fresh Version 5.1 boards.
- Enlarged core controls, timeline transport buttons, drawer widths, and touch
  targets.
- Reworked Light mode around a USA Hockey-inspired navy, blue, red, white, and
  ice-blue presentation palette.
- Added low-glare Dark mode while preserving the same spatial hierarchy.
- Updated panels, benches, timeline tracks, dialogs, inputs, toast messages,
  and command controls for both themes.
- Updated the browser theme-color metadata when the theme changes.
- This visual treatment is an original coaching-aid interface and does not imply
  endorsement by or affiliation with USA Hockey.

LANGUAGE SUPPORT

- Added a Settings language selector for:
  - US English
  - Canadian English
  - Swedish
  - Finnish
  - Russian
- Localized the primary navigation, Settings, Playbook controls, timeline,
  movement and puck inspectors, glow controls, possession workflow, and major
  status labels.
- Stored the selected language in the Version 5.1 browser session.
- Added the playful Canadian-English mode requested by the creator: translated
  interface strings receive “eh,” and a red maple leaf appears at center ice.
- Kept team names, player names, play names, coach-authored notes, and imported
  user data exactly as entered rather than altering them with localization.
- Browser-generated error text and operating-system file-picker text remain
  controlled by the browser and device.

VERSION 5.1 WORKFLOW

1. Place players from either bench or load a Version 5 template.
2. Select a player on the ice and record one or more movement clips beginning at
   the current playhead.
3. Select the puck to open Puck Director.
4. Hover or focus a player in the possession list to identify that token with the
   red targeting triangle.
5. Add possession, passes, drops, or open-ice shots on the shared timeline.
6. Drag movement clips and puck-event chips, or use the Inspector sliders, to
   refine timing.
7. Scrub or play the timeline in either direction.
8. Enable player or puck Glow when emphasizing a read during a presentation.
9. Collapse either side drawer, minimize the timeline, or hide all three to give
   the rink the maximum available screen area.
10. Use Pencil or Erase during playback or while paused to telestrate over the
    animation.
11. Save the current timeline to the Playbook and export JSON backups when
    moving between browsers or devices.

STORAGE AND VERSION MIGRATION

Version 5.1 uses these browser-storage keys:

botdHockeyCoachingAid.session.v5_1
botdHockeyCoachingAid.playbook.v5_1

On first launch, Version 5.1 checks the Version 5.0 keys when no Version 5.1
session exists. Version 5.0 teams, rosters, on-ice setup, movement clips, puck
route takes, drawings, display settings, Playbook entries, and custom artwork
are normalized into Version 5.1. The new appearance setting defaults to Light
and the new puck-glow profile defaults to disabled.

Version 4 turn/action-lane data is still not migrated automatically because it
cannot be translated reliably into independent continuous movement tracks and
puck-route takes. Version 4 releases remain usable separately.

A browser's local file origin and a GitHub Pages origin are different storage
locations. Export Playbook JSON before changing domains, repository paths,
browsers, or devices.

KNOWN LIMITATIONS

- Physical iPad and Apple Pencil hardware was not available during release
  validation. Tablet dimensions, touch targets, and pointer behavior were tested
  with browser emulation.
- The coach-oriented physics model is designed for tactical visualization, not
  officiating review or rigid-body scientific simulation.
- Live player collisions along curved, concurrently moving routes are sampled
  rather than solved continuously.
- Browser audio policies may require a direct user gesture before the first goal
  siren or other synthesized sound.
- Native fullscreen, vibration, file pickers, and Pencil secondary gestures vary
  by browser and operating-system support.
- Localization applies to application interface text. User-entered names,
  imported content, and browser-generated system messages are not translated.
- The Canadian-English center maple leaf is a built-in presentation overlay. A
  coach's custom center-ice image remains available beneath it and returns
  unchanged when another language is selected.

RELEASE VALIDATION

The final Version 5.1 release was exercised in headless Chromium with repeatable
checks covering:

- Version number and clean startup
- Light-mode default and Dark-mode switching
- Absence of drawer close-X controls
- Animated black selected-object ring
- Player Glow and puck Glow controls
- Player and puck glow color dialogs
- Possession-list hover, focus, selection, and rink targeting triangle
- Paused in-flight puck position and nested spin rendering
- Full-viewport timeline width and adaptive track scaling
- Left and right drawer collapse and rink expansion
- Timeline minimization and vertical rink expansion
- Swedish, Finnish, Russian, and Canadian-English interface switching
- Canadian-English “eh” text and center maple leaf
- All ten Version 5 templates
- Timeline step controls after repeated layout changes
- Version 5.0 state normalization into Version 5.1
- Desktop 1920 x 1080 rendering
- 1366 x 1024, 1024 x 1366, and 820 x 1180 responsive layouts
- No document overflow with both drawers and timeline hidden
- JavaScript syntax validation
- PNG dimensions and decoding
- ZIP root paths, file names, and compressed-data integrity

No unexpected JavaScript runtime errors occurred in the exercised workflows.
The Preview.png included in the package was captured from the final index.html,
not from an earlier development build.

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


END OF README
