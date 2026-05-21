# Citation-Critical RAG

**Not summaries. Proof.**

![Python](https://img.shields.io/badge/Python-3.11+-blue?style=flat-square) ![FastAPI](https://img.shields.io/badge/FastAPI-backend-009688?style=flat-square) ![React](https://img.shields.io/badge/React-frontend-61DAFB?style=flat-square) ![License](https://img.shields.io/badge/License-Proprietary-red?style=flat-square)

---

## The Problem

Organizations working with large volumes of regulatory, compliance, or legal documents face a specific and consequential failure with current AI tools. Popular enterprise tools and custom-built RAG pipelines return answers that read fluently and cite sources. They name a document. Sometimes a page number. But they cannot return the exact sentence, from the exact section, on the exact page — verbatim, traceable, provable.

The answer is rephrased. The citation is decorative.

In domains where documents are the source of truth and citations are evidence — this is not acceptable. Nuclear regulatory, pharmaceutical, legal, financial compliance, defense procurement. Any domain where a wrong citation has consequences beyond inconvenience. Where an auditor, a regulator, or a court will ask: where exactly does it say that? And the answer must be a precise location in a primary document, not a confident paraphrase of one.

Current tools are not built for this requirement. They are built for convenience. Convenience is not the same as correctness, and in citation-critical domains, the difference matters.

---

## What This System Does

This system ingests structured regulatory documents and makes them queryable with exact citation fidelity. Every answer is verbatim text pulled directly from the source document. Every answer carries the exact section number, section title, and page number. Nothing is paraphrased. Nothing is synthesized. If the answer is not present in the document, the system returns nothing — not a guess, not a rephrasing, nothing.

---

## The Hard Problems

**Document structure preservation**
Regulatory documents have five or more levels of hierarchy — chapters, sections, subsections, tables, bullet lists. Standard parsers flatten this into plain text, discarding all structural information. Every element must be preserved with its complete lineage intact.

**Intelligent chunking with full traceability**
Token-based chunking cuts mid-sentence, mid-regulation, mid-table. Every chunk must know its exact position in the document hierarchy — which section, which subsection, which page — and carry that information as structured metadata, not as an afterthought.

**Document connectivity**
Every element of a regulatory document is connected to every other relevant element. A retrieved fragment must carry enough context to know where it sits in the broader document — what surrounds it, what it belongs to, what it qualifies. Disconnected fragments produce disconnected answers.

**Domain-aware retrieval**
Generic embedding models do not understand domain-specific terminology. Regulatory acronyms, technical standards, citation formats are domain language. Retrieval must understand this language, not treat it as rare tokens that dilute semantic signal.

**Verbatim extraction enforcement**
Every language model wants to paraphrase. Enforcing verbatim extraction at the output layer while maintaining retrieval quality requires specific architectural choices at every stage of the pipeline — not just at the final generation step.

**Citation validation**
The system must verify that every returned citation actually exists verbatim in the retrieved source. Hallucinated citations — confident answers that cannot be traced back to the source — are worse than no answer. They create false evidence.

---

## Architecture

```
Document Input
      ↓
Document Parser — structure preserved
      ↓
Intelligent Chunker — hierarchy maintained
      ↓
Metadata Enrichment — full traceability attached
      ↓
Domain Classification — content categorized
      ↓
Intelligent Embedding — domain-aware representation
      ↓
Vector Storage — metadata indexed
      ↓
Intelligent Retrieval — precision-optimized search
      ↓
Verbatim Extraction — exact citation returned
      ↓
Citation Output — section, page, verbatim text
```

Each stage is a deliberate architectural decision. Implementation is proprietary.

---

## Sample Output

The distinction is not subtle.

**What generic RAG returns:**

```
"The fuel system meets applicable regulatory requirements
with appropriate safety margins maintained during normal
operations and anticipated operational occurrences."

Document: ML20205L411 | Page: 4
```

**What this system returns:**

```
Section 4.2.3 "Regulatory Basis", Page 4-3:

"GDC 27, Combined Reactivity Control Systems Capability,
as it relates to the reactivity control systems being
designed with appropriate margin and, in conjunction with
the ECCS, being capable of controlling reactivity to
maintain the capability of cooling the core under
postulated accident conditions"

Section 4.2.3 "Regulatory Basis", Page 4-3:

"GDC 35, Emergency Core Cooling, as it relates to
designing the reactor fuel system such that the
performance of the ECCS will not be compromised
following a postulated accident"
```

---

## Applicability

This system is domain-agnostic at the architectural level. The parsing, chunking, hierarchy preservation, and extraction layers work for any structured document corpus. Domain-specific components — classification rules, embedding models, metadata schema — are configurable per deployment.

Applicable wherever documents are the source of truth and citations are evidence:

- Nuclear regulatory
- Pharmaceutical and clinical
- Legal and compliance
- Financial regulation
- Defense and procurement

---

## Status

| Component | Status |
|-----------|--------|
| Core pipeline | ✅ Complete |
| NRC document corpus | ✅ Validated |
| End-to-end citation extraction | ✅ Validated |
| Multi-regulatory body support | 🔄 In progress |
| Production deployment | 🔄 In progress |

---

## Contact

This repository contains architecture documentation only.  
Implementation is proprietary.

For serious inquiries — regulatory organizations, enterprise compliance teams, or domain-specific deployments:

**LinkedIn:** [Hassan Abdullah](https://www.linkedin.com/in/hassan--abdullah)
