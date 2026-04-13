# Instruction for Agents

This document contains guidelines for our interaction and needs to be followed.

## Communication

- Skip the greetings and filler words like "Great question" and "Happy to help",
  and just start on the task. In fact, be as concise as possible in our
  communication.
- You're allowed to have opinions and disagree with me. Support with evidence.
- In general, don't ask for permission. Just find ways to do it.
- When there is any blocker, be resourceful and try to figure it out before
  asking. Read the file. Check the context. Search online to find out about
  similar problems. Only then ask, if you're stuck. The goal is to come back
  with answers, not questions.

## Documentation

- When working with a repo, use a hierarchical approach to find and read all
  README from the project root all the way down to the change level.
  - For example, to work with a code segment from `repo/src/lib/code.py`, you
    need to first read any README you can find from `repo/README.md`,
    `repo/src/README.md`, and `repo/src/lib/README.md`.
  - Child, granular README instructions override parental, global ones.
- When making changes and writing documentation, find the appropriate scope for
  the change, and write it in the corresponding README.
  - For example, if you made a change related to `repo/src/lib/code.py` and you
    are documenting it, you need to decide whether the change should be
    documented in `repo/README.md`, `repo/src/README.md`, or
    `repo/src/lib/README.md`. Read these READMEs to figure out which one the new
    change belongs.
  - Usually, when you make changes, go with the most general (highest) level
    possible and write documentations as such. Only when a change cannot be
    generalized, write it and document it at a lower level.

## Conciseness

- In general, when writing anything, be as concise as possible. The same outcome
  should be achieved with the shortest possible content. This stands for both
  programming code and documentation.

- When naming anything in code, prefer short names. There are a few ways to
  achieve this.
  - Prefer abbreviations. If there is a canonical abbreviation, use it instead
    of the full name. For example, `src` for source; `cfg` for config.
  - Prefer singular nouns. Do not use plurals unless absolutely necessary. For
    example, a file containing utility functions should be named `util` instead
    of `utils`; a folder containing test cases should be named `test` instead of
    `tests`.
  - Sometimes prefer nouns over adjectives if nouns are shorter. For example, a
    folder which keeps weekly updates can be named `week` instead of `weekly`; a
    directory for personal assets can be named `person` instead of `personal`.
  - Slightly prefer for names in the same hierarchy to have the same length. For
    example, if a folder contains both `schema.json` and `config.json` on the
    same level, notice that they have the same length which is nice. Given this,
    renaming `config` to the `cfg` abbreviation becomes optional.

- Avoid duplication, including the inadvertent kind.
  - When writing code, before starting, look at all possible places to see
    whether it is already written somewhere. If so, always reuse / improve on
    existent code if possible.
  - When writing documentation, before starting, look at all possible places to
    see whether the information is already captured somewhere. If so, include a
    pointer to it instead of writing the same information again.

- When writing anything, answer the question: can it be generalized as much as
  possible? For example, if I find that for a particular list of documents,
  adding some hyperparameters is necessary, then can the hyperparameters be
  added via a global mechanism so that it can apply to other lists of documents
  if needed? Always prefer this kind of global solutions over local ones.
  Whenever something can be generalized while still keeping the same local
  effect, prefer the global solution.

- Do not use brackets if possible. Brackets make reading order ambiguous. Often
  what you would want to write in brackets can be written in full as its own
  clause.

## Standard

- It is good to stay organized and unambiguous. The best way to do that is
  relying on a set of standards for records.

- When referring to a collection of entities, it could be error-prone to refer
  to them by their name, because sometimes different entities could have the
  same name, there could be different names for the same entity, or even
  different ways of writing the same name. In these cases, using the name to
  refer to entities can cause inconsistencies and make representation full of
  noise and retrieval unreliable.

- Therefore, when the collection of entities is well-defined, and there exists a
  common standard to refer to these entities by a code name, it is the best
  practice to adopt that standard and refer to standards by their code name. It
  is also good that the code name is often shorter than the full name.
  - For example, if we were recording a list of entities where each entity is
    tied to a geographic location, depending on whether these locations are
    contextualized politically or scientifically, we should use either the
    ISO-3166 standards, or the longtitude and latitude to refer to the
    locations.
    - So, "San Francisco, CA" would be referred to as `SFO` by its IATA metro
      area code. This is shorter and will not collide with, for example, "San
      Jose, Guatemala" which is `GSJ`.
  - For another example, if we are maintaining a database of documents where
    each is tied to a company, we could use the stock symbol of companies to
    refer to the companies.

- If you find yourself working with any objective entities, if you haven't done
  so already, stop and use extensive internet search and consulting to find
  whether a standard exists for our subject. Adopt the standard.

- When we secure a standard, it is often needed to make this standard into a
  synced artifact. Often this means saving it as dataset on a remote like
  HuggingFace.
  - This serves some purposes:
    - To systematically find common names of entities by their code names.
    - To keep different digital assets in sync.
    - To make customizations on top of standards, e.g. referring to entities in
      different languages, which is my personal preference.
  - For example, if during some project we neededed to find a collection of code
    names for major world cities, it is desirable to make this into a
    HuggingFace dataset.
  - Refer to my personal doc collection to find existent artifacts like this.

## Test

- When implementing any functionality that will live on in the repo and be
  reused, write corresponding tests. Make sure the tests are comprehensive and
  all pass. Follow repo conventions and write documentation about the tests.

- When writing any code, stop and ask: are we making any implicit assumptions
  about the code or content? If so, we need to realize it and make these
  invariants explicit and encode them into a test routine.
  - For example, if I am creating a list of documents and I expect all of them
    to be indexed by a certain field, then I need to stop and realize I am
    making an assumption that the field exists in all samples. Therefore, a
    tests should make sure that the field really exist in all samples.

## Misc

- In general, each line should not exceed 80 chars.

- The top lind of each commit message should look like this: `[tag] short
  one-liner`.
  - For example: `[chess] support hexagonal board`.
  - There could be multiple tags.

- In general, for any markup language or programming language, as long as it is
  code, before commiting, find the most canonical / popular auto-formatter for
  the language and use it to format the file. This should be done on all
  changes.
  - For example, if you made changes to a python file, you should find with
    internet search that `black` is a canonical formatter for it, and should
    have used it to format the python file before commiting your changes.

- Prefer writing lists over writing prose paragraphs. Each list item should be
  basically a sentence that's as short as possible.

- For yaml entries, use the `>` notation for any long string.

- In file naming, treat the underscore `_` as the outer-most, primary substitute
  for whitespace ; only use the hyphen `-` if another layer is needed.

- When writing anything in Chinese, only use traditional characters. Do not use
  any simplified characters at all. For transliterations, prefer mainland
  Chinese variants over Hong Kong variants over Taiwan variants. But no matter
  which one, always make sure to convert everything into traditional characters,
  especially if it comes from mainland China.

- Preserve the ordering of list elements. Usually it should be from the most
  prominent to the least. If the same type of list elements occur in multiple
  locations, make sure the rankings across these locations are consistent.

- When I refer to my personal code, it is usually stored under `~/llz`.

## Approach

Here is the procedure to follow when given any task in general.

- Read the documentation of the project and make sure everything makes sense.
  - Specifically, are there any assumptions made by the project?
  - Are these assumptions still up-to-date?
    - If external conditions have changed, do everything needed to update it
      accordingly.

- Do your research to find whether there exists best practices or pre-built
  solutions for the whole or part of the task. If something else is directly
  reusable, use it instead of reinventing the wheel.

- If there are invariants / assumptions made inside this project, make sure they
  are all covered by test cases.
  - Make sure test cases are as extensive and comprehensive as possible. Can
    there be more tests? Is there any invariant currently not tested?
  - Make sure tests all pass.

- Randomly select some sample lines from some files and take a look. Do they
  conform with your expectations? Can you find any problems or inconsistencies?
  If so, assume the problem is general and work on a global fix.

- Read each README file one by one. Can any file be more concise? For example,
  can some sentences or paragraphs be combined? Can some word choices be
  streamlined? If so, improve it.

- Read each program file one by one. Can any source code be more concise? For
  example, can some functions be combined? Maybe some code is independently
  written in more than one location. Find them and combine them so we avoid code
  duplication.

- Think whether the file directory structure still makes sense. If need be,
  tentatively work on a redesign of the project and ask me for review.
