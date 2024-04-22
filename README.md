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

## License

The content in the Kimchi Grammar repository is available under
the [Creative Commons Attribution 4.0 International License (CC-BY 4.0)](LICENSE).
This license allows for sharing, copying, distributing, and transmitting the work, or adapting it for any purpose, even
commercially, as long as
appropriate credit is given, a link to the license is provided, and any changes made are indicated.

Please note, the audio content provided in this repository is generated using Elevenlabs and is licensed under a
separate commercial license.
Use of this audio content must adhere to the terms specified by the commercial license from Elevenlabs.
