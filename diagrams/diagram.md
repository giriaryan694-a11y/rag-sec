# RAG-SEC Diagrams (SVGs embedded)

This file contains the main diagrams for the RAG-SEC handbook as **inline SVG** so you can paste them directly into README.md or view them in the canvas.

> Tip: Right-click any SVG and choose "Save as" → SVG to export, or copy the SVG node into a vector editor for PNG exports.

---

## Diagram 1 — RAG Architecture (Flow)

<svg viewBox="0 0 900 260" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="RAG architecture" width="900" height="260">
  <defs>
    <linearGradient id="g1" x1="0" x2="1"><stop offset="0" stop-color="#2563eb"/><stop offset="1" stop-color="#7c3aed"/></linearGradient>
    <filter id="f1" x="-20%" y="-20%" width="140%" height="140%"><feDropShadow dx="0" dy="6" stdDeviation="10" flood-color="#0b1220"/></filter>
    <marker id="arrow" markerWidth="10" markerHeight="10" refX="6" refY="5" orient="auto"><path d="M0,0 L10,5 L0,10 z" fill="#cbd5e1"/></marker>
  </defs>

  <!-- User Query -->

  <rect x="40" y="24" rx="12" ry="12" width="200" height="60" fill="url(#g1)" opacity="0.95" filter="url(#f1)" />
  <text x="140" y="60" text-anchor="middle" font-size="16" fill="#fff">User Query</text>

  <!-- Retriever -->

  <rect x="330" y="24" rx="12" ry="12" width="200" height="60" fill="#0ea5a1" opacity="0.95"/>
  <text x="430" y="60" text-anchor="middle" font-size="16" fill="#012">Retriever</text>

  <!-- KB -->

  <rect x="620" y="24" rx="12" ry="12" width="200" height="60" fill="#f97316" opacity="0.95"/>
  <text x="720" y="60" text-anchor="middle" font-size="16" fill="#051">Knowledge Base (KB)</text>

  <!-- arrows -->

  <path d="M240 54 L330 54" stroke="#cbd5e1" stroke-width="3" fill="none" marker-end="url(#arrow)" />
  <path d="M530 54 L620 54" stroke="#cbd5e1" stroke-width="3" fill="none" marker-end="url(#arrow)" />

  <!-- LLM Generator -->

  <rect x="330" y="130" rx="16" ry="16" width="300" height="80" fill="#60a5fa" opacity="0.95"/>
  <text x="480" y="175" text-anchor="middle" font-size="16" fill="#012">LLM Generator</text>

  <!-- retrieved docs arrow down -->

  <path d="M720 84 L480 130" stroke="#cbd5e1" stroke-width="3" fill="none" marker-end="url(#arrow)" />

  <!-- output -->

  <rect x="330" y="220" rx="12" ry="12" width="300" height="40" fill="#22c55e"/>
  <text x="480" y="247" text-anchor="middle" font-size="14" fill="#021">Final Response (Output)</text>
</svg>

---

## Diagram 2 — RAG Attack Surface (Layered)

<svg viewBox="0 0 900 420" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="RAG attack surface" width="900" height="420">
  <style>.l{font-size:13px;fill:#0f172a}</style>

  <rect x="60" y="20" width="780" height="56" rx="10" fill="#0ea5a1"/>
  <text x="100" y="56" fill="#081" font-size="14">User Query Layer</text>
  <text x="720" y="56" fill="#7f1d1d" font-size="13">(Prompt Injection)</text>

  <rect x="60" y="96" width="780" height="56" rx="10" fill="#38bdf8"/>
  <text x="100" y="132" fill="#022" font-size="14">Embedding Model</text>
  <text x="720" y="132" fill="#7f1d1d" font-size="13">(Adversarial Inputs)</text>

  <rect x="60" y="172" width="780" height="56" rx="10" fill="#f97316"/>
  <text x="100" y="208" fill="#041" font-size="14">Vector DB / Retriever</text>
  <text x="720" y="208" fill="#7f1d1d" font-size="13">(Retrieval Manipulation)</text>

  <rect x="60" y="248" width="780" height="56" rx="10" fill="#7c3aed"/>
  <text x="100" y="284" fill="#fff" font-size="14">Knowledge Base (Documents)</text>
  <text x="720" y="284" fill="#fce" font-size="13">(Data Poisoning / Metadata)</text>

  <rect x="60" y="324" width="780" height="56" rx="10" fill="#60a5fa"/>
  <text x="100" y="360" fill="#012" font-size="14">LLM Generator</text>
  <text x="720" y="360" fill="#7f1d1d" font-size="13">(Jailbreak / Hallucination)</text>
</svg>

---

## Diagram 3 — Defense Pipeline (Conceptual)

<svg viewBox="0 0 900 220" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="defense pipeline" width="900" height="220">
  <defs>
    <marker id="a" markerWidth="10" markerHeight="10" refX="6" refY="5" orient="auto"><path d="M0,0 L10,5 L0,10 z" fill="#e6eef8"/></marker>
  </defs>
  <rect x="40" y="30" width="160" height="60" rx="10" fill="#0ea5a1"/>
  <text x="120" y="60" text-anchor="middle" font-size="13" fill="#012">Input Validation</text>

  <rect x="240" y="30" width="160" height="60" rx="10" fill="#38bdf8"/>
  <text x="320" y="60" text-anchor="middle" font-size="13" fill="#012">Sanitize & Normalize</text>

  <rect x="440" y="30" width="160" height="60" rx="10" fill="#7c3aed"/>
  <text x="520" y="60" text-anchor="middle" font-size="13" fill="#fff">KB Verification</text>

  <rect x="640" y="30" width="160" height="60" rx="10" fill="#f97316"/>
  <text x="720" y="60" text-anchor="middle" font-size="13" fill="#012">Retrieval Filters</text>

  <path d="M200 60 L240 60" stroke="#e6eef8" stroke-width="3" marker-end="url(#a)"/>
  <path d="M400 60 L440 60" stroke="#e6eef8" stroke-width="3" marker-end="url(#a)"/>
  <path d="M600 60 L640 60" stroke="#e6eef8" stroke-width="3" marker-end="url(#a)"/>

  <rect x="320" y="120" width="260" height="60" rx="12" fill="#60a5fa"/>
  <text x="450" y="150" text-anchor="middle" font-size="13" fill="#012">LLM + Output Filters</text>

  <path d="M720 60 L450 120" stroke="#e6eef8" stroke-width="2" fill="none" marker-end="url(#a)"/>
</svg>

---

## Usage

* Paste the SVGs directly into Markdown or HTML files to embed the vector diagrams.
* Export as SVG/PNG for README images if you prefer raster images.

---

*Saved as `diagrams/diagrams_md` in the canvas.*
  
