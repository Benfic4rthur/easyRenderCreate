# Format: browser scene

A real-time world to explore or watch in the browser, with no game goal. Both viewing modes use the sections in [prompt-template.md](prompt-template.md).

## Format round

1. How do they want to see the scene? (free flight: WASD + mouse, Q/E up and down, Shift to speed up (recommended) / automatic playback / orbit around a point / walk on the ground). With automatic playback, accept a fixed view or a moving camera. Make the default choice fit the scene and show it in the summary. Include manual takeover only if requested.
2. For interactive viewing, offer extras: procedural ambience / start menu with a loading screen / phone touch controls / terrain collision. For automatic viewing without controls, offer procedural ambience or an automatic loading screen if relevant. Skip choices already settled by the brief.

Mention in half a line that each extra costs build time and performance.

## Where each answer goes in the template

- Interactive viewing: name the movement in the opening and specify the input in CONTROLS. For a guided tour with manual takeover, describe both the route and the takeover input. Use the tour for the existing performance run.
- Automatic viewing without controls: say in the opening that it plays on its own in the browser. Keep CONTROLS as one line, e.g. `Start automatically when ready. Slowly orbit the main structure, then hold the final view. No viewer controls or start button.` For a fixed view, state the framing and what animates. Loop only when requested or when the concept calls for a continuous loop. Keep the world animating after a camera route ends unless the person requests a different ending.
- Sound: a SCENE item. In interactive mode, procedural ambience starts on the first click. In automatic mode without controls, keep the scene playing silently whenever the browser blocks audio autoplay. Never require a click to begin the visuals.
- Menu, touch, collision: on the CONTROLS line after a semicolon (`…, Shift to accelerate; start menu with a loading bar; touch steering on phones; solid terrain you slide along`).
- Touch on phones also adds the graceful-degradation line to TARGET.
- For automatic viewing without controls, replace the scripted fly-through in TARGET and VERIFICATION with a 60 s recording and performance run of the actual playback. Check that a fresh page starts without input and plays through the chosen ending or loop. Capture the six review views separately if the public playback uses a fixed camera.

## Verification poses

Six: the hero frame; a wide view from the starting point; a landmark up close; looking into the main light; a close-up of a surface or material; the densest area.
