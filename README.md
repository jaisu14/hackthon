# ClauseGuard AI — Legal Contract Risk & Contradiction Analyzer

> **Hackathon MVP**: Detect hidden contract risks, cross-jurisdiction conflicts, and clause contradictions before they become legal problems.

---

## 🚀 Overview

**ClauseGuard AI** is a legal-tech SaaS application that extracts, classifies, and audits legal contracts (PDF, DOCX, and text) against a predefined safe-contract ruleset. 

The core feature is the **Contradiction Engine**, which reliably detects and highlights conflicting clauses with side-by-side textual evidence (e.g., unlimited indemnity vs. a $50,000 liability cap).

---

## ✨ Key Capabilities

1. **Document Processing & Clause Extraction**
   - Supports **PDF** (via PyMuPDF/pdfjs extraction) and **DOCX** (via python-docx/mammoth).
   - Segments raw contract text into numbered clauses, sections, headings, titles, and page boundaries.

2. **Clause Classification**
   - Categorizes clauses into 14 standard legal categories: *Limitation of Liability, Indemnity, Termination, Intellectual Property, Confidentiality, Governing Law, Dispute Resolution, Payment, Warranty, Data Protection / GDPR, Force Majeure, Insurance, Assignment, Non-Compete*.

3. **Predefined Safe Ruleset (`rules.json`)**
   - Audits required standard clauses based on contract archetypes (Master Services Agreement, Vendor Agreement, NDA, Software License).
   - Flags missing critical clauses (e.g., missing Insurance or Data Breach Notification).

4. **Deterministic Contradiction Engine**
   - Finds semantically related clauses using vector similarity and pattern heuristics.
   - Detects concrete, high-stakes contractual collisions:
     - **Liability vs Indemnity**: Broad/unlimited indemnity vs aggregate liability dollar caps.
     - **Termination Notice**: 30-day convenience termination notice vs 60-day at-will notice.
     - **Jurisdiction & Venue**: Exclusive State/Federal court forum (e.g., New York) vs mandatory foreign arbitration (e.g., Singapore SIAC).
     - **IP Ownership**: Supplier background/foreground retention vs Customer work-for-hire assignment.
     - **Confidentiality Survival**: 1-year expiration vs 5-year survival obligations.

5. **Jurisdiction Detection**
   - Identifies mentions of legal systems (US, New York, California, Delaware, UK, EU GDPR, Singapore, India, Australia) and flags **"Cross-jurisdiction review required"**.

6. **Interactive Split-Screen UI**
   - **LEFT**: Full contract text with clickable clauses, search filter, and active contradiction alerts.
   - **RIGHT**: Ranked findings (Critical, High, Medium, Low) with confidence percentages, side-by-side evidence quotes, and counsel mitigation recommendations.
   - Bidirectional scrolling: clicking a finding scrolls directly to the affected clauses.

7. **Contract Risk Map**
   - Visual relationship network linking clauses: `Clause A ── [CONTRADICTS] ── Clause B`.

8. **Executive Audit Report**
   - Generate, preview, and download structured audit reports as `.txt` or print directly to PDF.

9. **Built-in Demo Contract**
   - Includes a full Master Services Agreement containing deliberate benchmark traps for instant 1-click evaluation without requiring external files or API keys.

---

## 🛠️ Tech Stack

- **Frontend**: React 19, TypeScript, Tailwind CSS, Lucide Icons, Motion
- **Document Extractors**: `mammoth` (DOCX), `pdfjs-dist` (PDF)
- **Engine**: Rule-based NLP, Token Cosine Similarity, and Safe Ruleset Heuristics
- **Build Tool**: Vite 8, Node.js / TSX

---

## 📦 Setup & Running the Project

### Prerequisites
- Node.js (v18 or higher)
- npm or bun

### 1. Install Dependencies
```bash
npm install
```

### 2. Configure Environment Variables
Copy `.env.example` to `.env`:
```bash
cp .env.example .env
```

Available variables:
- `GEMINI_API_KEY`: *(Optional)* Optional API key for auxiliary generative summaries. The core contradiction and risk engine operates 100% deterministically without an API key.
- `APP_URL`: Hosted application URL.

### 3. Start Development Server
```bash
npm run dev
```
Open your browser at `http://localhost:3000`.

### 4. Build for Production
```bash
npm run build
```

---

## ⚖️ Legal Disclaimer
ClauseGuard AI is an automated risk identification and contract review tool designed for hackathons and preliminary triage. It does not constitute binding legal advice and must be verified by licensed legal counsel.
