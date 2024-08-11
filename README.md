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
on [Kimchi Reader's discord](https://discord.gg/aEm5eDRpeZ) and/or open a pull request. Contributions should be
introducing small, focused changes that address specific aspects without including unrelated modifications.

### How to contribute

Normally contributing on a github repository requires knowledge of git. There are tons of tutorials on the internet
and/or alternatively you can always ask for helps on our discord server. The general workflow is the follow:

1. Create a fork of Kimchi Grammar
2. Make a new branch from `main`
3. Apply the change you want to make (eg. create a new grammar point or edit an existing one - this is where you most of your time)
4. Commit the change
5. Open a pull request

> [!TIP]
> All these steps can be done directly on the GitHub website without installing anything.

## Guidelines & Nomenclature

### Schema for a Grammar point

```yaml
point: [ Hangul form of grammar, appears in pop-up dict ]
definitions:
  - slug: [ Appears at the end of url in browser ]
    name: [ Summarizes grammar in pop-up dict ]
    english_alternatives: [ english phrases with similar meaning ]
    meaning: [ Describes grammar in one or two sentences ]
    examples:
      - type: simple
        sentence: [ Korean example sentence ]
        translated: [ English translation of korean sentence ]
        audio_url: [ generated audio reading, leave it blank ]
metadata:
  type: [ noun, verb, or composite ]
details: |-
  [Use markdown syntax to explain more details about the grammar]
```

As for the yaml filename itself you can take inspiration from the neighboring files.

A note on the `type` field. `noun` and `verb` are used when the related grammar only attach to a certain kind of word.
`composite` is for grammar points that appear on a pack of words. (Eg. `ㄹ 수 있다` is something that get attached to 3
words)

### Guideline naming grammar points

> [!TIP]
> Guidelines are not strict rules, but rather suggestions to help maintain consistency and clarity across the content.

Where applicable, the field `name` appears in the popup dictionary next to the grammar point. Keep the name short, and
refer to the examples for tips on naming. If you're not sure which of the two naming styles should be used, pick
whichever one seems simple and makes sense.

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

## License

The content in the Kimchi Grammar repository is available under
the [Creative Commons Attribution 4.0 International License (CC-BY 4.0)](LICENSE).
This license allows for sharing, copying, distributing, and transmitting the work, or adapting it for any purpose, even
commercially, as long as
appropriate credit is given, a link to the license is provided, and any changes made are indicated.

Please note, the audio content provided in this repository is generated using Elevenlabs and is licensed under a
separate commercial license.
Use of this audio content must adhere to the terms specified by the commercial license from Elevenlabs.
