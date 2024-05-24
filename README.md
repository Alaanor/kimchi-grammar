# Kimchi Grammar

This repository is hosting the data used in the grammar section of Kimchi Reader, you can see it live
at [kimchi-reader.app/grammar](https://kimchi-reader.app/grammar).
It exclusively contains data in the form of .yaml files for now, no code is included.

## Purpose and scope

### Goals

- **Efficiency:** The grammar content in this repository is designed to be non-verbose and straight to the point,
  providing clear and concise explanations.
- **Reference Oriented:** It should aim to create a comprehensive reference or Wiki-like resource that can be easily
  consulted.
- **Input Focused:** The content is primarily focused on enhancing the understanding of grammar through reading and
  listening, this focus supports learners
  in absorbing grammatical structures and usage naturally, with less emphasis on active language production such as
  writing and speaking.

### Non-Goals

- **Not a Course:** This repository is not intended to serve as a structured language course or a series of lessons.

## Project structure

| path               | details                                                                                                                                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `point/`           | Contains the data for the grammar points. Each `.yaml` file is a page on the website.                                                                                                                           |
| `comparison/`      | This data is used to hydrate `point/*` pages with some comparison.                                                                                                                                              |
| `relation.yaml`    | This file is used to generate the relation graph between grammar points. I have not yet defined what exactly constitute a relation. If you think you have a good way to organize the data here, please suggest. |
| `inheritance.yaml` | Document the building block between each grammar point. Eg. `ㄹ_수_있다.yaml` exist and internally it make use of `verb_ㄴ_은_는_ㄹ_을.yaml` for the first part.                                                         |

## Custom markdown syntax

Inside the .yaml files, you may use markdown on the following fields:

| folder              | fields             |
|---------------------|--------------------|
| `point/*.yaml`      | `details`          |
| `comparison/*.yaml` | `details`          |
| `comparison/*.yaml` | `points[].details` |

The markdown used by kimchi has been extended with some custom directives, html, etc. such as:

| syntax                                      | effect                                                                                             | example                                                                                                                                  |
|---------------------------------------------|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| `:dict[lemma]`                              | Make a link to the dictionary entry `lemma`                                                        | `:dict[가다]`                                                                                                                              |
| `:dict[lemma]{word}`                        | Make a link to the dictionary entry `lemma` with the text `word`                                   | `:dict[가다]{가요}`                                                                                                                          |
| `:grammar[grammar_id]`                      | Make a link to the grammar entry `grammar_id`                                                      | `:grammar[verb_며_으며]`                                                                                                                    |
| `:grammar[grammar_id]{slug}`                | Make a link to the grammar entry `grammar_id` at the `slug` definition                             | `:grammar[noun_같이]{similarity}`                                                                                                          |
| `:grammar[grammar_id]{noprefix}`            | Make a link to the grammar entry `grammar_id` without the prefix (Eg. V+)                          | `:grammar[noun_이다]{noprefix}`                                                                                                            |
| `:grammar[grammar_id]{noprefix slug}`       | Make a link to the grammar entry `grammar_id` at the `slug` definition without the prefix (Eg. V+) | `:grammar[noun_은_는]{noprefix topic}`                                                                                                     |
| `::example[korean \| english]`              | Add an example in the body with translation                                                        | `::example[제<f>가</f> 할게요. \| I will do it.]`                                                                                             |
| `::example[korean \| english \| audio_url]` | Add an example in the body with translation and audio                                              | `::example[제<f>가</f> 할게요. \| I will do it. \| https://r2.kimchi-reader.app/grammar/제가_할게요__2024-04-13.mp3]`                              |
| `:correct[text]`                            | Show a valid example                                                                               | `:correct[새벽<f>같이</f> 떠나다]`                                                                                                              |
| `:wrong[text]`                              | Show an invalid example                                                                            | `:wrong[새벽<f>처럼</f> 떠나다]`                                                                                                                |
| `:source[url]`                              | Cite a source for the information                                                                  | `:source[https://namu.wiki/w/절#s-4.1]`                                                                                                   |
| `:::alert {rule}`                           | Start a rule block                                                                                 | [irregular_verb.yaml](https://github.com/Alaanor/kimchi-grammar/blob/a3315d175a29da4ca4d48916810745031570f1ef/point/irregular_verb.yaml) |
| `<f>text</f>`                               | Make the text `text` in colored bold                                                               | `<f>bold</f>`                                                                                                                            |

## Contributions

Contributions are highly welcomed, feel free to open an issue, talking about it
on [Kimchi Reader's discord](https://discord.gg/aEm5eDRpeZ) and/or open a pull request.
Contributions should be introducing small, focused changes that address specific aspects without including unrelated
modifications.

# Contributions

Contributions are highly welcomed, feel free to open an issue, talking about it on [Kimchi Reader's discord](https://discord.gg/aEm5eDRpeZ) and/or open a pull request.
Contributions should be introducing small, focused changes that address specific aspects without including unrelated modifications.

# Grammar Entry Style Guide

Use the [Template](#template) as a starting point for making your own grammar page. Refer to the Field Details for more info regarding style and purpose of the field.

[Field Explanations](#field-explanation) contain tips and examples for how to write a good entry.

Table of Contents

- [Creating the file](#creating-the-file)
- [Template](#template)
- [Field Explanation](#field-explanations)
- [Field Details](#field-details)
  - [point](#point)
  - [definitions](#definitions)
    - [slug](#slug)
    - [name](#name)
    - [english_alternatives](#english-alternatives)
    - [meaning](#meaning)
    - [examples](#examples)
    - [type](#type)
    - [sentence](#sentence)
    - [audio_url](#audio_url)
  - [metadata](#metadata)
    - [type](#type)

## Creating the File

1. Use a text editor to make a .yaml file.
2. Name the file based on being attached to a noun, attached to a verb, or "composite". "Composite" here means there is a space in the middle of the form. This gets its own category:

- Examples:
  - `noun_까지.yaml`
  - `verb_으려고_라고.yaml`
  - `고_싶다.yaml` (composite)

## Template

The Following example is the page for 와/과:

```yaml
point: 와/과
definitions:
  - slug: enumeration
    name: Enumeration
    english_alternatives: and
    meaning: Connects multiple nouns, indicating a list or group without specifying order.
    examples:
      - type: simple
        sentence: 초가집에는 어머니<f>와</f> 어린 삼 남매가 살았다.
        translated: In the straw-thatched house lived a mother and her three young siblings.
        audio_url: https://r2.kimchi-reader.app/grammar/초가집에는_어머니와_어린_삼_남매가_살았다._2024-02-21.mp3
      - sentence: 대만<f>과</f> 일본은 사이가  좋다.
        type: simple
        translated: Taiwan and Japan are on good terms.
        audio_url: https://r2.kimchi-reader.app/grammar/대만과_일본은_사이가_좋다._2024-02-21.mp3
  - slug: companionship
    name: Companionship
    english_alternatives: together, with
    meaning:
      Indicates that an action involves more than one party or that something
      is done together with someone or something else.
    examples:
      - sentence: 너<f>와</f> 난 평생을 함께할 친구야.
        type: simple
        translated: You and I are friends for the rest of our lives.
        audio_url: https://r2.kimchi-reader.app/grammar/너와_난_평생을_함께할_친구야._2024-02-21.mp3
      - sentence: 친구<f>와</f> 같이 갔어요.
        type: simple
        translated: I went with my friend.
        audio_url: https://r2.kimchi-reader.app/grammar/친구와_같이_갔어요._2024-02-21.mp3
metadata:
  type: noun
details: |-
  # Usage {#usage}

  - <f>와</f> is used in front of a word ending in a vowel.
  - <f>과</f> is used in front of a word ending in a consonant.
```

## Field Explanations

```yaml
point: [Hangul form of grammar, appears in pop-up dict]
definitions: (blank line)
  - slug: [Appears at the end of url in browser ]
    name: [Summarizes grammar in pop-up]
    english_alternatives: [english phrases with similar meaning]
    meaning: [Describes grammar in one or two sentences]
    examples: 
      - type: simple
        sentence: [Korean example sentence]
        translated: [English translation of korean sentence]
        audio_url: [generated audio reading. leave blank]
metadata:
  type: [noun, verb, or composite]
details: |-
  [Use markdown syntax to explain more details about the grammar]
```

## Field Details

### Name

This field appears in the popup dictionary next to the grammar point. Keep the name short, and refer to the examples for tips on naming. If you're not sure which of the two naming styles should be used, pick whichever one seems simple and makes sense.

_When to use Active Descriptive Voice_

- Conveying a specific emotion or intent:
  - "Expresses Surprise" (for -네)

- When describing the functionality or purpose of a grammar point:
  - "Expresses Possibility" (for -을 수 있다)

- Reflecting the speakers attitude or perspective:
  - "Conveys Politeness" (for -습니다/습니다)

_What to Avoid_

- Present progressive: "Indicating concern", "Expressing Contrast"
- Non-present tense: "Showed Intent", "Will demonstrate Emphasis"
- Imperative (command): "Express Surprise", "Clarify Reason"
- Passive voice: "Politeness Conveyed"

_When to Use Labels Instead of Active Voice_

- Neutral descriptions of the sequence or structure of a sentence without an emotional or intentional nuance.
  - "Cause and Effect" (for -기 때문에)
  - "Simultaneous Actions" (for -면서)

- When the grammar point fits a generic "grammatical" purpose or category.
  - "Condition" (for -면)
  - "Comparison" (for -보다)

- Indicating tense or aspect
  - "Past" (for -았/었)
  - "Progressive" or "Ongoing" (for -고 있다)

_What to Avoid_

- Technical or linguistic terms: "Progressive **Aspect**", "Subordinating clauses".
- Terms should be understood without linguistic knowledge beyond basic grammar concepts i.e. "verb", "tense".

### point
wip

### definitions
wip

### slug
wip

### name
wip

### english alternatives
wip

### meaning
wip

### metadata
wip

### type
wip

### sentence
wip

### audio_url
wip

### type
wip

## License

The content in the Kimchi Grammar repository is available under
the [Creative Commons Attribution 4.0 International License (CC-BY 4.0)](LICENSE).
This license allows for sharing, copying, distributing, and transmitting the work, or adapting it for any purpose, even
commercially, as long as
appropriate credit is given, a link to the license is provided, and any changes made are indicated.

Please note, the audio content provided in this repository is generated using Elevenlabs and is licensed under a
separate commercial license.
Use of this audio content must adhere to the terms specified by the commercial license from Elevenlabs.
