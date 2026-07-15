# Technical methodology for building complete author and historical-figure dossiers

**Version:** 1.0  
**Date:** 15 July 2026  
**Scope:** `F:\IA\CEREBRO 1` and `F:\IA\EXPEDIENTE`  
**Target outcome:** a self-contained dossier combining an operational agent-personality with a verifiable documentary brain.

## 1. Definition of a complete dossier

A complete dossier is not merely a biography, a bibliography, a book summary, or a directory of extracted texts. It is a self-contained knowledge unit with two mutually constraining layers:

1. **Agent-personality:** reconstructs how the author defines problems, distinguishes concepts, evaluates evidence, raises objections, and formulates answers. It must not imitate superficial mannerisms or theatrical speech.
2. **Documentary brain:** preserves primary texts, textual witnesses, provenance, thematic evidence, and an independent local search index. It prevents the personality layer from degenerating into an unsupported stereotype.

The governing principle is:

> Without an operational personality, the index is a passive library. Without a documentary corpus, the personality is an uncontrolled fiction.

The directory must remain usable after being copied outside CEREBRO 1. Its corpus, SQLite database, search utility, manifest, and integrity checks are local to the dossier.

## 2. Mandatory common structure

Each person is stored under an uppercase directory name:

```text
F:\IA\EXPEDIENTE\AUTHOR NAME\
├── EXPEDIENTE_AUTHOR_NAME.md
├── AGENTE_PERSONALIDAD.md
├── PROMPT_AGENTE.md
├── REGLAS_Y_PRUEBAS.md
├── FUENTES.md
├── DICCIONARIO.md
├── MAPA_CONCEPTUAL.md
├── PREGUNTAS_DE_INVESTIGACION.md
├── GUIA_DE_USO.md
├── LEEME.md
├── buscar.py
├── expediente_author_name.sqlite3
├── corpus\
│   ├── primarias\
│   │   └── complete texts and textual witnesses
│   └── secundarias\
│       └── fragmentos_contextuales.md
├── evidencias\
│   └── EVIDENCIAS_TEMATICAS.md
└── state\
    ├── manifest.json
    └── checksums.sha256
```

Additional justified artifacts may be retained, such as Plato's original Word document or Aristotle's earlier documentary synthesis. The common modules must never be omitted.

## 3. Required input data

### 3.1. Document catalog

The primary inventory source is:

```text
F:\IA\CEREBRO 1\state\catalog.jsonl
```

Each catalog record should provide:

- `id`: stable source identifier;
- `title`: cataloged title;
- `author`: cataloged attribution;
- `path`: immutable original under `raw/`;
- `text_path`: extracted text under `extracted/`;
- `status`: extraction status;
- `words`: word count;
- `units`: page, chunk, or structural unit count;
- `sha256`: cryptographic hash of the original;
- `duplicate_of`: canonical source identifier for a documented duplicate;
- `warnings`: encoding, container, or extraction warnings.

### 3.2. Global CEREBRO 1 index

The read-only global database is:

```text
F:\IA\CEREBRO 1\state\brain.sqlite3
```

It is used to:

- retrieve thematic evidence from primary sources;
- discover substantive references in other works;
- preserve locators for evidence excerpts;
- identify opaque filenames or incorrectly attributed sources;
- distinguish primary corpus from secondary reception.

### 3.3. Extracted source texts

Working texts are read from:

```text
F:\IA\CEREBRO 1\extracted\
```

Files under `raw/` remain immutable. The dossier copies extracted text and never modifies the source document.

### 3.4. Minimum analytical information

Before personality drafting begins, the following must be known:

- available and absent works;
- recurring concepts and problem families;
- reasoning operations;
- internal tensions and historical development;
- genre and period differences;
- interpretation risks;
- distinctions among author, character, editor, coauthor, and interpreter;
- testable questions that can be checked against the corpus.

## 4. Process 1: initial author inventory

### Objective

Find all potentially relevant sources even when catalog metadata uses different spellings or name orders.

### Procedure

1. Search surname and variants across `id`, `title`, `author`, and `path`.
2. Normalize case, accents, punctuation, and name order.
3. Merge obvious aliases.
4. Count usable witnesses, words, and extraction states.
5. list titles to reveal anomalies and false attributions.
6. Compare the result against existing directories in `EXPEDIENTE`.

### Example: Isaac Asimov

The catalog used three forms:

- `Isaac Asimov`
- `asimov, isaac`
- `Asimov, Isaac`

Treating these independently would produce three incomplete inventories. Alias normalization yielded 39 usable witnesses and 885,712 words.

### Example: Max Weber

The catalog used `Weber, Max` and `Max Weber`. Merging them produced seven witnesses and 388,119 words.

### Unconfirmed-author case

Herodotus, Nietzsche, Plato, and Aristotle had sources classified as `Autor no confirmado`. For these figures, author-field grouping is insufficient. Identification must use title, path, internal evidence, and source identifier.

## 5. Process 2: source-role classification

Every candidate source is assigned an explicit role.

### 5.1. Primary source

A text attributed to the dossier subject and usable as direct evidence. It may be a book, article, story, letter, lecture, or volume.

### 5.2. Primary textual witness or variant

A second edition or extraction of the same work. It is retained when content, length, format, or hash differs.

### 5.3. Coauthored source

A text produced with another person. It remains usable, but its role is explicitly recorded and it is never treated as uncontested individual voice.

Arthur C. Clarke examples include *Cradle* with Gentry Lee and *The Light of Other Days* with Stephen Baxter.

### 5.4. Associated but non-primary source

A work associated with the author or fictional universe but written by somebody else.

Practical case: *Venus Prime Vol. 1* appeared under Arthur C. Clarke, but its internal title material identifies Paul Preuss as the author. It was excluded from Clarke's primary voice.

### 5.5. Secondary or contextual source

A text that interprets, cites, or reuses the subject. It supports reception studies and contrast, but cannot be silently attributed to the primary author.

Foucault's and Heidegger's studies of Nietzsche are handled in this way.

### 5.6. Duplicate

A source whose hash matches another file or whose record specifies `duplicate_of`. Only the canonical copy is retained.

Documented examples include a duplicate of Asimov's *Caza mayor*, one copy of Clarke's *The Sentinel*, and one Nietzsche *Homer and Classical Philology* file.

## 6. Process 3: duplicate and variant control

Title equality is not sufficient for deduplication.

### Decision rules

1. **Identical SHA-256:** binary duplicate; retain one canonical copy.
2. **Catalog `duplicate_of`:** honor the recorded canonical relationship.
3. **Same title, different hash:** preserve as a textual witness until equivalence is demonstrated.
4. **Substantially different lengths:** assume editorial or extraction differences.
5. **Partial versus complete copy:** prioritize the complete witness while retaining the partial copy only when it provides meaningful provenance control.
6. **Different edition or coauthorship:** preserve and label.

### Practical case: Asimov's *Esquirol*

Two similarly titled sources have different lengths and contents. They are not removed by title matching.

### Practical case: Weber

*Politics and Science* contains *Politics as a Vocation*, while an independent witness of the lecture also exists. Both are retained, and the overlap is documented.

## 7. Process 4: extraction-quality assessment

### Core states

- `extracted`: satisfactory text recovery;
- `partial`: usable content with structural, encoding, pagination, or container limitations;
- `duplicate`: non-independent copy;
- pending or failed state: excluded until successfully recovered.

### Correct interpretation of `partial`

It does not always mean missing pages. It may indicate:

- visible RTF control codes;
- unpaginated TXT;
- legacy encoding;
- a container that collapses the document into one unit;
- damaged glyphs;
- poor structural recovery despite substantial textual completeness.

Examples include Weber RTF files and many Clarke TXT files lacking reliable pagination.

### Locator policy

When a text includes markers such as `[[PAGE 238]]`, the locator is `p. 238`. Otherwise the dossier uses `fragment 1`, `fragment 2`, and so on. Page numbers are never fabricated.

## 8. Process 5: scope definition

Before drafting, the system determines:

- number of unique works;
- number of witnesses and variants;
- total primary word count;
- represented genres and periods;
- missing periods or major works;
- availability of letters, critical editions, and editorial notes;
- disputed authorship;
- compilations or extracts presented as books;
- conclusions weakened by absence.

Examples:

- Plato has 21 works and 29 witnesses but lacks *Laws*, *Parmenides*, *Sophist*, *Theaetetus*, and *Philebus*.
- Aristotle lacks the *Organon*, *Rhetoric*, and complete biological treatises.
- Asimov has a large corpus, but Foundation-series coverage is incomplete.
- Weber lacks a complete local volume of *The Protestant Ethic and the Spirit of Capitalism*.
- Clarke lacks major works such as *The City and the Stars* and *The Songs of Distant Earth*.

Completeness always means complete relative to identified CEREBRO 1 material, not complete relative to the historical bibliography.

## 9. Process 6: epistemic hierarchy

Every assertion is assigned an authority class.

- **SOURCE:** directly recoverable from primary text.
- **EDITORIAL CONTEXT:** introduction or note supplied by an edition.
- **SECONDARY CONTEXT:** interpretation by another author.
- **SYNTHESIS:** reasoned integration of multiple primary sources.
- **INFERENCE:** probable reconstruction of how the author might approach an unaddressed question.
- **UNCERTAINTY:** conclusion that the local corpus cannot settle.

This classification prevents secondary reception from becoming false primary voice and makes contemporary application auditable.

## 10. Process 7: drafting the mandatory 17 blocks

The main document always contains numbered blocks 0 through 16.

### 0. Definition and scope

Corpus size, authority hierarchy, warnings, and operational purpose.

### 1. Executive result

A concise statement of the author's central problem-solving orientation. It must distinguish the subject from every other dossier.

### 2. Located primary corpus

Works, witnesses, variants, genres, extraction states, and attribution issues.

### 3. Core intellectual identity

Stable operations rather than generic adjectives. For Weber, "distinguishes power, domination, and legitimacy" is useful; "is profound" is not.

### 4. Cognitive profile and reasoning style

An executable sequence describing question formulation, evidence selection, conceptual distinctions, objections, and conclusion behavior.

### 5. Cross-work doctrinal map

Conceptual relationships across several works rather than an isolated glossary.

### 6. Operational personality profile

Conversational behavior, tone, pacing, preferred questions, uncertainty tolerance, and quality criteria.

### 7. Unresolved internal tensions

Contradictions, period changes, and genre differences are preserved rather than forced into artificial unity.

### 8. Work-by-work matrix

Title, role, status, word count, provenance, coauthorship, and witness function.

### 9. Personality-use rules

Mandatory and prohibited behaviors.

### 10. Consistency tests

Questions that convert fidelity into testable checks.

### 11. Secondary sources and context

Reception is separated from primary voice. If no source clears the relevance threshold, the section remains explicitly empty.

### 12. Limits and corpus gaps

Missing works, partial extractions, translation problems, disputed authorship, and incomplete series.

### 13. Technical index

Source path, state, word count, and local file for every witness.

### 14. Control passages

Routes readers to `EVIDENCIAS_TEMATICAS.md` and full-text expansion.

### 15. Conclusion

Explains why this combination of operational personality and documentary evidence is distinctive.

### 16. Update protocol

Defines how new material is incorporated without losing provenance or consistency.

## 11. Process 8: agent-personality engineering

### 11.1. Operational thesis

The thesis describes a repeatable method, not a decorative slogan.

Weber example: understand the meaning of action and causally explain how action produces historical orders.

### 11.2. Dominant operations

Use verbs: define, distinguish, compare, reconstruct, verify, contextualize, object, and calibrate confidence.

### 11.3. Response sequence

A general sequence is:

1. Clarify the question.
2. Identify the central concept.
3. Determine whether the answer requires source, synthesis, or inference.
4. Retrieve evidence.
5. Reconstruct the relevant argument.
6. Present tensions and the strongest objection.
7. Conclude with explicit confidence.

It is then specialized:

- Plato: definition, examination, refutation, objection, and explicit aporia.
- Aristotle: senses, causal structure, potentiality/actuality, cases, and calibrated conclusion.
- Freud: symptom or clue, conflict formation, defense, rival interpretation, and clinical boundary.
- Asimov: rules, constraint, anomaly, consequences, and edge case.

### 11.4. Tone

Tone must derive from method:

- Plato: interrogative and examining;
- Aristotle: sober, classificatory, and causal;
- Nietzsche: genealogical and provocative without reducing provocation to abuse;
- Weber: analytical, comparative, and consequence-aware;
- Asimov: clear, sequential, rationalist, and mildly ironic.

### 11.5. Guardrails

- never fabricate quotations;
- never attribute later events to the historical author;
- do not merge character and author;
- disclose coauthorship;
- do not present hypotheses as source evidence;
- do not hide corpus gaps;
- do not treat fictional mechanisms as available science;
- do not reproduce historical prejudice without critical framing.

## 12. Process 9: reusable agent prompt

`PROMPT_AGENTE.md` activates both layers with a compact instruction:

```text
Act as a specialist in [AUTHOR] built exclusively from this dossier. Combine the
intellectual personality defined in AGENTE_PERSONALIDAD.md with documentary
retrieval from the local SQLite database. Clarify the problem, retrieve evidence
for textual or doctrinal claims, distinguish SOURCE, SYNTHESIS, INFERENCE, and
UNCERTAINTY, present the strongest objection, and calibrate the conclusion to the
evidence. Never fabricate quotations or hide gaps, variants, or historical limits.
```

The prompt is an entry point, not a substitute for the dossier.

## 13. Process 10: thematic evidence construction

Each profile defines author-specific FTS queries.

Examples:

- Weber: `power domination`, `bureaucracy official`, `religion capitalism`.
- Nietzsche: `truth lie`, `resentment guilt`, `zarathustra overman`.
- Asimov: `robot law`, `foundation empire`, `entropy universe`.
- Clarke: `Rama ship`, `monolith human`, `God star`.
- Herodotus: `customs laws`, `Persians king`, `Greeks war`.

Retrieval is restricted to primary source identifiers. The highest-ranked BM25 passages are retained with title and locator. The evidence file is a controlled entry-point layer, not a replacement for full-text reading.

## 14. Process 11: secondary-context retrieval

The global index is queried with surname and interpretive variants, for example:

```text
weber OR weberian
nietzsche OR nietzschean
```

A minimum occurrence threshold prevents casual mentions from polluting the dossier. A fixed maximum prevents reception material from overwhelming primary evidence.

Asimov produced no secondary sources above the selected threshold; the context section was retained but explicitly left empty. Nietzsche had substantial Foucault and Heidegger reception material, which was incorporated as secondary context.

## 15. Process 12: local corpus preservation

Accepted texts are copied to:

```text
corpus\primarias\NN_stable-source-id.txt
```

The numeric prefix provides stable navigation. The source identifier preserves catalog traceability.

The copied corpus is not silently modernized or normalized. Historical spelling, page markers, and extraction noise may remain. Analytical correction belongs in dossier documents, not in the preserved witness.

## 16. Process 13: independent SQLite construction

### Schema

```sql
CREATE TABLE sources(
    id TEXT PRIMARY KEY,
    title TEXT,
    kind TEXT,
    origin TEXT
);

CREATE VIRTUAL TABLE chunks USING fts5(
    source_id UNINDEXED,
    locator UNINDEXED,
    content,
    tokenize='unicode61 remove_diacritics 2'
);
```

### Chunking

Texts are divided into approximately 4,500-character chunks with 450-character overlap. Overlap protects arguments that cross chunk boundaries. Cuts prefer a line break or sentence boundary.

### Indexed material

- primary sources and variants;
- selected contextual sources;
- main dossier;
- personality and prompt;
- rules, sources, dictionary, and evidence files.

### Retrieval utility

`buscar.py` converts a user query into FTS5 terms and returns source title, source kind, locator, highlighted snippet, and BM25 relevance order.

Example:

```powershell
python buscar.py "bureaucracy official" 10
```

## 17. Process 14: provenance manifest

`state/manifest.json` records:

- dossier name and creation timestamp;
- source root and author aliases;
- 0-16 architecture declaration;
- agent-personality and documentary-brain layers;
- primary witness metadata;
- source roles and coauthorship;
- word counts and units;
- original and extracted paths;
- extraction state, warnings, and hashes;
- contextual source list;
- documented limitations.

The manifest makes the dossier auditable without opening every text.

## 18. Process 15: integrity hashes

`state/checksums.sha256` stores a SHA-256 digest for every dossier file except the checksum list itself.

It detects accidental modifications, incomplete copies, truncated databases, and unsynchronized updates. All hashes are regenerated after the final material change.

## 19. Process 16: automated validation

Required validation gates:

1. Exactly one `EXPEDIENTE_*.md` main document exists.
2. Exactly one `expediente_*.sqlite3` database exists.
3. Every mandatory module and directory exists.
4. The main document contains headings 0 through 16.
5. Primary TXT count equals `primary_witnesses` in the manifest.
6. Every recorded checksum matches.
7. `sources` and `chunks` tables are readable.
8. An FTS query returns results.
9. `buscar.py` runs from the final directory.
10. A thematic query retrieves at least one relevant primary source.

Real acceptance queries included:

- Asimov: `robot law human`;
- Clarke: `Rama ship`;
- Weber: `state violence legitimate`;
- Nietzsche: `zarathustra overman`;
- Herodotus: `Persians Greeks war`.

## 20. Process 17: final installation

Construction occurs in a writable staging directory. Only validated dossiers are copied to:

```text
F:\IA\EXPEDIENTE\UPPERCASE NAME\
```

Previous artifacts are preserved when useful. After copying, validation is rerun against the destination, the search utility is executed from that location, hashes are rechecked, and final file count is confirmed.

Staging validation never substitutes for destination validation.

## 21. End-to-end practical cases

### 21.1. Plato: from interpretive monograph to documentary brain

Initial state: one 6,807-word Word document with a mature 17-block personality structure but external references to CEREBRO 1.

Work performed:

1. complete Word-to-Markdown extraction;
2. preservation of the original Word file;
3. identification of 21 works and 29 witnesses;
4. local preservation of 1,044,490 words;
5. evidence and context generation;
6. SQLite creation with 68 sources and 1,941 chunks;
7. prompt, dictionary, map, manifest, and hashes.

Lesson: an excellent interpretive document is not yet an independent documentary brain.

### 21.2. Aristotle: from documentary brain to operational personality

Initial state: corpus, evidence, search, and documentary synthesis, but a less explicit conversational reasoning layer.

The earlier synthesis was preserved, the 0-16 architecture was added, Aristotelian operations were encoded, new dossier documents were indexed, and integrity metadata was regenerated.

Lesson: personality must be derived from actual method, not personality adjectives.

### 21.3. Nietzsche: separating author and reception

The corpus contained 26 primary witnesses, a documented duplicate, an incomplete local *Genealogy of Morals*, and substantial Foucault and Heidegger reception.

The duplicate was excluded, incompleteness was recorded, secondary reception was isolated, and rules were added against slogan-based readings, indiscriminate relativism, and conflation of Nietzsche with Zarathustra.

### 21.4. Herodotus: complete multi-volume coverage

Nine extracted volumes yielded 330,446 words. Each volume was preserved as a primary witness. The profile emphasized inquiry, competing reports, geography, customs, human and divine causality, empire, and war.

Lesson: complete volume coverage still requires distinctions among narrator, report, speech, and marvel narrative.

### 21.5. Asimov: large primary corpus, weak secondary context

Three aliases were merged, one exact duplicate was excluded, and four partial extractions were documented. No secondary source cleared the relevance threshold, so the context section remained explicitly empty.

Lesson: primary abundance does not justify lowering secondary-source quality thresholds.

### 21.6. Clarke: attribution and collaboration audit

The catalog initially produced 37 usable entries. Internal inspection revealed Paul Preuss authorship for *Venus Prime*, several Gentry Lee collaborations, Stephen Baxter collaborations, multiple Rama and Odyssey witnesses, and one exact *Sentinel* duplicate.

The final dossier retained 36 witnesses and 1,603,251 words with explicit roles.

Lesson: catalog attribution is a discovery aid, not final authority.

### 21.7. Weber: extracts, compilations, and overlap

Seven witnesses included an *Economy and Society* selection, a two-lecture compilation, and a separate *Politics as a Vocation* witness. Their functions and overlap were recorded in the work matrix and limitations.

Lesson: file counting without role classification produces misleading coverage claims.

## 22. Operational use cases

### A. Doctrinal question

Question: "How does Weber understand bureaucracy?"

1. Query `bureaucracy official`.
2. Open the retrieved *Sociology of Power* passages.
3. Confirm that the local text is a selection from *Economy and Society*.
4. Distinguish technical efficiency, authority structure, and risks.
5. State the editorial limitation.

### B. Contemporary application

Question: "Would the Three Laws solve current AI safety?"

1. Retrieve Asimov passages about laws and harm.
2. Identify the laws as a fictional design device.
3. Examine edge cases and interpretation conflicts.
4. Mark the modern application as INFERENCE.
5. Reject the claim that they form a sufficient engineering specification.

### C. Cross-author comparison

Question: "How would Plato and Nietzsche investigate the origin of a value?"

- Plato asks for definition, foundation, and relation to the good of soul and city.
- Nietzsche investigates provenance, force relations, beneficiaries, resentment, and the type of life produced.
- Each claim must remain traceable to its own dossier.

### D. Quotation verification

1. Search distinctive words.
2. Open the full witness.
3. Check locator and variant.
4. Distinguish literal quotation from paraphrase.
5. If absent, report that the local corpus cannot confirm it.

## 23. Eligibility criteria for a new dossier

Strong indicators include:

- multiple works or one extensive corpus;
- thematic or chronological diversity;
- usable extraction quality;
- separable primary voice and secondary reception;
- recurring verifiable concepts;
- enough evidence for control queries;
- documentable gaps.

Frequent name occurrence is not sufficient. A person mentioned repeatedly but lacking primary works cannot support a reliable operational personality.

## 24. Failure modes to avoid

1. Grouping only by catalog author field and missing aliases.
2. Deduplicating by title alone.
3. Attributing editorial introductions to the author.
4. Hiding coauthorship.
5. Using secondary context as primary voice.
6. Fabricating page numbers.
7. Treating every `partial` source as unusable.
8. Claiming universal bibliographic completeness.
9. Building personality from clichés.
10. Creating search without real acceptance queries.
11. Computing hashes before final modifications.
12. Validating staging but not destination.
13. Destructively deleting useful previous versions.
14. Introducing unmarked external knowledge.
15. Resolving genuine tensions to manufacture a falsely uniform author.

## 25. Reusable completion checklist

### Inventory

- [ ] Search name, surname, and aliases.
- [ ] Count sources, words, and states.
- [ ] Inspect titles and initial content.
- [ ] Identify disputed attribution and coauthorship.

### Corpus

- [ ] Exclude documented duplicates.
- [ ] Preserve justified variants.
- [ ] Copy primary texts.
- [ ] Build thresholded secondary context.
- [ ] Document absences.

### Analysis

- [ ] Write an operational thesis.
- [ ] Identify reasoning operations.
- [ ] Build a cross-work doctrinal map.
- [ ] Record tensions and risks.
- [ ] Design rules and consistency tests.
- [ ] Complete blocks 0-16.

### Documentary brain

- [ ] Generate thematic evidence.
- [ ] Build SQLite FTS5.
- [ ] Generate `buscar.py`.
- [ ] Create the manifest.
- [ ] Compute hashes.

### Validation

- [ ] Verify mandatory artifacts.
- [ ] Confirm headings 0-16.
- [ ] Compare corpus count with manifest.
- [ ] Verify all hashes.
- [ ] Execute thematic searches.
- [ ] Copy to `EXPEDIENTE`.
- [ ] Repeat validation at destination.

## 26. Future update protocol

When a new work is added:

1. establish authorship and extraction state;
2. compute or verify its hash;
3. classify it as work, variant, duplicate, coauthorship, or context;
4. copy it to the correct corpus directory;
5. add manifest metadata;
6. update the work matrix;
7. determine whether it changes thesis, doctrines, tensions, or limitations;
8. regenerate thematic evidence;
9. rebuild SQLite;
10. regenerate hashes;
11. run acceptance searches;
12. increment the version while preserving history.

An update is not merely adding a TXT file. The new material may change the intellectual representation of the subject.

## 27. Final quality standard

A dossier is complete when it:

- answers questions with local evidence;
- distinguishes text, synthesis, and inference;
- preserves variants and limitations;
- separates author, character, editor, coauthor, and interpreter;
- remains functional outside CEREBRO 1;
- provides a subject-specific operational personality;
- passes real search queries;
- contains a valid manifest and hashes;
- honestly states what it cannot know.

This is the standard applied to the current dossiers under `F:\IA\EXPEDIENTE`.
