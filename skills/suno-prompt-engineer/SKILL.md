---
name: suno-prompt-engineer
description: Create, rewrite, structure, diagnose, and iteratively improve Suno-ready songs, lyrics, metatags, and Style prompts. Use when Codex needs to turn a song idea, draft lyric, reference song, production brief, existing Suno prompt, generated track, or listening feedback into directly pasteable Lyrics and Style fields; guide music beginners through structure and reference selection; preserve or rewrite lyrics at an explicit edit level; analyze why a reference works without copying it; control phrasing gaps, overlapping vocals, modulation, chromaticism, melisma, arrangement, vocals, and mix; or revise a Suno result across multiple listening rounds.
---

# Suno Prompt Engineer

## Objective

Turn the user's intent into an original, coherent, singable song design and two coordinated Suno inputs. Guide beginners in plain language, preserve factual and lyrical boundaries, and iterate from the first draft through listening feedback.

Treat all Suno controls as probabilistic. Increase the intended tendency through compatible structure, wording, spacing, and metatags; never promise exact obedience, timing, notes, voice identity, or commercial rights.

## Route the request

Classify the request before responding:

- **Create**: Write a song from an idea, scene, story, purpose, or hook.
- **Rewrite**: Revise supplied lyrics at edit level L1, L2, or L3.
- **Structure**: Preserve every lyric word under L0 and add sections, phrasing gaps, and metatags.
- **Style**: Create or repair only the global Style field.
- **Analyze reference**: Extract transferable structure, lyric, hook, arrangement, vocal, and production mechanisms.
- **Audit**: Diagnose an existing Lyrics/Style pair and return corrected pasteable fields.
- **Iterate**: Convert audio or listening feedback into the smallest useful prompt change.
- **Instrumental**: Design a track without lead lyrics or unauthorized vocal elements.
- **Explore**: Offer genuinely different structural or production directions before fully writing them.

Combine modes when needed, but choose one primary mode.

## Load only the needed references

- Read [references/interaction-workflow.md](references/interaction-workflow.md) for questioning, beginner guidance, state, versioning, or listening iterations.
- Read [references/lyrics-writing.md](references/lyrics-writing.md) for original lyrics, rewrites, hooks, imagery, singability, rhyme, or special song types. For Chinese lyrics, also read [references/chinese-human-lyrics.md](references/chinese-human-lyrics.md) and apply its creation or optimization pass.
- Read [references/lyrics-formatting.md](references/lyrics-formatting.md) for section tags, local metatags, breath gaps, vocal overlap, modulation, chromaticism, melisma, or Lyrics-field formatting.
- Read [references/style-prompting.md](references/style-prompting.md) whenever creating, auditing, or revising a Style field.
- Read [references/reference-analysis.md](references/reference-analysis.md) when the user supplies or names a song, artist, audio, video, URL, or lyrics as a reference.
- Read [references/output-contracts.md](references/output-contracts.md) before finalizing a first draft, audit, rewrite, instrumental, reference analysis, or iteration response.
- Consult [references/prompt-library.md](references/prompt-library.md) only when broader vocabulary or examples are needed. Search its headings or terms instead of reading it wholesale. Treat it as an uncurated candidate library: current rules in this file and the focused references override it.

## Run the core workflow

1. Identify the task mode and the user's expertise level.
2. Extract hard constraints: purpose, language, people, facts, required phrases, forbidden content, edit permission, and reference scope.
3. Apply the beginner confirmation gate before drafting. In Create mode, if the user supplies only a broad topic, event, person, place, weather, scene, or one-line idea and has not established at least two creative anchors, do not write Lyrics or Style yet. Creative anchors include purpose/audience, core statement, emotional direction, reference song/listening feeling, style, structure preference, and vocal/production direction.
4. Present two to four concrete, plain-language directions inferred from the user's material and ask the user to choose, combine, or replace them. Include a recommended default and ask about a reference song or familiar-versus-innovative structure when those answers would materially change the result. Ask no more than three compact questions in one round.
5. Bypass this gate only when the user explicitly asks to generate immediately, such as “直接写”, “不用问”, “先出一版”, or an equivalent instruction. State the consequential assumptions before the draft. Conservative defaults may reduce follow-up questions but must not bypass the gate by themselves.
6. Build an internal brief: audience, scene, core statement, viewpoint, emotional arc, concrete imagery, hook, structure, style identity, vocal plan, and exclusions.
7. Design section functions before writing lines. Make Verse 2 add information and make the hook carry the central claim.
8. For Chinese lyrics, establish a natural narrator voice, truthful detail boundary, scene chain, and conversational core phrase before drafting. Write or revise the lyric at the authorized edit level, then run the Chinese human-writing pass without sacrificing singability.
9. Format Lyrics with structural tags, meaningful local metatags, phrase boundaries, breath space, and coordinated musical events.
10. Create the global Style from compatible genre, emotion, groove, harmony, arrangement, vocal, and mix decisions.
11. Check Lyrics and Style together for contradictions, crowding, missing rests, uncontrolled vocal layering, and unnecessary key or melodic movement.
12. Return the contract for the active mode. Keep pasteable content inside clean code blocks and explanations outside them.
13. During iteration, preserve confirmed elements, change one to three related variables, state the expected effect, and version the result.

## Apply default structure

For a beginner's first propagation-oriented draft, default to:

```text
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Pre-Chorus]
[Chorus]
[Outro]
```

Place the memorable hook inside the Chorus. Treat a repeated transition before the Chorus as `Pre-Chorus`, not `Bridge`. Add a one-time `Bridge` and `Final Chorus` only when the song needs a genuine late contrast or stronger final development. Follow a user-specified viable structure instead.

## Protect edit boundaries

- **L0 — Structure only**: Do not change, add, remove, or reorder lyric words.
- **L1 — Conservative polish**: Fix awkward wording, minor rhythm, repetition, and local rhyme while preserving narrative and core lines. Use this for an unspecified request to “optimize.”
- **L2 — Structural revision**: Reorder sections, rewrite some lines, add transitions, and strengthen the hook while preserving the core theme, facts, relationships, and protected material.
- **L3 — Deep rewrite**: Rebuild the song while preserving only the user-designated premise, facts, phrases, or brand requirements.

Never invent names, dates, product capabilities, claims, personal history, or other facts. Flag contradictions instead of silently repairing them with fabrication.

## Enforce musical clarity

- Use structural tags for every section and one to three local metatags for each meaningful state or change. Do not impose a whole-song cap of six local tags.
- Use line breaks, blank lines, punctuation, and targeted pause or instrumental tags to create breathing groups. Use spaces inside Chinese text only for intentional phrase or syllable emphasis.
- Keep a single separated lead vocal by default. Introduce backing layers only where designed; avoid continuous overlapping lines, dense ad-libs, and unrequested call-and-response.
- Keep the tonal center stable and harmony predominantly appropriate to the chosen genre. Reserve modulation and chromatic color for explicit transitions or highlights.
- Keep ordinary delivery mostly syllabic with clear diction. Reserve short melisma or vocal runs for selected phrase endings or climaxes unless the genre requires more.
- Put whole-song conditions in Style and section-specific events in Lyrics. Express an important local event in both fields only when the global arrangement must prepare for it.
- Use metatags broadly by function, not decoratively. Remove redundant or contradictory tags.

## Use references safely and precisely

Accept song titles, versions, URLs, audio, video, user-supplied lyrics, or multiple references. Separate evidence from inference. If only lyrics are available, do not claim to analyze melody, arrangement, or mix.

Translate references into abstract mechanisms such as structure, emotional curve, image strategy, hook placement, groove, instrumentation, vocal dynamics, or spatial production. Do not reproduce lyrics, melody, signature phrases, or a singer's identity-dependent voice. When multiple references are supplied, assign each a role instead of blending every feature.

## Iterate after generation

Classify feedback as lyric content, prosody, structure, breath, hook, voice, harmony/tonality, arrangement, dynamics, mix, or model variance. Recommend another generation before adding constraints when the direction is correct and the problem appears isolated or random. Modify the prompt when the same issue repeats or the prompt itself conflicts.

Track the current version, confirmed elements, current problem, retained elements, changed variables, and expected result. Output complete fields when changes are broad; output a section and Style patch only when the replacement boundary is unmistakable.

## Complete the final check

Before delivery, verify that:

- The mode and edit authority are correct.
- In beginner Create mode, the required confirmation occurred or the user explicitly authorized immediate generation.
- The selected direction and creative anchors come from the user’s answer rather than silent creative assumptions.
- The central idea, viewpoint, facts, and protected phrases remain intact.
- Chinese lyrics sound like a particular person in a particular moment rather than a generic lyrical narrator; invented fictional detail is not presented as the user's real history.
- Verse 2 advances the song and the hook is concrete, concise, and memorable.
- Lyrics contain functional structure, metatags, and breathing space without command clutter.
- Style contains a coherent style identity, emotional arc, groove, arrangement, vocal design, and mix.
- Lyrics and Style agree about sections, vocals, instrumentation, intensity, and ending.
- Modulation, chromaticism, melisma, backing vocals, and ad-libs are intentional rather than uncontrolled.
- Code blocks contain only pasteable content.
