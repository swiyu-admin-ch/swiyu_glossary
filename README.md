![github-banner](https://github.com/swiyu-admin-ch/swiyu-admin-ch.github.io/blob/main/assets/images/github-banner.jpg)

# swiyu_glossary

Translations of the swiyu glossary, managed with [Weblate](https://weblate.org/) using [TBX](https://en.wikipedia.org/wiki/TermBase_eXchange) (TermBase eXchange) files.

## Structure

```
tbx/de.tbx   # English → German
tbx/fr.tbx   # English → French
tbx/it.tbx   # English → Italian
tbx/rm.tbx   # English → Romansh
```

Each file is a **bilingual** termbase: English (`en`) is the source language and
the language in the filename is the target. Every concept is a `<termEntry>`
holding a source `<langSet xml:lang="en">` and a target `<langSet>`:

```xml
<termEntry>
    <langSet xml:lang="en"><tig><term>verifiable credential</term></tig></langSet>
    <langSet xml:lang="de"><tig><term>überprüfbarer Nachweis</term></tig></langSet>
</termEntry>
```

There is no `en.tbx` — English already lives in the source `<langSet>` of every
file, and a file named after the source language would be detected as a
duplicate.

One file per language is a Weblate requirement, not a TBX one. TBX itself can
hold every language in a single file, but Weblate derives the target language of
a component file from its filename via the file mask, so a single multilingual
`glossary.tbx` cannot be mapped to a language. A multilingual TBX can still be
used for a one-off import through the glossary upload form.

## Weblate component

| Setting | Value |
| --- | --- |
| File format | `TermBase eXchange file` |
| File mask | `tbx/*.tbx` |
| Monolingual base language file | *(empty)* |
| Template for new translations | *(empty)* |
| Source language | `English (en)` |
| Use as a glossary | on |

Because the template for new translations is empty, Weblate cannot create a
language from the UI. To add one, commit a new `tbx/<code>.tbx` file following
the same layout.

## Seed entry

Each file ships one `verifiable credential` entry with an empty target, so the
component has a string to parse when it is first connected. Translate it or
remove it once real terms are in place.
