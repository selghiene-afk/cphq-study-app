# 🏥 CPHQ Exam Prep — Study App

A self-hosted, offline-capable exam prep tool for the **Certified Professional in Healthcare Quality (CPHQ)** exam. Built as a single `index.html` file — no server, no login, no subscription.

**Live app:** `https://selghiene-afk.github.io/cphq-study-app/`

---

## 📦 What's Inside

| File | Purpose |
|------|---------|
| `index.html` | The entire app — question bank, UI, and logic in one file |
| `README.md` | This file |

---

## ✨ Features

- **2,211 questions** across all 7 CPHQ domains, blueprint-aligned, deduplicated and answer-verified
- **Per-option "why others are wrong"** — every distractor has its own explanation, shown inline after answering
- **Flashcard mode** — MCQ choices (A–D) shown on the card front, flip to reveal the correct answer, with spaced repetition (SR) scheduling
- **Quiz mode** — timed or untimed sessions with instant feedback and rationales
- **Mock Exam** — full-length simulated exam (125 questions, 3-hour timer)
- **Analytics** — track score trends, domain performance, and weak areas
- **Study Guide, Glossary, Pioneers, Organizations, QI Tools** — built-in reference panels
- **Rationales** — every question has a one-to-two sentence explanation of the correct answer
- **Dark/Light mode**, bookmarks, confidence ratings
- **Domain tagging** — every question tagged to its CPHQ blueprint domain

---

## 🗂️ CPHQ Domain Coverage (Blueprint-Aligned)

Based on the official NAHQ CPHQ Content Outline:

| Domain | Questions | App % | Blueprint % |
|--------|-----------|-------|-------------|
| Performance and Process Improvement | 497 | 22.5% | 21.6% |
| Health Data Analytics | 492 | 22.3% | 20.8% |
| Quality Leadership | 328 | 14.8% | 15.2% |
| Patient Safety | 310 | 14.0% | 14.4% |
| Quality Review and Accountability | 279 | 12.6% | 12.8% |
| Population Health and Care Transitions | 154 | 7.0% | 8.8% |
| Regulatory and Accreditation | 151 | 6.8% | 6.4% |
| **Total** | **2,211** | **100%** | **100%** |

> Note: The app domain **Quality Leadership** maps to the official NAHQ domain **Quality Leadership and Integration**.

---

## 🚀 Deploying to GitHub Pages

### First time setup

1. Create a new GitHub repository (public)
2. Upload `index.html` to the repo root
3. Go to **Settings → Pages**
4. Under *Source*, select **Deploy from a branch**
5. Choose `main` branch → `/ (root)` → click **Save**
6. Wait ~60 seconds, then visit:
   ```
   https://your-username.github.io/your-repo-name
   ```

### Updating the app

**Via GitHub web (easiest):**
1. Go to your repo on GitHub
2. Click `index.html` → click the **pencil (edit) icon**
3. Select all content (`Ctrl+A`) → paste the new `index.html` content
4. Click **Commit changes**

**Via command line:**
```bash
git add index.html
git commit -m "Update question bank"
git push
```

---

## 🐛 Bug Fixes & Changelog

### v5.0 — Current (July 2026)
**Question bank cleanup, answer verification, and per-option rationales**

**Data changes:**
| Change | Count |
|--------|-------|
| Bank reduced from 2,500 to 2,211 after full deduplication | −289 questions |
| Duplicate questions removed (shingle + sequence similarity) | 12 pairs |
| Answer-key errors corrected against HQ Solutions 5th Ed. | 3 questions |
| Per-option "why others are wrong" explanations added | 2,211 questions |
| Missing correct-answer rationales authored (one sentence each) | 226 questions |
| Option-echo prefixes stripped from distractor explanations | 881 reasons |
| Broken/fragment option reconstructed | 1 question |
| Domain renamed "Leadership and Organization" → "Quality Leadership" | 328 questions |
| Clear-cut domain reassignments | 10 questions |

**Answer verification:**
- All 464 pages of HQ Solutions 5th Edition OCR-extracted and indexed as the source of truth
- 30 calculation questions fully verified; 3 hard errors fixed (complication rate, correlation sign, FMEA RPN formula)
- 68 heuristic-flagged questions manually reviewed against source — all cleared, zero content errors

**App logic:**
- **Per-option rationale display** — "why others are wrong" reasons are keyed by option **text**, not letter, so they follow the shuffled display order and never mis-attach. Verified across 1,000 shuffle simulations with zero mismatches.
- **Rationale gate fix** — questions with per-option reasons but an empty summary rationale now render their full breakdown instead of falling back to "Rationale not yet available."
- **Flashcard MCQ mode** — the card front now shows all four answer choices (A–D, reshuffled per view); the back reveals the correct answer with its letter. Answer is matched by text, so front and back always agree.

---

### v4.0 — March 2026
**Question bank overhaul — 2,500 questions, fully audited**

**Data fixes applied:**
| Fix | Count |
|-----|-------|
| Backslash artifacts removed (`\'`, `\"` rendering visibly) | 226 questions |
| Answer embedded in stem (`**bold**`) converted to `______` | 7 questions |
| Split/broken options merged (option cut mid-sentence across 2 entries) | 29 questions |
| Answer text not matching any option (truncated answer field) | 195 questions |
| Duplicate options within same question | 6 questions |
| Generic placeholder distractors replaced with domain-appropriate ones | 32 options |
| Rationale letter references removed (e.g. "Option B is correct" in rationale) | 32 rationales |
| Answer text revealed in question stem | 1 question |
| Duplicate questions removed | 5 questions |
| Spelling errors fixed (distinct, ensure, behavior, organization, analyzing, etc.) | 13 fields |

**App logic fix:**
- **Rationale letter mismatch** — The app shuffles option order on display, but the rationale panel was re-labeling options A/B/C/D based on the original stored order instead of the displayed order. This caused "A ← correct" to point to the wrong option. Fixed by passing the displayed (shuffled) option order to the rationale renderer.

---

### v3.0 — February 2026
- Expanded question bank from 1,533 to 2,500 questions
- Added domain tagging to all questions
- Rebalanced domains to match CPHQ blueprint percentages
- All rationales condensed to maximum 2 sentences
- Removed 7 questions requiring embedded tables that couldn't render in plain text
- Fixed `classList` initialization error on app load (`showPanel('flashcards')` → `showPanel('flashcard')`)

---

### v2.0 — January 2026
- Generated rationales for all 934 previously missing questions via Claude API
- Fixed JS string escaping corruption (`SyntaxError` from unescaped newlines in RAW array)
- Fixed document body initialization — questions not displaying on page load
- Rationale artifacts cleaned (`"},"},` patterns removed from rationale text)
- Truncated rationales repaired (hard-cut at ~400 characters)

---

### v1.0 — December 2025
- Initial release with 1,533 questions
- Flashcard, Quiz, Mock Exam, Analytics modes
- Spaced repetition system

---

## 🛠️ Troubleshooting

**App loads but shows 0 questions**
→ GitHub Pages might still be building. Wait 1–2 minutes and hard-refresh (`Ctrl+Shift+R`).

**Options look shuffled differently each time**
→ This is intentional — options are randomized on every question to prevent pattern memorization. Per-option explanations follow the shuffle automatically.

**Rationale shows wrong letter (e.g. "A ← correct" but correct answer is C)**
→ This was a known bug fixed in v4.0 and reinforced in v5.0 (reasons are now keyed by option text, not letter). Make sure you are running the latest `index.html`.

**A question shows "why others are wrong" but no correct-answer rationale**
→ Fixed in v5.0. All 226 affected questions now have a one-sentence rationale. Download the latest `index.html`.

**Analytics shows incorrect domain breakdown**
→ Domain data is embedded in the question bank. Ensure you are using the latest `index.html`, which includes the renamed "Quality Leadership" domain and updated counts.

---

## 📝 Notes

- All data is stored locally in your browser (`localStorage`) — no account needed
- The app works fully offline once loaded
- No API key required — all rationales and per-option explanations are pre-embedded
- Questions sourced from multiple CPHQ review materials and original content, rephrased throughout; answers verified against HQ Solutions 5th Edition

---

*Built for personal CPHQ exam prep — 2026 exam target 🎯*
