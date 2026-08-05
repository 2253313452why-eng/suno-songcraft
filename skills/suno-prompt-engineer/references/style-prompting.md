# Style Prompting 2.0

## Contents

1. Scope
2. Information slots
3. Priority and conflict handling
4. Beginner translation
5. Prompt shapes
6. Iteration
7. Quality check

## Keep Style global

Describe the whole song's style identity, emotional curve, tempo and groove, harmony, instrumentation, arrangement, vocal baseline, spatial production, and necessary exclusions. Do not include full lyrics, per-line directions, explanations, or visual composition.

Use natural concise English. Treat the template as a variable skeleton rather than a mandatory paragraph.

## Fill the information slots

### Style identity

Choose one primary genre and normally no more than two supporting influences. State how they combine. Add an era or production tendency only when it matters.

Prefer:

```text
Mandopop ballad with subtle contemporary R&B influence
```

Avoid undirected lists of many genres.

### Emotional design

Choose one core emotion, one supporting emotion, and a trajectory. Prefer section-aware change over synonym stacking:

```text
intimate and reflective in the verses, gradually becoming hopeful and uplifting in the chorus
```

### Tempo and groove

Describe slow, medium, or fast motion; meter; groove; and drum/bass behavior when useful. Infer from the scene and reference when the user does not know BPM.

```text
a steady mid-tempo 4/4 groove with restrained drums and a gently driving bass line
```

Do not invent an exact BPM unless it improves the task.

### Tonality and harmony

Describe major/minor tendency, modal color, harmonic warmth, complexity, stability, or Chorus lift. Do not force an exact key when unknown.

```text
minor-leaning harmony with a warmer lift in the chorus
```

Default to a stable tonal center and genre-appropriate predominantly diatonic behavior. Allow modulation or chromatic color only as an intentional structural event.

### Instruments and arrangement

Give instruments a role, technique, entry point, or dynamic function. Cover opening, support, rhythm, low end, buildup, climax, and ending as needed.

```text
It opens with close-miked piano and a sparse ambient pad. Fingerpicked acoustic guitar enters in the verse, followed by restrained drums and warm strings that widen into the chorus.
```

### Vocal design

Describe lead organization, range or register if useful, timbre, Verse delivery, Chorus delivery, diction, backing layers, and emotional control. Do not invent detailed gender, age, or identity when unspecified.

```text
A warm, clear lead vocal uses intimate conversational phrasing in the verses, controlled belting in the chorus, and restrained harmonies only in the final refrain.
```

Control crowding explicitly when relevant: single lead, audible breath gaps, no overlapping lines, restrained melisma, and limited ad-libs.

### Space and mix

Use concrete production relationships: vocal-forward, close or distant, dry or reverberant, stereo width, separation, low-end control, dynamics, polished or organic texture.

```text
Keep the lead vocal forward and intimate, with clear instrument separation, moderate stereo width, controlled low end, and restrained plate reverb.
```

### Exclusions

Add only exclusions that address a real risk. Avoid a default wall of `no...` clauses. For instrumental work, define exactly whether lead voice, speech, chant, choir, or vocal samples are excluded.

## Resolve conflicts by priority

Use this order:

1. Explicit user requirements.
2. Protected phrases, facts, and exclusions.
3. Confirmed reference analysis.
4. Lyrics content and structure.
5. Use case and audience.
6. Genre conventions.
7. Conservative defaults.

Convert intentional contrasts into time-based development:

```text
sparse and intimate in the verses, expanding into a wide full-band chorus
```

Do not flatten contradictions such as minimal/full, dry/cavernous, clean/heavily distorted, whispered/powerfully belted, or stable/frequently modulating into simultaneous global requirements.

## Translate beginner language

Interpret vague words as questions about musical variables:

- **好听**: melody, timbre, groove, emotion, or production?
- **抓耳**: hook, repetition, rhythm, title line, or Chorus entry?
- **高级**: restraint, harmony, tone selection, space, dynamics, or mix?
- **有氛围**: space, texture, tempo, harmony, or ambience?
- **很炸**: drums, low end, dynamic contrast, vocal layers, or delivery?
- **治愈**: warm timbre, stable groove, brighter harmony, or intimate voice?
- **电影感**: narrative development, orchestral layers, dynamic range, or depth?

Ask one discriminating plain-language question only when the answer materially changes the result.

## Use prompt shapes

### Standard song

```text
A [primary style] song with [emotion and trajectory], driven by [tempo, meter, or groove]. It opens with [opening design], while [instruments and roles] shape the arrangement toward [climax]. The lead vocal has [timbre], using [Verse delivery] in the verses and [Chorus delivery] in the chorus, supported by [backing design]. Keep the mix [space and production], with [necessary constraints].
```

### Concise song

```text
[Style and influence], [emotional curve], [tempo and groove]. [Core instrumentation and arrangement]. [Vocal design]. [Mix and essential exclusions].
```

### Instrumental

```text
A [style] instrumental with [emotion and development], driven by [tempo and groove]. It opens with [instrument], while [later instruments and arrangement]. Keep the production [space and mix]. Instrumental only, with [precise vocal exclusions].
```

### Duet

Define the two roles, contrasting timbres, section ownership, call-and-response only if desired, shared Chorus, and final convergence.

### Rap

Prioritize beat type, speed, drums, low end, flow density, articulation, Verse/Hook contrast, ad-libs, and vocal position.

Use approximately 40–70 English words for a simple concise prompt, 70–120 for the standard default, and 120–180 only for complex arrangements. Treat these as editing heuristics, not platform limits.

## Convert references into Style

Translate the reference into abstract attributes rather than naming an imitation target:

```text
A restrained piano-led pop ballad with conversational verses, a gradually rising pre-chorus, a title-centered chorus, warm string support, controlled emotional belting, and a clean vocal-forward mix.
```

If the user selects only structure or emotion from the reference, do not import its voice, instrumentation, or mix.

## Iterate minimally

Keep confirmed style identity and stable variables. Change one to three related variables per round. When the Chorus lacks impact, adjust Chorus drums, low end, harmonies, vocal intensity, or width without automatically changing genre, tempo, lyrics, and ending.

Recommend another generation before prompt expansion when the direction is correct and the fault appears isolated.

## Check Style

- Keep one clear primary genre.
- Express emotion as a trajectory.
- Make groove fit the use case.
- Avoid unsupported exact BPM, key, register, or identity.
- Give instruments roles or entry points.
- Give the arrangement an energy curve.
- Specify timbre, delivery, diction, and layer behavior where useful.
- Make mix language concrete.
- Use only necessary exclusions.
- Align with Lyrics tags and section events.
- Keep tonal movement and vocal ornament intentional.
- Remove redundant synonyms and decorative vocabulary.

