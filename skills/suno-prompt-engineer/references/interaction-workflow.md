# Interaction and Iteration Workflow

## Contents

1. Collaboration level
2. Ask or generate decision
3. Conversation state
4. First draft
5. Listening feedback
6. Regeneration versus revision
7. Minimal iteration
8. Completion

## Choose the collaboration level

### Beginner guidance

Use plain language when the user offers only a theme, vague listening words, or a reference. Ask at most one to three high-value questions at a time. Offer a default rather than testing BPM, key, meter, or production knowledge.

Prioritize:

1. Who or what is the song for, and where will it be used?
2. What is the one statement the song must express?
3. Is there a reference song or desired listening feeling?
4. Does the user prefer a familiar propagation-oriented structure or an innovative one?

Explain the default as story Verse → emotional transition → memorable Chorus, not only as technical labels.

### Beginner confirmation gate

In Create mode, treat a topic as source material rather than a complete creative brief. A request based only on weather, a place, an event, a person, a scene, or one broad sentence must pause before Lyrics and Style generation unless the user explicitly requests an immediate draft.

Count the following as creative anchors:

- Purpose or audience.
- Core statement or intended takeaway.
- Emotional direction or listening feeling.
- Reference song.
- Style direction.
- Familiar or innovative structure preference.
- Vocal or production direction.

If fewer than two anchors are established, ask one confirmation round. Do not use inferred defaults to skip it.

Translate the material into two to four distinct, concrete choices. Each choice should describe a felt scene, emotional movement, or listening experience—not a list of technical parameters. Mark one sensible default, and let the user choose, combine, or describe another direction.

Example for a weather-based request:

```text
我查到今天北京白天闷热、多云，夜间转晴。这个天气可以写成三种不同方向：

A. 城市轻快（推荐）：白天的热退下去，晚风让人重新松一口气。
B. 温柔治愈：把天气变化写成一个人从疲惫到被安慰。
C. 夜行情绪：保留闷热和霓虹感，写一点克制的孤独。

你更想选哪一个，还是组合两个？有参考歌曲可以告诉我；结构如果没有偏好，我会使用容易听懂和记住的常规结构。
```

Do not ask beginners to choose BPM, key, meter, chord vocabulary, vocal register, or mix terminology unless they volunteer that level of control. Infer those after the user confirms the audible direction.

### Collaborative creation

Show a short brief or structural recommendation when the user wants to discuss direction. Confirm only decisions that change the output materially.

### Professional direct mode

Use supplied structure, tempo, harmony, instrumentation, vocal, and production requirements. Do not re-ask known information. Ask only about a blocking contradiction.

## Decide whether to ask or generate

Ask first when:

- The beginner confirmation gate applies.
- A core fact, audience, relationship, use case, reference version, or rewrite permission cannot be inferred safely.
- Two requirements conflict materially.
- Different answers would create fundamentally different songs.
- The user explicitly requests planning before writing.

Generate immediately when:

- The user says “直接写,” “先出一版,” or “不要问.”
- At least two creative anchors are established and the remaining brief is coherent enough.
- Missing details have conservative compatible defaults after the beginner confirmation gate has been satisfied or explicitly bypassed.
- The request is an unambiguous format conversion, structural pass, local repair, or Style-only task.

State a consequential assumption in one sentence before the deliverable. Do not add a long preamble.

When the gate applies, the current-turn deliverable is the choice set and confirmation question—not provisional Lyrics or Style. Do not append a complete song “for convenience,” because that defeats the confirmation step.

## Maintain conversation state

Track internally:

- **Fixed facts**: people, brands, places, dates, claims, use case, protected and forbidden content.
- **Confirmed creative decisions**: theme, viewpoint, structure, hook, style, voice, and emotional curve.
- **Reference profile**: sources, assigned dimensions, transferable mechanisms, and excluded imitation features.
- **Version state**: current version, changes, locked elements, unresolved questions, and next listening test.

When a core direction changes, create a new branch or version and say so instead of silently overwriting the prior direction.

## Deliver the first draft

Complete an internal brief, section blueprint, lyric, formatting pass, Style design, and cross-field check before delivering V1. Do not leave obvious structural, factual, breath, tag, or conflict problems for the user to discover.

## Receive listening feedback

Accept audio, a Suno link, video, text feedback, timestamps, multiple generations, highlighted lyric sections, or a comparison reference.

If audio is available, analyze by section and timestamp. If only text is available, state that the diagnosis is based on the user's description.

Classify the issue:

- Lyric content or concreteness.
- Prosody, density, pronunciation, or singability.
- Structure or energy timing.
- Breath, overlap, or phrase separation.
- Hook memorability.
- Vocal timbre, register, force, melisma, or ad-libs.
- Tonality, modulation, chromaticism, or melodic stability.
- Instrumentation or arrangement density.
- Dynamic contrast.
- Mix, reverb, width, vocal position, or low end.
- Model variability.

## Distinguish regeneration from revision

Recommend another generation before changing the prompt when the direction is correct and the issue is isolated: one unusual ornament, one pronunciation error, one accidental texture, or an untested first result.

Revise when the same fault recurs, the structure repeatedly fails, vocals consistently overlap, melisma or modulation remains excessive, the Chorus repeatedly lacks impact, breathing is absent from formatting, the fields conflict, or the user's goal changes.

Do not pile on negative constraints after one random result.

## Run a minimal iteration

1. Record the current version.
2. State the observed problem.
3. Lock the confirmed elements.
4. Select one to three related variables.
5. Modify the smallest clear replacement boundary.
6. State the expected audible effect without promising success.
7. Request or await the next generation result.

Example state:

```text
Current: V2
Keep: theme, hook, Verse instrumentation, lead timbre
Problem: Chorus lacks impact; Verse 2 has no breath gap
Change: Chorus drums and width; one Vocal Rest and Instrumental Fill in Verse 2
Expected: stronger section contrast and clearer phrase separation
```

Output complete fields when changes are broad. Output one section plus a Style patch only when the replacement location is unambiguous.

## Finish the project

Finish when the user accepts the lyric, hook, structure, breath behavior, style direction, and coordinated Lyrics/Style fields, or when remaining variance is clearly identified as generation randomness or post-production work.

Return only the final title, version, Lyrics, Style, and essential generation note. Do not repeat the entire revision history.
