# BDB for Context-Fabric

*A Hebrew and English Lexicon of the Old Testament* by Francis Brown, S. R. Driver and Charles A. Briggs (Oxford, 1906), as one file for the [Context-Fabric browser](https://github.com/Context-Fabric/context-fabric/tree/master/libs/browser), with every entry linked to the lexemes of the BHSA.

The file is in the [releases](https://github.com/Context-Fabric/bdb/releases). The browser downloads it from there (*Open a corpus* → *Dictionaries* → *Add*, or `cfabric-browser add bdb`) and checks its checksum.

## What is in it

`bdb.json.gz`, gzipped JSON:

- `entries`: the 11,878 entries of BDB in its order, Hebrew (11,015) then Aramaic (863): the text as Sefaria has it, its HTML reduced to a few tags (`big`, `sub`, `sup`, `strong`, `em`, `br`, `span dir`), references to verses as OSIS ids (`<a data-osis="Gen.1.1">`) and to other entries as their ids (`<a data-entry="b.cw.ab">`); with Open Scriptures' id, part of speech, short definitions, root group (`section`), and Strong's and TWOT numbers.
- `links`: per BHSA lexeme (`"Hebrew BR>["`) the entries it belongs to, the main one first, and how the link was made: `oshb` (the BHSA's words aligned with the Open Scriptures Hebrew Bible, whose lemmas lead to the entries, with the share of the occurrences), `cited` (another entry cites the lexeme's verses clearly better) or `manual`.
- `abbreviations`: BDB's list of abbreviations.
- `meta`: the sources at their versions, with checksums, and figures of the build.

All 9,230 lexemes of the BHSA (2021) are linked. 22 entries stop short in Sefaria's text and are marked `incomplete`; two entries Sefaria lacks (Oreb, and Aramaic שִׁלְטוֹן) have only Open Scriptures' short definition.

## How it is made

With `python -m cfabric_browser.dictionaries.build OUT` in the Context-Fabric repository: it walks Sefaria's API once (about 12,000 requests, one a second, kept in a checksummed cache), joins Sefaria's entries to Open Scriptures' ids by BDB's order and headwords (with joins by hand in `joins.yaml`), aligns the BHSA with the OSHB verse by verse, and checks the links against the verses BDB cites (with corrections by hand in `corrections.yaml`).

## Sources and licences

- **BDB** (1906): public domain. The text is from Sefaria's *BDB Dictionary* and *BDB Aramaic Dictionary*, given there as public domain, from a scan in the National Library of Israel.
- **Open Scriptures HebrewLexicon** (ids, short definitions, lexical index, Strong's and TWOT numbers): CC BY 4.0, Open Scriptures Hebrew Bible Project.
- **Open Scriptures Hebrew Bible** (`morphhb`, the lemmas used for linking): CC BY 4.0.
- **BHSA** (ETCBC, the lexemes linked to): the links name its lexemes; the BHSA is CC BY-NC 4.0.

The file is licensed under CC BY-NC 4.0. The text of BDB (1906) is in the public domain, and Open Scriptures' data in it (ids, short definitions, Strong's and TWOT numbers) remains available under CC BY 4.0. The links to the BHSA's lexemes derive from the BHSA (CC BY-NC 4.0). See `LICENSE`.
