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

- **2,500 questions** across all 7 CPHQ domains, blueprint-aligned
- **Flashcard mode** — flip through questions with spaced repetition (SR scheduling)
- **Quiz mode** — timed or untimed sessions with instant feedback and rationales
- **Mock Exam** — full-length simulated exam (125 questions, 3-hour timer)
- **Analytics** — track score trends, domain performance, and weak areas
- **Study Guide, Glossary, Pioneers, Organizations, QI Tools** — built-in reference panels
- **Rationales** — all 2,500 questions have built-in answer explanations (max 2 sentences)
- **Dark/Light mode**, bookmarks, confidence ratings
- **Domain tagging** — every question tagged to its CPHQ blueprint domain

---

## 🗂️ CPHQ Domain Coverage (Blueprint-Aligned)

Based on the official NAHQ CPHQ Content Outline (2024):

| Domain | Questions | Blueprint % |
|--------|-----------|-------------|
| Performance and Process Improvement | 540 | 21.6% |
| Health Data Analytics | 520 | 20.8% |
| Leadership and Organization | 380 | 15.2% |
| Patient Safety | 360 | 14.4% |
| Quality Review and Accountability | 320 | 12.8% |
| Regulatory and Accreditation | 160 | 6.4% |
| Population Health and Care Transitions | 220 | 8.8% |
| **Total** | **2,500** | **100%** |

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

### v4.0 — Current (March 2026)
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
→ This is intentional — options are randomized on every question to prevent pattern memorization.

**Rationale shows wrong letter (e.g. "A ← correct" but correct answer is C)**
→ This was a known bug fixed in v4.0. Make sure you are running the latest `index.html`.

**App shows "Page loaded, initializing... RAW questions: 2500" but crashes**
→ A `classList` error on a missing panel ID. Fixed in v3.0. Download the latest `index.html`.

**Analytics shows incorrect domain breakdown**
→ Domain data is embedded in the question bank. Ensure you are using the latest `index.html` which includes domain tags on all questions.

---

## 📝 Notes

- All data is stored locally in your browser (`localStorage`) — no account needed
- The app works fully offline once loaded
- No API key required — all 2,500 rationales are pre-embedded
- Questions sourced from multiple CPHQ review materials and original content, rephrased throughout

---

*Built for personal CPHQ exam prep — 2026 exam target 🎯*
