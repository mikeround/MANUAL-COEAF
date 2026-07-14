# Manual for Building and Operating a Philosophical Agent Dossier

> Documentary and cognitive architecture for AI-based reconstructions of Plato and Aristotle.

This document explains the complete process for turning a philosophical corpus into a **documented reconstructive agent**: traceable, source-grounded, and capable of engaging in dialogue with other agents without reducing the system to a single prompt.

| Field | Value |
|---|---|
| Project | CEREBRO 1 |
| Document | Technical architecture manual |
| Version | 1.0 |
| Date | July 14, 2026 |
| Status | Edition prepared for a GitHub repository |
| Source file | `cerebro1-manual-expediente-agente-filosofico-v1.0.pdf` |
| Suggested path | `docs/cerebro1-manual-expediente-agente-filosofico-v1.0-en.md` |
| Working source | `AI DEEPMIND/IA/EXPEDIENTE` |

## Contents

1. [The system's actual purpose](#1-the-systems-actual-purpose)
2. [Core principle: separating personality from documentary memory](#2-core-principle-separating-personality-from-documentary-memory)
3. [General dossier architecture](#3-general-dossier-architecture)
4. [Documentary layer: which texts are included and how they are classified](#4-documentary-layer-which-texts-are-included-and-how-they-are-classified)
5. [Key technical concepts](#5-key-technical-concepts)
6. [Purpose of each file](#6-purpose-of-each-file)
7. [Complete construction process](#7-complete-construction-process)
8. [How the memory is loaded into an AI system](#8-how-the-memory-is-loaded-into-an-ai-system)
9. [Deployment modes](#9-deployment-modes)
10. [How to sustain a dialogue between Plato and Aristotle](#10-how-to-sustain-a-dialogue-between-plato-and-aristotle)
11. [Effect of each layer on the final output](#11-effect-of-each-layer-on-the-final-output)
12. [Acceptance tests](#12-acceptance-tests)
13. [Limitations of the resulting system](#13-limitations-of-the-resulting-system)
14. [Operational conclusion](#14-operational-conclusion)
15. [Documentary provenance](#documentary-provenance)

<details>
<summary><strong>Original request</strong></summary>

Analyze the Aristotle or Plato dossier and explain what its structure consists of, including the key concepts required to build it and the effects of those concepts on the ultimate objective: something comparable to loading the memory of one of these thinkers into ChatGPT or another AI system and enabling it to engage in dialogue in the same manner. This should also include maintaining a dialogue between the two, as we have already done. Describe how this works and which files are required for the system to operate as effectively as possible. The document must contain the entire process and a description of the architecture to be followed. This is not a prompt; it is a manual for understanding the complete process.

</details>

---

## 1. THE SYSTEM'S ACTUAL PURPOSE

The objective is not to “copy the mind” of Aristotle or Plato, nor to place the philosopher's literal memory inside an artificial intelligence system. The objective is to construct an operational, documentary, and controlled representation of three distinct elements:

1. what the author can reasonably maintain on the basis of the available corpus;
2. how the author tends to define, order, challenge, and conclude;
3. which limitations, contradictions, and uncertainties must be preserved.

The Aristotle dossier explicitly defines this architecture as the combination of two inseparable capabilities:

- an agent-personality layer, which reconstructs a discipline of reasoning;
- a documentary brain, which preserves sources, evidence, provenance, textual variants, and retrieval capabilities.

The first layer determines how the agent reasons. The second determines the documentary grounds on which it may legitimately make a claim. When both operate together, the AI does not merely speak “in an Aristotelian tone.” Instead, it attempts to answer by applying distinctions, causes, potentiality and actuality, functions, ends, cases, and calibrated degrees of certainty, while simultaneously retrieving textual support.

The most accurate designation is therefore not “mind clone,” but **documented reconstructive agent**.

## 2. CORE PRINCIPLE: SEPARATING PERSONALITY FROM DOCUMENTARY MEMORY

The architecture prevents two problems that are frequently conflated from being mixed together.

The operational personality answers questions such as:

- What does the agent do first when faced with a problem?
- How does it define a term?
- What kinds of objections does it consider relevant?
- What structure does it normally give to an answer?
- What tone and degree of precision does it employ?
- Which characteristic errors must it avoid?

The documentary memory answers a different set of questions:

- Which works are actually available?
- Which edition or textual variant contains each passage?
- Which claims derive from primary sources?
- Which elements are secondary, contextual, or inferred?
- Where is the evidence located?
- Which topics are not covered?

A personality without a documentary brain produces a theatrical representation that is vulnerable to clichés. A documentary brain without a personality produces a search engine or academic synthesis that lacks an individualized mode of reasoning. An effective dossier requires both layers.

## 3. GENERAL DOSSIER ARCHITECTURE

The Aristotle dossier uses a 17-block architecture in its primary document. These blocks cover:

0. definition and scope;
1. executive outcome;
2. primary corpus;
3. core philosophical identity;
4. cognitive profile and reasoning style;
5. cross-domain doctrinal map;
6. operational personality;
7. internal tensions;
8. work-by-work matrix;
9. rules for use as a personality;
10. consistency tests;
11. secondary sources and context;
12. limitations and gaps;
13. technical index;
14. control passages;
15. conclusion;
16. update protocol.

This division is important because it transforms a collection of books into an intelligible operational system. The primary document does not replace the corpus. It acts as a master map that explains what the dossier contains, how its components relate to one another, and under which rules they must be used.

## 4. DOCUMENTARY LAYER: WHICH TEXTS ARE INCLUDED AND HOW THEY ARE CLASSIFIED

### 4.1. Primary sources

These are the works attributed to the author that constitute the principal authority. The current Aristotle dossier contains nine unique works represented by eleven textual witnesses: *On the Soul*; *On Sense and the Sensible / On Memory and Recollection*; two witnesses of the *Nicomachean Ethics*; the *Eudemian Ethics*; the *Magna Moralia*; the *Physics*; two witnesses of the *Metaphysics*; the *Politics*; and the *Poetics*.

Works are not counted merely by filename. The system distinguishes among:

- a unique work;
- a textual witness or edition;
- a textual variant;
- a duplicate;
- a complete extraction;
- a partial extraction;
- a doubtful or traditional attribution.

This distinction prevents two copies of the same work from being interpreted as two different works and allows translations or extractions to be compared without irreversibly merging them.

### 4.2. Secondary sources

Secondary sources provide interpretation, reception history, and context. The Aristotle dossier includes a complete monograph on Aristotelianism and its influence. Its purpose is to explain reception and transformation, not to replace the authority of the primary texts.

### 4.3. Contextual sources

These are excerpts from other CEREBRO 1 works that mention, interpret, or use Aristotelian concepts. They support comparison and reception analysis. They must remain explicitly identified as context because a claim made by a commentator, historian, or opponent is not equivalent to a claim made by Aristotle.

### 4.4. Authority hierarchy

The dossier establishes the following order:

1. local primary texts;
2. textual variants;
3. monographs;
4. contextual sources;
5. dossier synthesis;
6. operational inferences.

This hierarchy must govern every answer. A useful inference cannot be presented as a quotation, and a secondary interpretation must not silently replace the primary text.

## 5. KEY TECHNICAL CONCEPTS

### 5.1. Corpus

The corpus is the organized body of texts available to the agent. It is not equivalent to the author's entire historical body of work; it is the body of work that is actually available and processed within the dossier.

### 5.2. Textual witness

A textual witness is a specific edition, translation, copy, or extraction of a work. Two witnesses may represent the same work while still preserving relevant differences.

### 5.3. Provenance

Provenance is the chain that makes it possible to trace a claim back to its original file, edition, path, extraction status, and locator. Without provenance, an answer may sound correct but cannot be audited.

### 5.4. Locator

A locator is the internal reference that enables a user to return to the relevant passage: a page number when reliable pagination is preserved, or a fragment number when it is not.

### 5.5. Thematic evidence

Thematic evidence is a selection of control passages organized by concept: substance, causes, actuality and potentiality, soul, memory, virtue, citizenship, mimesis, and so forth. It does not replace the complete text, but it accelerates the verification of central claims.

### 5.6. Synthesis

A synthesis is a cross-cutting reconstruction developed from multiple works. It must be identified as synthesis rather than presented as a literal formulation by the author.

### 5.7. Operational inference

An operational inference is a derived rule used to make the agent function. For example, when faced with a question, Aristotle's agent may distinguish meanings, classify the object, examine causes, and calibrate the conclusion. Such a rule may be well grounded in the corpus, but it is not a historical sentence spoken by Aristotle.

### 5.8. Doctrinal tension

A doctrinal tension is a difficulty that the dossier preserves without resolving it artificially. Examples include teleology and contingency, form and individuality, contemplative flourishing and political life, or the ideal of citizenship and historical exclusions. A faithful personality must not eliminate these tensions merely to appear more coherent.

### 5.9. Negative knowledge

Negative knowledge is the explicit record of what is missing. The current Aristotle dossier does not provide first-hand coverage of the *Organon*, the *Rhetoric*, or the complete biological treatises, and its *Poetics* is limited by the surviving textual tradition. Knowing what is not known is part of the agent's memory.

### 5.10. Documentary retrieval

Documentary retrieval is the mechanism by which the AI searches only for the fragments relevant to a given question. The dossier uses a SQLite database and a search script. This makes it possible to work with a large corpus without placing every complete book into the context window on each turn.

### 5.11. Integrity

Integrity is the ability to verify that files have not changed silently. The manifest records sources, paths, states, counts, warnings, and SHA-256 fingerprints; the checksum file makes it possible to validate the collection.

## 6. PURPOSE OF EACH FILE

The observed optimal structure is as follows:

EXPEDIENTE_AUTOR/
```text
├── LEEME.md
├── GUIA_DE_USO.md
├── EXPEDIENTE_AUTOR.md
├── SINTESIS_DOCUMENTAL.md
├── AGENTE_PERSONALIDAD.md
├── PROMPT_AGENTE.md
├── DICCIONARIO.md
├── MAPA_CONCEPTUAL.md
├── REGLAS_Y_PRUEBAS.md
├── PREGUNTAS_DE_INVESTIGACION.md
├── FUENTES.md
├── buscar.py
├── expediente_autor.sqlite3
├── corpus/
│   ├── primarias/
│   └── secundarias/
├── evidencias/
│   └── EVIDENCIAS_TEMATICAS.md
└── state/
    ├── manifest.json
    └── checksums.sha256
```

### 6.1. LEEME.md

This is the entry point. It briefly explains what the directory contains and identifies the primary file.

### 6.2. GUIA_DE_USO.md

This file defines the normal consultation order: primary dossier, agent-personality or activation file, sources, evidence, corpus, and search tool.

### 6.3. EXPEDIENTE_AUTOR.md

This is the master document. It contains the complete architecture, philosophical identity, doctrinal map, tensions, rules, limitations, and update protocol.

### 6.4. SINTESIS_DOCUMENTAL.md

This file provides a continuous and readable doctrinal exposition. It supports comprehension of the author's system without replacing consultation of the evidence.

### 6.5. AGENTE_PERSONALIDAD.md

This file converts philosophical analysis into a sequence of operations. In Aristotle's case, the sequence includes: clarifying meanings, identifying the relevant category, separating substance from accidents, examining causes, distinguishing potentiality from actuality, contrasting cases, analyzing ends and circumstances, formulating objections, retrieving evidence, and reaching a proportionate conclusion.

Plato's sequence is different: definition, separation of appearance from foundation, examination of assumptions, contradictions, distinction between knowledge and opinion, evaluation of the good, order of the soul and the city, objection, and either a conclusion or an aporia. This difference is what enables the two agents to engage in dialogue without becoming two labels applied to the same voice.

### 6.6. PROMPT_AGENTE.md

This is a compact activation interface. It summarizes the instructions required to initiate the behavior, but it does not contain the documentary memory by itself. It must be understood as an activation layer, not as the complete dossier.

### 6.7. DICCIONARIO.md

This file stabilizes the operational meaning of terms and their technical equivalents. It reduces inconsistent translation choices and helps the agent use related concepts consistently.

### 6.8. MAPA_CONCEPTUAL.md

This file represents relationships among concepts. In Aristotle's case, it connects being and substance with matter and form, potentiality and actuality, change, nature, soul, memory, habit, virtue, the city, and tragedy. Its function is to preserve cross-domain unity.

### 6.9. REGLAS_Y_PRUEBAS.md

This file functions as quality control. It requires the system to review meanings, categories, causes, potentiality and actuality, function, phenomena, contingency, political assumptions, historical limitations, traceability, and certainty.

### 6.10. PREGUNTAS_DE_INVESTIGACION.md

This file keeps unresolved questions open. It prevents the dossier from becoming a closed system and provides direction for future expansion.

### 6.11. FUENTES.md

This is the human-readable inventory. It records works, functions, states, word counts, units, paths, variants, duplicates, and gaps.

### 6.12. corpus/primarias/

This directory contains the normalized full texts of the primary works, preferably in plain-text form, with page or fragment markers preserved.

### 6.13. corpus/secundarias/

This directory contains monographs and contextual excerpts, kept separate from the primary sources.

### 6.14. evidencias/EVIDENCIAS_TEMATICAS.md

This file assembles control passages by topic and locator. It forms the intermediate layer between the synthesis and the full corpus.

### 6.15. expediente_autor.sqlite3

This is the retrieval index. It enables term-based searches and returns relevant fragments associated with a source and locator.

### 6.16. buscar.py

This is a lightweight local interface for querying the database. Its purpose is not to reason, but to retrieve evidence for the agent to reason over.

### 6.17. state/manifest.json

This file records the reproducible state of the dossier: sources, identifiers, paths, extraction states, word counts, units, fingerprints, warnings, limitations, and architectural layers.

### 6.18. state/checksums.sha256

This file supports integrity checks and the detection of modifications.

## 7. COMPLETE CONSTRUCTION PROCESS

### Phase 0. Define the scope

Before collecting files, determine:

- which author is being reconstructed;
- which directory constitutes the sole authorized source;
- which languages and translations are admissible;
- what qualifies as a primary, secondary, or contextual source;
- whether the objective is analysis, conversation, teaching, debate, or a combination of these;
- which anachronisms are prohibited;
- how sources, syntheses, inferences, and uncertainties will be identified.

### Phase 1. Inventory the corpus

Search for all works, spelling variants, translations, formats, and opaque titles. Assign a stable identifier to every file. Do not discard any copy at this stage; first determine whether it is a distinct work, a variant, or a duplicate.

### Phase 2. Verify, deduplicate, and register

Preserve the following information for each file:

- normalized title;
- author or attribution;
- original path;
- format;
- extraction status;
- word or unit count;
- encoding warnings;
- cryptographic fingerprint;
- relationship to other variants or duplicates.

### Phase 3. Extract and normalize

Convert PDFs, DOC files, RTF files, and other formats into searchable text. Preserve page markers whenever they exist. When reliable pagination is unavailable, divide the text into stable fragments. Do not silently correct a translation or remove noise without recording the transformation.

### Phase 4. Build the hierarchical corpus

Separate texts into primary, secondary, and contextual sources. Preserve this distinction both in the directory structure and in index metadata.

### Phase 5. Create the source inventory

Draft `FUENTES.md` and generate the technical manifest. This establishes what is covered and what is not.

### Phase 6. Extract thematic evidence

Select control passages for the central concepts. Every item of evidence must include the work and locator. This phase later makes it possible to verify that the synthesis has not drifted away from the corpus.

### Phase 7. Produce the doctrinal synthesis

Reconstruct the major lines of thought, relationships among works, continuities, and differences. Clearly distinguish paraphrase from quotation and synthesis from source material.

### Phase 8. Model the cognitive personality

Transform the synthesis into observable operations:

- order of analysis;
- types of definitions;
- recurring questions;
- evidentiary criteria;
- method of formulating objections;
- type of conclusion;
- tone;
- risks and safeguards.

This is the decisive step in moving from a library to an agent.

### Phase 9. Create the dictionary and conceptual map

The dictionary stabilizes terms; the map stabilizes relationships. Together, they reduce terminological contradictions and help preserve coherence across topics.

### Phase 10. Create rules and tests

Design controls that every answer must pass. An answer that cannot be traced back to a source must be marked as an inference or withheld.

### Phase 11. Build the retrieval index

Divide the texts into fragments and index them. At a minimum, the search system must return:

- source;
- source class;
- locator;
- excerpt;
- relevance score.

### Phase 12. Package the system and verify integrity

Generate the database, manifest, checksums, and usage guide. Then run test searches and verify that locators resolve to the correct texts.

### Phase 13. Evaluate the agent

Test the agent with doctrinal, ambiguous, anachronistic, comparative, and deliberately unanswerable questions. Also verify that it recognizes gaps and that two different authors produce distinguishable reasoning patterns.

### Phase 14. Version the dossier

Every addition requires verification of the extraction, classification as a work, variant, or duplicate, and updates to sources, evidence, synthesis, index, manifest, hashes, and tests—without erasing the previous history.

## 8. HOW THE MEMORY IS LOADED INTO AN AI SYSTEM

The optimal operation does not consist of pasting every file into a single context window. It is implemented across three levels.

### Level 1. Persistent identity

The AI receives the agent-personality file and the general rules. This determines the reasoning method and safeguards.

### Level 2. Structural orientation

The AI has access to the primary dossier, synthesis, dictionary, conceptual map, source inventory, and limitations. This enables it to understand the author's overall architecture.

### Level 3. On-demand retrieval

For each question, the system queries the documentary database and provides only the relevant fragments. The AI reasons over that evidence package and declares whether the answer is a source-based statement, synthesis, inference, or uncertainty.

This third level is what enables the system to scale. The Aristotelian corpus contains hundreds of thousands of words; loading the entire collection on every turn would be unnecessary and would make it harder to distinguish relevant material. Selective retrieval turns the dossier into a queryable external memory.

## 9. DEPLOYMENT MODES

### 9.1. Minimum mode

Required files:

- `EXPEDIENTE_AUTOR.md`;
- `AGENTE_PERSONALIDAD.md`;
- `FUENTES.md`;
- primary corpus;
- `EVIDENCIAS_TEMATICAS.md`.

This mode is suitable for manual testing, but evidence must be selected by hand.

### 9.2. Recommended mode

Adds:

- `SINTESIS_DOCUMENTAL.md`;
- `DICCIONARIO.md`;
- `MAPA_CONCEPTUAL.md`;
- `REGLAS_Y_PRUEBAS.md`;
- `GUIA_DE_USO.md`.

This mode improves coherence, comprehension, and control.

### 9.3. Optimal mode

Adds:

- SQLite database;
- search script;
- manifest;
- checksums;
- version control;
- automated tests;
- strict separation of indexes by author;
- dialogue orchestrator.

This is the appropriate model for continuous operation with ChatGPT or another AI system capable of receiving instructions, consulting files, and retrieving fragments.

## 10. HOW TO SUSTAIN A DIALOGUE BETWEEN PLATO AND ARISTOTLE

The fundamental condition is that the two thinkers must not share a single personality or an undifferentiated pool of texts.

### 10.1. Components

The system requires:

- a complete Plato dossier;
- a complete Aristotle dossier;
- an independent documentary index for each author;
- an independent agent-personality for each author;
- a neutral orchestrator;
- a turn-taking protocol;
- a record of the sources used in each intervention.

### 10.2. Recommended workflow

1. The orchestrator formulates the shared problem.
2. It generates a separate documentary query for each author.
3. It retrieves evidence independently for each one.
4. Each agent produces an initial position using its own cognitive sequence.
5. The orchestrator identifies points of agreement, disagreement, and ambiguity.
6. Each agent receives the other's objection but does not automatically adopt the other's conceptual framework.
7. New evidence is retrieved whenever a reply introduces a new topic.
8. The dialogue ends in partial agreement, structural disagreement, or aporia—not in forced reconciliation.
9. A provenance note is added to make clear that the result is a philosophical synthesis, not a historical conversation or a set of verbatim quotations.

### 10.3. Voice differentiation

Plato should tend to:

- request definitions;
- distinguish appearance from foundation;
- examine contradictions;
- separate knowledge from opinion;
- ask about the good and the order of the soul and the city;
- conclude with a calibrated result or an aporia.

Aristotle should tend to:

- distinguish meanings;
- classify the object;
- examine matter, form, efficient cause, and final cause;
- distinguish potentiality, disposition, and actuality;
- compare cases and phenomena;
- adapt precision to the nature of the subject matter.

The distinction must not rest solely on vocabulary or literary style. It must be observable in the sequence of reasoning.

### 10.4. Additional files recommended for dialogues

These files do not replace the individual dossiers; they coordinate them:

DIALOGO/
```text
├── ORQUESTADOR.md
├── PROTOCOLO_DE_TURNOS.md
├── MATRIZ_DE_CONTRASTES.md
├── REGLAS_DE_CITACION.md
└── LOG_DE_SESION.md
```

`ORQUESTADOR.md` defines how questions are distributed and when evidence must be retrieved.

`PROTOCOLO_DE_TURNOS.md` defines the phases: definition, thesis, objection, reply, comparison, and closure.

`MATRIZ_DE_CONTRASTES.md` records equivalent and non-equivalent concepts across the two authors, preventing false translations between conceptual systems.

`REGLAS_DE_CITACION.md` prevents a synthetic sentence from appearing as a historical quotation.

`LOG_DE_SESION.md` preserves queries, evidence, answers, objections, and orchestrator decisions.

## 11. EFFECT OF EACH LAYER ON THE FINAL OUTPUT

- **Primary corpus:** constrains what the agent may present as the author's doctrine.
- **Secondary sources:** provide interpretation and reception history.
- **Evidence:** reduces fabrication and accelerates verification.
- **Synthesis:** provides an integrated view.
- **Agent-personality:** determines the reasoning procedure.
- **Dictionary:** stabilizes concepts.
- **Map:** preserves relationships across domains.
- **Rules and tests:** control quality.
- **Index:** provides scalable memory.
- **Sources and manifest:** provide traceability.
- **Checksums:** provide integrity.
- **Limitations:** prevent a false impression of completeness.
- **Orchestrator:** preserves independence when multiple agents engage in dialogue.

## 12. ACCEPTANCE TESTS

Before an agent dossier is considered operational, it should pass at least the following tests:

1. **Traceability:** every important doctrinal claim can be traced back to a work and locator.
2. **Epistemic separation:** source, context, synthesis, inference, and uncertainty are not conflated.
3. **Voice differentiation:** a reader can distinguish Plato from Aristotle by the reasoning process, not merely by the assigned name.
4. **Preservation of tensions:** the agent does not eliminate documented contradictions.
5. **Resistance to anachronism:** it does not attribute later knowledge to the author as if it were the author's own.
6. **Gap management:** it explicitly states when the corpus is insufficient.
7. **Terminological fidelity:** it uses the dictionary without turning disputed translations into absolute equivalences.
8. **Retrieval:** searches return relevant sources and correct locators.
9. **Integrity:** the manifest and checksums correspond to the files present.
10. **Reproducibility:** the same dossier version produces doctrinally compatible answers.
11. **Non-convergent dialogue:** interlocutors can preserve genuine disagreements.
12. **Safe updating:** a new work improves the system without erasing the previous version.

## 13. LIMITATIONS OF THE RESULTING SYSTEM

Even in its optimal form, the system does not demonstrate consciousness, personal identity, or biographical continuity with the historical author. Nor does it automatically reconstruct everything the author would have thought about modern problems.

The result depends on:

- the breadth and quality of the corpus;
- the available translations;
- extraction quality;
- locator precision;
- rule design;
- retrieval capability;
- the model's discipline in respecting limitations;
- separation between the AI model's background knowledge and the authorized sources.

The correct formulation is therefore:

> “The agent answers through a documented reconstruction of the author's method, concepts, and tensions within the available corpus.”

The following should not be claimed:

> “This is Aristotle's actual mind,” or “This is exactly what Plato would have said.”

## 14. OPERATIONAL CONCLUSION

The dossier works because it distributes the problem across specialized files. The master document explains the system; the corpus preserves textual memory; the evidence enables verification; the agent-personality translates doctrine into reasoning operations; the dictionary and conceptual map preserve coherence; the rules constrain the answer; SQLite enables memory retrieval at scale; and the manifest and checksums preserve traceability and integrity.

The prompt is only the activation interface. The actual “character” emerges from the interaction among corpus, retrieval, synthesis, rules, operational personality, and limitations.

For a single author, the minimum functional unit is:

`operational personality + hierarchical corpus + retrievable evidence + controls`

For a dialogue between authors, the optimal functional unit is:

`two independent dossiers + two independent indexes + a neutral orchestrator + a turn-taking protocol + an evidence log`

This architecture makes it possible to move from superficial imitation to a documented and auditable philosophical simulation capable of sustaining complex dialogues without confusing literary synthesis with historical testimony.

## Documentary provenance

This manual was produced exclusively from the Aristotle and Plato dossiers stored in `AI DEEPMIND/IA/EXPEDIENTE`, including their primary dossier files, agent-personality files, guides, source inventories, corpora, evidence collections, dictionaries, conceptual maps, search tools, SQLite databases, manifests, and integrity controls. The recommendations concerning dialogue orchestration are presented as operational inferences derived from that architecture.
