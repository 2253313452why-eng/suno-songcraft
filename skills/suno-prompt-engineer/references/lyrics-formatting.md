# Lyrics Formatting, Metatags, and Vocal Control

## Contents

1. Field responsibilities
2. Tag system
3. Breath and spacing
4. Vocal overlap
5. Tonality and ornamentation
6. Formatting examples
7. Reliability rules

## Separate the two fields

Put lyrics, section boundaries, local performance states, rests, and section-specific events in Lyrics. Put whole-song genre, emotion, groove, harmony, instrumentation, vocal baseline, mix, and exclusions in Style.

Express a major local event in both places only when Style must prepare the global arrangement for it, such as one controlled final-Chorus lift.

## Use the tag system

Use English half-width brackets. Put each tag on its own line before the material it affects. Prefer short natural tags of one to four words.

Use three layers:

1. **Structural tags**: `[Intro]`, `[Verse 1]`, `[Pre-Chorus]`, `[Chorus]`, `[Bridge]`, `[Final Chorus]`, `[Outro]`, `[End]`.
2. **Local musical events**: `[Gradual Build]`, `[Instrumental Fill]`, `[Brief Pause]`, `[Guitar Solo]`, `[Beat Dropout]`, `[Controlled Belting]`.
3. **Experimental tendencies**: `[Controlled Key Lift]`, `[Short Melisma]`, `[Spaced Vocal Delivery]`, special ambience, uncommon instruments, or exact ending behavior.

Use a structure tag for every section. Use one to three local tags for a meaningful section state or transition. Do not enforce a whole-song cap of six local tags. Do not repeat an unchanged state before every lyric line.

Avoid long bracketed instructions, Chinese translations inside tags, near-synonym stacks, visual instructions, and ordinary notation terms with no useful audio behavior.

## Create breathing space

Use a hierarchy:

1. **Punctuation** for a micro-rest inside a phrase.
2. **Line break** for a normal singable phrase boundary.
3. **Blank line** between groups of phrases for a stronger breath or musical answer.
4. **Local event tag** such as `[Brief Pause]`, `[Vocal Rest]`, `[Instrumental Fill]`, `[Beat Dropout]`, or `[Instrumental Break]` for an intentional structural rest.
5. **Word spacing** only for a highlighted slow, hesitant, shouted, or chant-like delivery.

Do not add spaces between every Chinese character. It can create clipped pronunciation or rigid syllable-by-syllable singing. Prefer phrase-level spacing:

```text
十六小时　都精彩
每一次出发　都有未来
```

Use character spacing only for a deliberate highlight:

```text
[Spaced Vocal Delivery]
十 六 小 时
都 精 彩
```

Treat blank lines, spaces, and pause tags as tendencies rather than exact timing controls.

## Prevent overlapping vocals

Keep a separated solo lead by default. Useful local tags include:

```text
[Solo Lead Vocal]
[Clear Lead Vocal]
[Clear Syllabic Phrasing]
[Vocal Rest]
[Backing Vocals Enter]
[Unison Chorus]
```

Keep Verses free of unrequested backing layers. Introduce harmonies only where designed and mark their entry. Avoid `[Layered Vocals]`, `[Choir]`, or `[Call and Response]` unless the user wants them.

Use Style language such as:

```text
Use a single, clearly separated lead vocal with audible breath gaps between phrases. Keep the verses free of overlapping vocal lines, dense ad-libs, and continuous backing vocals. Introduce restrained harmonies only in the chorus while preserving clear lead-vocal articulation.
```

If no layering is desired anywhere, state:

```text
Keep one isolated lead vocal throughout, with no overlapping vocals, no call and response, and no continuous backing layers.
```

## Distinguish pitch behaviors

### Key modulation

Treat a move to a new tonal center as modulation. Keep it global in Style and mark a local highlight only when needed:

```text
Maintain a stable tonal center throughout, with no frequent or abrupt key changes.
```

For one final lift:

```text
Maintain a stable tonal center throughout, allowing one controlled key lift only in the final chorus.
```

```text
[Final Chorus]
[Controlled Key Lift]
```

Treat the local tag as experimental and do not promise an exact interval.

### Chromatic and out-of-key color

Use mostly genre-appropriate diatonic harmony. Permit sparse chromatic passing tones, borrowed harmony, or modal color at intentional transitions:

```text
Use mostly diatonic harmony, with sparse chromatic passing tones and occasional modal color only at emotional transitions.
```

For stronger restraint:

```text
Keep the harmony stable and predominantly diatonic. Avoid excessive chromatic movement, unstable pitch shifts, and wandering harmonic transitions.
```

### Melisma and vocal runs

Treat multiple notes on one syllable, melisma, runs, and ad-libs as vocal ornamentation rather than modulation. Default to clear syllabic phrasing:

```text
Keep the vocal phrasing mostly syllabic, with clear diction and restrained ornamentation. Avoid continuous melisma, excessive vocal runs, and uncontrolled ad-libs.
```

Reserve one controlled highlight when useful:

```text
Reserve one short, controlled melismatic run for the final phrase of the climax.
```

```text
[Short Melisma]
被听见
```

Increase harmonic and ornamental freedom only when the chosen genre—such as R&B, soul, gospel, jazz, opera, or an experimental form—requires it.

## Use the default Lyrics shape

```text
[Instrumental Intro]
[Opening Instrument]

[Verse 1]
[Solo Lead Vocal]
[Clear Syllabic Phrasing]

第一组歌词
第二组歌词

[Brief Pause]

第三组歌词
第四组歌词

[Pre-Chorus]
[Gradual Build]

过渡歌词

[Vocal Rest]
[Instrumental Fill]

[Chorus]
[Clear Powerful Vocal]
[Full Band Lift]

副歌与核心 Hook

[Outro]
[Decrescendo]
[Clean Ending]

结尾歌词

[End]
```

Adapt sections to the actual lyric. Do not create empty sections for symmetry.

## Apply reliability rules

- Treat section tags as the strongest layer.
- Treat natural Style language and compatible lyric formatting as primary control methods.
- Treat self-describing local event tags as medium-strength tendencies.
- Treat exact key changes, rare instruments, special languages, exact durations, exact pauses, and forced endings as experimental.
- Move uncertain global behavior into Style instead of inventing a long local tag.
- Tell the user when a requested control will likely require comparative generations.

