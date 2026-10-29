# Securing &amp; Documenting the Scene

A browser-based crime scene documentation lab for high school Forensic Science.
Students secure a scene, mark evidence, and photograph it under enforced forensic
procedure. Nothing is collected — documentation is the whole competency.

Runs on school Chromebooks. No install, no build step, no dependencies beyond
three.js from a CDN. Open `index.html` and it runs.

**Live:** https://talmond-source.github.io/forensics-scene-lab/

## What the lab enforces

**Securing, before entry.** Four situational decisions covering scene control, perimeter,
approach path, and the scene entry log. Wrong answers are refused with the reasoning
rather than simply marked wrong. Committing all four reveals the common approach path
on the floor.

**The approach path.** Sterile zones sit over the areas where transfer evidence is most
likely. Stepping into one is logged with a timestamp and costs points.

**Overall photographs.** Four corners, each requiring the student to actually stand at that
corner with enough of the room in frame. These hard-lock the moment any evidence marker
is placed — the undisturbed record has to exist first, and after that it cannot.

**Marking.** Numbered markers auto-associate with evidence within reach. Strays are logged.

**Midrange and close-up.** Every frame is validated against the scene geometry before it
enters the record: subject in frame, clear line of sight, correct distance for the shot type,
centred, square to flat surfaces, correctly lit, marker visible. Rejected frames are shown
back to the student alongside the forensic reason they failed.

## Student deliverable

A scene documentation record containing every accepted photograph, every rejection and its
reason, the contamination log, and a score across securing, overall photographs, marking,
photography, findings and interpretation. Exports as CSV.

## Teacher options

| URL parameter | Effect |
| --- | --- |
| `?hints=1` | Rings over every interactable — differentiation for students who would otherwise spend the period hunting pixels |
| `?debug=1` | Live readout of hotspot distances and aim state |

A **Quality** toggle in the toolbar switches shadows and pixel ratio for weaker hardware.
No pedagogical difference between the two settings.

## Authoring a new case

Everything case-specific lives in the `CASE` object at the top of the script: the securing
decisions, the four overall camera positions, the evidence items with their anchor
coordinates and per-item validation rules, the sterile zones, the findings and the
interpretations. The validation engine, marker system and scoring read from that data and
need no changes.

Note that a new case's solution lives in this same block, so keep that in mind before
sharing the source with a class.

## Roadmap

The room is built geometry. The validation layer reads from world coordinates, so a
Gaussian splat capture of a physically staged room can replace the geometry without
touching the evidence anchors, the photographic checks, or the scoring.
