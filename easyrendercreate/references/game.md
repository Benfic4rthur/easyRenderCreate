# Format: game

A small original game that runs in the browser from a single HTML file. The world stays the visual centerpiece; the game gives a reason to move through it. Prefer one simple, polished core loop over many half-finished mechanics.

If the person names an existing game, keep the genre and the mechanic ("dodge obstacles", "collect before time runs out") and make clear that the name, world, characters, levels, art and sound will be new. The name of the cited game never goes into the prompt.

## Format round A: the game

1. What kind of game? (exploration with a light goal: find, collect, activate (recommended when the world should shine) / reflex arcade: dodge, chase, beat the high score / puzzles that use the world itself / a race or flight along a course)
2. How does a run end, and how long is it? (win by completing the goal / lose on a mistake or when time runs out / endless, score only) and (about 2 min / 5 to 10 min / open-ended)
3. Controls? (keyboard and mouse (recommended) / keyboard only / gamepad / touch on phones)

Skip whatever the person already said.

## Format round B: how it feels to play

1. Difficulty? (relaxing / ramps up slowly (recommended) / hard from the start)
2. Feedback on actions? (strong: particles, camera shake and sound on every hit / subtle (recommended for contemplative games) / almost none)
3. Progression and interface? (levels / score with a best score saved in the browser / none, just the world) and (minimal HUD / informative HUD)

## Final detail round: threats, objects and story

Run this round after the rules round and before the summary. Ask up to three questions, skipping anything settled or irrelevant to the chosen loop. Offer only choices that fit the rules already agreed. Give each substantive option one short, concrete example with its effect so a letter is enough to decide it.

1. What can stop the player? (A) none / (B) hazards / (C) enemies / (D) both. For each approved threat, say what triggers it and what happens to the player.
2. What can the player pick up or use? (A) none / (B) pickups / (C) objects to activate / (D) both. Give each approved item or object one clear effect.
3. How much story does the game need? (A) none / (B) a one-sentence premise / (C) a premise revealed through play. Ask this only if story fits the game or the person brought it up.

If all relevant details are clear, go straight to the summary. If the person delegates a choice, choose the simplest detail that serves the loop and mark it in the summary.

## Variation in the template

The template in [prompt-template.md](prompt-template.md) applies in full, with these changes:

**Opening paragraph.** `Build a real-time {concept} browser game called {name}. It only needs to look beautiful and {core loop in a few words, e.g. let me glide through the ruins chasing a high score}.` The name is the one the person approved in the summary.

**TARGET.** On the second line, replace `scripted 60 s fly-through` with `scripted 60 s playthrough that includes the busiest moment`.

**SCENE.** For an endless game (runner, arcade), replace the `World:` line with `World: built from a fixed pool of segments recycled ahead of the player, so it never visibly repeats or ends`. Numbers, score and interface text are drawn by code, with no font files. When story is approved, use one short premise line. For a story revealed through play, state what the player discovers and how.

**CONTROLS.** Put input on the first line and use short bullets for the rules. Keep only the outcomes that apply. Add approved threat, item and object rules here. Combine related rules on one line and state cause and effect, such as `Sentries patrol the corridors. They chase on sight. Contact costs one life.` or `A fuse restores power to one checkpoint and is consumed on use.` Put explicit exclusions in CONSTRAINTS unless an existing line already states them.

```text
CONTROLS
Space to flap, Esc to pause, R to restart
- Goal: {objective and applicable win, loss or score rules}. A run lasts about {duration, if specified}.
- Difficulty: {curve}
- Feedback: {what happens on hit, miss and near-miss}
- {Score and local best saved in the browser | levels | no HUD}; start screen shows the controls
```

**VERIFICATION.** The poses become: the hero frame; the start screen; the most intense action moment; a close-up of a surface or material; the moment with the most effects on screen; the end-of-run screen. The recording is of a scripted run. Add a third item:

```text
- Playtest: scripted runs with a fixed seed reach {the agreed win, loss or score outcomes} with no soft-lock. Check that restart always returns to a clean state. If the game has a distinct challenge or interaction, verify one example. Then a separate subagent that knows only the controls plays three short runs through browser automation, with the game slowed down in test mode if it needs fast reflexes, and reports where it got confused, stuck or bored.
```

**DONE WHEN.** `DONE WHEN: all three verification gates pass. Deliver index.html, its bundle size, the performance report, the playtest report and the critic's final review.`
