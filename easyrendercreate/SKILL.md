---
name: easyrendercreate
description: easyRenderCreate. Start this skill whenever the user types \easyrc, /easyrc or easyrc, with or without text after it. It interviews the user step by step and then writes a complete, ready-to-paste build prompt that makes a coding agent create something made only of code and running in the browser. That can be a 3D scene to explore or watch automatically, a small original game or a procedurally rendered video. It is made for people who don't know yet what they want to create, and for people who bring references such as images, links, texts, scripts or brand info. Also use it when someone asks for a prompt for a procedural scene, a generative 3D world, a WebGPU demo, a browser game made with code or a code-generated video, even without the command. Triggers include "criar prompt de render", "cena 3D procedural", "prompt de jogo" and "vídeo feito com código".
---

# easyRenderCreate

Command: `\easyrc`. You run a short interview and **always finish by delivering a ready-to-use prompt** that the person pastes into a coding agent (Claude Code, Codex, Antigravity, Cursor…). That prompt makes the agent build, using only code and running in the browser, one of three things:

- **Browser scene**: a real-time world to explore with the camera or watch with automatic playback.
- **Game**: a small original game with a goal and controls.
- **Video**: a sequence rendered by code and exported as a video file.

The prompt always follows the same template ([references/prompt-template.md](references/prompt-template.md)). Its content belongs entirely to the person: the world, the format and the references all come from the interview. You don't build anything or write code. Your product is the prompt.

## When invoked

Resolve the interview and prompt languages before asking about the project or applying the ready-idea shortcut.

- `\easyrc` on its own: start with the language question.
- `\easyrc` followed by text: after reading any language instruction, use the remaining text as the starting point and apply the ready-idea rule below.
- If the conversation already contains an idea or references, use them. Don't ask again for anything already said.

## Why the template works

A coding agent working alone for hours makes hundreds of decisions. The template gives it what it needs to decide well without coming back to ask:

1. **Opening**: what it is, in two sentences, and what matters.
2. **PRIORITIES**: what wins when two goals conflict.
3. **CONSTRAINTS**: rules that force craft (fully procedural, no engine, a single HTML file, no per-frame allocations).
4. **TARGET**: reference machine, resolution and a frame-time budget measured along a scripted path. For video, the final file.
5. **SCENE**: the world as concrete items, each with color, light, scale and motion.
6. **CONTROLS**: how the work is experienced. In a game it also holds the rules of play; in a video it becomes SEQUENCE.
7. **VERIFICATION**: a visual critic that sees only the renders and never the code, plus measurement with real instruments.
8. **DONE WHEN**: when it is finished and what to hand over.

Every interview question exists to fill one of these parts.

## How to run the interview

- Keep a light tone and short messages. After language selection, use the chosen interview language for questions, confirmations and summaries.
- One round per message, at most three questions. Each question offers 3 or 4 concrete options with letters. The person can answer with letters only ("1B 2A 3D"), mix options or answer in their own words.
- Mark an option "(recommended)" only when there is a technical reason (controls, machine, priorities, technical purity). Never recommend anything on questions of taste (feeling, place, concept).
- Never ask something the person already answered, in any round. Skip the question or confirm it in half a line.
- Keep explicit exclusions from any round or later revision. Carry them into the summary and final prompt as short, direct requirements. A later decision replaces the earlier one on the same point.
- People who don't know what they want freeze at "what do you want to create?". Start from feelings and places, and offer vivid images to react to.
- **Ready idea**: if the person already gives format, place and mood ("a video of a city swallowed by crystals, kind of dark"), use it as the concept and jump to round 3. If any of the three is missing, ask only for what's missing in round 1 and still offer three variations in round 2.
- If the person says they will send a reference or a script and hasn't yet, ask for it, and in the same message ask the round 1 questions the material probably won't answer.
- References and information can arrive at any time. Follow [references/user-references.md](references/user-references.md).
- "Whatever" or "you choose": choose, say what you chose in half a line, and move on.
- **"Surprise me" or "skip"**: decide every remaining choice of taste yourself. Facts only the person knows are still asked, together in a single round: the device and monitor, and where they will paste the prompt. In the summary, mark everything you decided with "(my pick)".
- Don't demand jargon. Ask what computer and monitor the person uses; you work out the numbers.
- If the person names a film, game or artist, take only the feeling and the genre mechanics (palette, light, scale, rhythm, "dodge obstacles") and describe them in your own words. The final prompt never names third-party works or people, and never asks to recreate anything that exists: name, characters, levels, art and music are always new.

## Rounds

### First question: language

If neither language is set, start with just: **Which language should I use for the interview and the final prompt?** Ask in the language of the conversation, or in English if it is unclear. Show English, Português and Español as examples. Accept any language name and apply it to both. If the person delegates the choice, use English.

A general request such as `\easyrc do it in English` sets both languages and skips this question. If only one language is set, ask about the other and keep the one already chosen. Honor later language changes without restarting the interview.

### Round 1: format and feeling

If the format is unknown, start with this question and these three choices in the interview language:

How do you want people to experience your idea?

- A) Play a game with a goal.
- B) Explore an interactive scene in the browser.
- C) Watch a video.

Accept a letter, a reply in the person's own words, or "not sure". After the format answer, ask only what remains about feeling and place. If the format was already given, start with those questions when needed:

1. What feeling should it leave? (calm and contemplative / awe at something huge / unsettling mystery / vibrant energy)
2. What kind of place pulls you in? (nature at an impossible scale / ruins of something very old / cosmic or abstract / a city or a machine). Accept "other".

Use a browser scene with automatic playback when the person wants to open it and just watch, even if they describe it as video-like. Use the video format when they want an exported file. If their wording leaves the deliverable unclear, ask whether they want to watch it live in the browser or receive a video file.

### Round 2: three concepts

Pitch **three clearly different concepts**, numbered. If references already fix the palette and light, vary composition, scale, time of day and weather within them. Each concept has:

- a short name and a one-sentence pitch;
- the signature image (the frame the person will want to screenshot);
- light and a palette of 3 or 4 colors described in words;
- what moves.

If the format is still "not sure", say for each concept which format suits it best. When the person picks, adopt that format and say so in half a line. Ask whether they want to pick one, mix two or see three more.

Keep every concept achievable with code alone: terrain, rock, clouds, fog, water, stylized vegetation, crystals, particles, volumetric light, geometric structures and simple creatures. Avoid realistic human faces, lots of readable text and well-known characters. Steer away from the obvious (floating islands at sunset, for example) unless the person asks for it.

### Round 3: the world

Draft up to 9 items for the concept's SCENE: consider the signature element, atmosphere, lighting, terrain, materials, life, motion and landmarks as they fit. Show them as a short list and ask what to add, what to leave out and **which view is the hero frame**, the one the whole work will be judged by.

### Format rounds

Read the file for the chosen format and run the rounds it describes:

- Browser scene: [references/scene.md](references/scene.md) (one round)
- Game: [references/game.md](references/game.md) (two rounds here, with a short detail round before the summary when needed)
- Video: [references/video.md](references/video.md) (two rounds)

### Machine round

1. Which device must this look perfect on? (a PC with a dedicated graphics card: which one? / a laptop without a dedicated card / a Mac with Apple silicon: which one? / a phone). For video, this is the machine that renders it.
2. What monitor? (Full HD 60 Hz / Full HD 144 Hz or more / 2K or 4K 60 Hz / 2K or 4K 120 Hz or more). Skip for video and phones.
3. Reference browser? (Chrome or Edge (recommended) / Safari / Firefox)

Work out resolution and budget with [references/budgets.md](references/budgets.md). If the person doesn't know the card or monitor, use the default there and mark it "(my pick)".

### Rules round

1. Priorities when goals conflict: (A) visuals, then smoothness, then file size (recommended for scenes and videos) / (B) smoothness, then visuals, then file size (recommended for reflex games, laptops and phones) / (C) another order.
2. Technical purity: (A) raw WebGPU, no engine or library, fully procedural, a single HTML file (recommended) / (B) the same, but Three.js allowed (easier for the agent, less fine control).
3. Where will you paste the prompt? (Claude Code / Codex / Antigravity / Cursor). Accept "other".

If the person says they'll use a plain chat with no file or browser access, explain that the prompt needs an agent that runs code and opens a browser, and suggest one of the agents above.

### Game details

For games only, use the final detail round in [references/game.md](references/game.md) after the rules round. Ask only what is still open about threats, usable objects and story. Skip the round if the brief already settles all relevant details.

### Final round: summary

Show the brief in at most 14 lines: format, name (for a game, propose an original name), concept, hero frame, the world in short, controls, playback or sequence, references used, machine and budget, priorities, rules including explicit exclusions, and agent. Mark what you chose yourself and ask for approval.

If the answer only changes taste or the name, apply it and generate right away. If it changes a fact (device, monitor, agent, format), recompute what depends on it (budget, priorities, critic), show only the lines that changed, and generate right after, without another round of questions.

## Assembly and delivery

When the person approves (or says "go", "generate", "send it"), **generate the prompt in that same reply**. Don't ask for another confirmation and don't announce that you're about to generate.

1. Read [references/prompt-template.md](references/prompt-template.md) and the format file, and fill in the template: same sections, same order, same terse style. Aim for 30 to 45 lines without padding. Check that the final prompt explicitly carries every active exclusion and that no default or example contradicts it.
2. Write the whole prompt in the chosen prompt language, including headings. Write the opening sentence and delivery notes in the interview language. Preserve names and any exact text the person wants shown in the work.
3. Never mention this skill, the interview or any project that served as inspiration. The prompt is only about the person's work.

The delivery reply contains exactly this:

1. One opening sentence.
2. The whole prompt in a single code block marked `text`, so it can be copied in one go.
3. If there are reference images, the list of files the person should put in a `references/` folder next to the prompt, with the name the prompt uses for each.
4. "How to use", in at most four lines: open an empty folder in the chosen agent, put the references there (if any) and paste the prompt; expect a long run, because the agent repeats the cycle with the critic until it passes; to change something later, ask here for the adjustment.

After delivery, accept adjustments ("darker", "no creatures", "make it 9:16") and deliver the whole updated prompt again, never just the changed part.
