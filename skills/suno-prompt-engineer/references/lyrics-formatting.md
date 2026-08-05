# Lyrics Formatting, Metatags, and Vocal Control

## Contents

1. Field responsibilities
2. Tag system
3. Breath and spacing
4. Vocal overlap
5. Emotional and register ceiling
6. Tonality and ornamentation
7. Formatting examples
8. Reliability rules

## Separate the two fields

Put lyrics, section boundaries, local performance states, rests, and section-specific events in Lyrics. Put whole-song genre, emotion, groove, harmony, instrumentation, vocal baseline, mix, and exclusions in Style.

Express a major local event in both places only when Style must prepare the global arrangement for it, such as one controlled final-Chorus lift.

## Use the tag system

Use English half-width brackets. Put each tag on its own line before the material it affects. Prefer short natural tags of one to four words.

Use three layers:

1. **Structural tags**: `[Intro]`, `[Verse 1]`, `[Pre-Chorus]`, `[Chorus]`, `[Bridge]`, `[Final Chorus]`, `[Outro]`, `[End]`.
2. **Local musical events**: `[Instrumental Fill]`, `[Brief Pause]`, `[Guitar Solo]`, `[Beat Dropout]`, `[Vocal Pullback]`, `[Reduced Arrangement]`.
3. **Experimental tendencies**: `[Controlled Key Lift]`, `[Short Melisma]`, `[Spaced Vocal Delivery]`, special ambience, uncommon instruments, or exact ending behavior.

Use a structure tag for every section. Use zero to three local tags only for a meaningful state or transition. A section needs no local tag when the whole-song Style already describes its delivery. Do not enforce a whole-song cap of six local tags, but do not decorate every section mechanically.

Put persistent instructions such as solo lead vocal, clear syllabic diction, low register, soft piano, or stable tonal center in Style. Do not repeat `[Solo Lead Vocal]` and `[Clear Syllabic Phrasing]` before every Verse. Choose one precise structural opening such as `[Instrumental Intro]`; do not stack `[Intro]` and `[Instrumental Intro]` when they mean the same event.

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

## Control the emotional and register ceiling

Treat “sad,” “quiet,” “restrained,” and “intimate” as limits on energy behavior, not only mood adjectives. A Chorus may become more emotionally explicit without becoming louder, higher, wider, or more densely arranged.

First set the whole-song baseline in Style: low-to-mid register, narrow melodic range, intimate or near-spoken delivery, restrained dynamics, sparse arrangement, stable tonal center, and no unrequested modulation, belting, octave leaps, or climactic high notes.

Then use a local pullback tag immediately before a section or line that is likely to overshoot:

```text
[Vocal Pullback]
[Return to Low Register]
[Restrained Dynamics]
[Near-Spoken Delivery]
[Narrow Melodic Range]
[Short Note]
[No Melisma]
[Falling Cadence]
```

Use only the smallest compatible subset. Place the tag before the affected line, not after it. Shorten an overloaded line, provide a breath boundary, and avoid an open-ended sustained cadence when the final word keeps triggering a high held note.

Audit every local tag for hidden escalation. In a quiet song, tags such as `[Gradual Build]`, `[Powerful Vocal]`, `[Controlled Belting]`, `[Full Band Lift]`, `[Full Strings]`, `[Crescendo]`, and `[Controlled Key Lift]` conflict unless the user explicitly approved that event. Replace them with semantic intensity, subtle harmonic color, a brief texture change, or one of the pullback behaviors above.

These controls influence probability; they cannot force an exact pitch or guarantee that a generation will never rise. If the same overshoot repeats, strengthen the coordinated Style wording and simplify the risky line before stacking more tags.

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

[Verse 1]

第一组歌词
第二组歌词

[Brief Pause]

第三组歌词
第四组歌词

[Pre-Chorus]

过渡歌词

[Vocal Rest]
[Instrumental Fill]

[Chorus]

副歌与核心 Hook

[Outro]
[Decrescendo]
[Clean Ending]

结尾歌词

[End]
```

Adapt sections to the actual lyric. Do not create empty sections for symmetry, and add local tags only where the musical state actually changes.

For a quiet song whose refrain must stay down rather than lift, use a shape like:

```text
[Chorus]
[Same Register]
[Restrained Dynamics]

副歌与核心 Hook

[Bridge]
[Reduced Arrangement]
[Vocal Pullback]

转折歌词

[Final Chorus]
[Return to Low Register]
[Near-Spoken Delivery]

最后一次 Hook
```

## Apply reliability rules

- Treat section tags as the strongest layer.
- Treat natural Style language and compatible lyric formatting as primary control methods.
- Treat self-describing local event tags as medium-strength tendencies.
- Treat exact key changes, rare instruments, special languages, exact durations, exact pauses, and forced endings as experimental.
- Move uncertain global behavior into Style instead of inventing a long local tag.
- Tell the user when a requested control will likely require comparative generations.
