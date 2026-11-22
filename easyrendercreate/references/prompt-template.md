# Final prompt template

Use the same sections, order, headers and terse style, with the format changes below. Aim for 30 to 45 lines. Keep shorter briefs short and use extra lines only for actual requirements.

Follow each format's file (scene.md, game.md, video.md). CONTROLS describes input or automatic playback for a scene, includes the rules of play for a game, and becomes SEQUENCE for an exported video.

## Template

```text
Build a real-time {adjectives + concept} that runs in the browser. It only needs to {what matters, e.g. look beautiful} and {the experience, e.g. let me fly a free camera through it}.

PRIORITIES (in this order when they conflict)
1. {Visual quality}
2. {Stable frame pacing at the target spec}
3. {Small bundle size}

CONSTRAINTS
- No 3D engines or rendering libraries (Three.js, Babylon.js or similar).
- Rendered with WebGPU.
- Fully procedural: no texture, model or sound files. Ship a single self-contained index.html and report its minified size.
- No JS allocations per frame (avoid GC stutter); preallocate every buffer.

TARGET
- {OS}, {browser}, {GPU}, {CPU}, {refresh} Hz display
- {W×H} at native resolution. Average GPU frame time ≤ {avg} ms and no single frame above {worst} ms over a scripted 60 s fly-through.

SCENE
- {scene items, see the rules below}
- World: bounded, but its edges can't be seen from the starting area

CONTROLS
{one line describing the chosen controls or automatic playback}

VERIFICATION
- Visual critic: a separate subagent that only ever sees your renders, never your code or reasoning. Hand it 6 fixed camera poses rendered at {W×H} in GPU-accelerated {browser}, plus a short recording of the fly-through so it can spot shimmer, aliasing, popping and banding. It answers with concrete defects in priority order. Keep iterating until nothing it reports is worse than "minor".
- Performance: GPU timestamp queries plus a frame-time log of the scripted fly-through. Report the average, 99th percentile and maximum.

DONE WHEN: both verification gates pass. Deliver index.html, its bundle size, the performance report and the critic's final review.
```

## Filling rules

**Explicit exclusions.** Write the person's exclusions as short directives, such as `No creatures or on-screen interface.` Put them in CONSTRAINTS unless the format section already states them explicitly. Remove conflicting defaults, examples and requirements from the whole prompt, including verification. Avoid inventing exclusions for features that were never discussed. If a veto conflicts with a defining requirement of the chosen format, clarify that conflict before delivery.

**Opening paragraph.** Two sentences. The first says what it is, with two or three mood adjectives ("a real-time dreamlike desert canyon at dusk"). The second says what matters and how it is experienced.

**PRIORITIES.** Three short items in the order the person chose. Smoothness first reads: `1. Stable frame pacing at the target spec 2. Visual quality 3. Small bundle size`.

**CONSTRAINTS.** Start with the four technical lines and add any project-specific rules:
- Three.js allowed: replace the first line with `Three.js is the only library allowed, inlined into the file; no other engines.`
- No sound: `no texture or model files`. With sound, keep `no texture, model or sound files` (the sound is synthesized).
- Extra technical rules the person asked for become one more line in the same tone (e.g. `Must also run on recent phones: scale resolution first, then draw distance.`).

**TARGET.** Follow "TARGET lines" in [budgets.md](budgets.md).

**SCENE.** A flat list with no sub-headings, usually 7 to 10 items. Each item is one dense line: the element, then its color, light, scale and motion details separated by commas. Skip categories that do not fit the brief. Use this order:
1. The concept's signature element (what fills most of the hero frame).
2. Atmosphere: fog or absorption, color near → color far.
3. Light effects: rays, glow, reflections, sky or surface.
4. Terrain and structures: formations, arches, caves, floating things.
5. Surfaces, vegetation and materials, with their colors.
6. Life and motion: creatures, flocks, particles, flows (`Animated life: …`).
7. Landmarks: the unique pieces (`Set pieces: …`).
8. Sound, if any (`Procedural ambient sound: …`).
9. The person's references, if any (see [user-references.md](user-references.md)).
10. World boundary or extent, if relevant. Default to the `World: bounded, …` line.

**CONTROLS.** For scenes, use one line for the chosen controls or playback, including any approved interaction extras. For games, follow the format file.

**VERIFICATION.** Keep both checks. Follow the format's verification instructions and "Critic and capture by agent" in [budgets.md](budgets.md). After "6 fixed camera poses", add the short list of poses in parentheses, starting with the hero frame. Use only views and checks that apply to the chosen scope.

**DONE WHEN.** One line, as in the template.

**Language.** If the prompt is in another language, translate everything, headers included (in Portuguese: PRIORIDADES (nesta ordem quando houver conflito), RESTRIÇÕES, ALVO, CENA, CONTROLES, VERIFICAÇÃO, PRONTO QUANDO).

## Filled-in example (interactive scene)

Use it as a ruler for form, density and length, never as content. The person's concept always rules.

```text
Build a real-time dreamlike chain of floating islands above a sea of clouds at sunrise that runs in the browser. It only needs to look beautiful and let me fly a free camera through it.

PRIORITIES (in this order when they conflict)
1. Visual quality
2. Stable frame pacing at the target spec
3. Small bundle size

CONSTRAINTS
- No 3D engines or rendering libraries (Three.js, Babylon.js or similar).
- Rendered with WebGPU.
- Fully procedural: no texture, model or sound files. Ship a single self-contained index.html and report its minified size.
- No JS allocations per frame (avoid GC stutter); preallocate every buffer.

TARGET
- Windows 11, Chrome, RTX 4060, 144 Hz display
- 1920×1080 at native resolution. Average GPU frame time ≤ 11 ms and no single frame above 16.7 ms over a scripted 60 s fly-through.

SCENE
- Twenty to thirty floating islands, from car-sized boulders to masses 300 m across, with jagged undersides of layered rock
- Warm haze: peach near the camera → cool lavender in the distance
- Low orange-gold sun raking long shadows, soft light shafts through the gaps between islands
- Thin stone bridges and broken arches linking some islands; waterfalls pouring off the edges and dissolving into mist
- Wind-combed yellow-green grass, pale lichen and exposed strata on the cliffs, crisp edges catching the sun
- Animated life: flocks of small birds banking in loose formations, drifting pollen glinting in the sun, the cloud sea rolling slowly below
- Set pieces: a ring of tilted 40 m monoliths on the largest island, an upside-down tree hanging under another
- Procedural ambient sound: wind, distant water, soft birdsong
- World: bounded, but its edges can't be seen from the starting area

CONTROLS
WASD move, mouse look (pointer lock), Q/E up/down, Shift to accelerate

VERIFICATION
- Visual critic: a separate subagent that only ever sees your renders, never your code or reasoning. Hand it 6 fixed camera poses (into the sun through the monolith ring, wide view from the start, the upside-down tree up close, straight at the sun, grass and cliff close-up, the densest flock over the clouds) rendered at 1920×1080 in GPU-accelerated Chrome, plus a short recording of the fly-through so it can spot shimmer, aliasing, popping and banding. It answers with concrete defects in priority order. Keep iterating until nothing it reports is worse than "minor". Make sure the captures come from real GPU rendering, not a software fallback.
- Performance: GPU timestamp queries plus a frame-time log of the scripted fly-through. Report the average, 99th percentile and maximum.

DONE WHEN: both verification gates pass. Deliver index.html, its bundle size, the performance report and the critic's final review.
```
