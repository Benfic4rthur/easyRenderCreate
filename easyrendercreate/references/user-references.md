# The person's references and information

The person may send material at any time: images, links, texts, scripts, brand documents, palettes, lists of requirements. This file explains how to turn that material into concrete direction for the agent.

## On receiving material

1. Reply in a few lines with what you took from each item (see below). Ask only if something is ambiguous ("is image 2 about the light or the place?").
2. Use the material to shorten the interview: whatever it already answers is not asked again.
3. Give each **image** a label (`ref-01-light.jpg`, `ref-02-dunes.jpg`…), in the prompt's language. The labels go into the prompt, and the person puts the files in a `references/` folder next to it.
4. Text pasted into the chat (a script, a story, a brief) does not become a file. What matters goes straight into the prompt, condensed and in the prompt's language.

## What to take from each kind

- **Image**: palette (3 to 5 colors, with approximate hex values), direction and quality of the light, composition, scale, materials, atmosphere, what moves or suggests motion. Also say what **not** to take (a character, a third-party logo, an artist's exact style).
- **Link**: if your environment can open pages, open it and summarize it. If it can't, ask for a screenshot or a two-line description.
- **Text, script or story**: facts, names, order of events, tone, required elements. In a video, the script becomes the basis of SEQUENCE. In a game, it becomes the goal and the world.
- **The person's brand colors**: ask where they should appear, with suggestions (only in light sources / on one accent element / at the end of the video). They go in as a SCENE item.
- **The person's logo**: recommend redrawing it in code as a vector shape, because that keeps everything procedural. If the person prefers the original file, it is embedded in the HTML itself, and the procedural line in CONSTRAINTS gets the exception: `The only bitmap allowed is the brand logo (references/logo.png), embedded in index.html as a data URI.` Say where and how large it appears, and ask for contrast with the background.
- **List of requirements** (length, format, deadline, platform): goes straight into CONSTRAINTS, TARGET or the format section.

## Third-party works

References to films, games, illustrations or other people's photos are for feeling, palette, light, scale and genre mechanics. The prompt never asks to copy characters, recognizable settings, logos, music or a living artist's signature style, and never uses those works' names. Describe what is wanted in your own words.

## How references appear in the template

The template gets no new section. References go in like this:

- **SCENE**: one item, before the `World:` line. Example: `Look from references/ref-01-dusk.jpg: palette of slate blue #2c4a63, rust #b5532a and pale fog #d9dde0, low side light; ignore its buildings`.
- **VERIFICATION**: in the critic item, after the poses, add `Also hand it the images in references/ to judge whether light, palette and mood match them, without copying them.`
