# 🏥 CPHQ Exam Prep — Study App

A self-hosted, offline-capable exam prep tool for the **Certified Professional in Healthcare Quality (CPHQ)** exam. Built as a single `index.html` file — no server, no login, no subscription.

**Live app:** `https://your-github-username.github.io/your-repo-name`

---

## 📦 What's Inside

| File | Purpose |
|------|---------|
| `index.html` | The entire app — question bank, UI, and logic in one file |
| `FINAL_GENERATOR.js` | Node.js script to auto-generate rationales via Claude API |

---

## ✨ Features

- **1,533 questions** across all CPHQ domains
- **Flashcard mode** — flip through questions with spaced repetition
- **Quiz mode** — timed 10-question sessions with instant feedback
- **Mock Exam** — full-length simulated exam
- **Analytics** — track your score trends and weak domains
- **Study Guide, Glossary, Pioneers, Organizations, QI Tools** — reference panels
- **Rationales** — 1,249 questions have built-in answer explanations
- **Dark/Light mode**, bookmarks, confidence ratings

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

1. Make your changes to `index.html`
2. Go to your repo on GitHub
3. Click `index.html` → click the **pencil (edit) icon** → paste new content → **Commit changes**

Or via command line:
```bash
git add index.html
git commit -m "Update question bank"
git push
```

---

## 🤖 Generating Rationales (One-Time Setup)

284 questions are currently missing rationales. Run this once to fill them all in automatically using the Claude API.

### Prerequisites

- [Node.js](https://nodejs.org) installed (LTS version)
- An Anthropic API key from [console.anthropic.com](https://console.anthropic.com) → API Keys → Create Key

### Steps

**1. Put both files in the same folder**
```
CPHQ Final/
  ├── index.html
  └── FINAL_GENERATOR.js
```

**2. Open `FINAL_GENERATOR.js` in Notepad (or any text editor)**

Find this line near the top:
```js
const API_KEY = 'sk-ant-api03-...';
```
Replace the value inside the quotes with your actual API key.

**3. Open Command Prompt in that folder**

- Hold `Shift` + right-click inside the folder
- Select **"Open PowerShell window here"** or **"Open Command Prompt here"**

**4. Run the generator**
```cmd
node FINAL_GENERATOR.js
```

You'll see live progress:
```
📖 Reading index.html...
✅ Found 1533 questions
📊 Missing rationales: 284

⚡ Generating 284 rationales...

[  1%]   1/284 Q12... ✓
[  2%]   2/284 Q47... ✓
...
✅ Complete: 284 OK, 0 failed

💾 Saved to: index_with_all_rationales.html
```

**5. Deploy the output**

Rename `index_with_all_rationales.html` → `index.html` and push it to GitHub.

### Cost estimate
~284 questions × ~250 tokens each = ~71,000 tokens ≈ **less than $0.10** using Claude Haiku.

---

## 🗂️ CPHQ Domain Coverage

| Domain | Coverage |
|--------|----------|
| Quality Management & Leadership | ✅ |
| Patient Safety | ✅ |
| Performance Improvement | ✅ |
| Accreditation & Regulatory | ✅ |
| Data Management & Analysis | ✅ |
| Health Information Management | ✅ |

---

## 🛠️ Troubleshooting

**`Cannot find module` error when running generator**
→ Make sure you're in the same folder as the `.js` file. Run `dir` to confirm both files are listed.

**App loads but shows 0 questions**
→ GitHub Pages might still be building. Wait 1–2 minutes and hard-refresh (`Ctrl+Shift+R`).

**Rationale shows "not yet available"**
→ That question hasn't been processed by the generator yet. Run `FINAL_GENERATOR.js` to fill them all in.

**Generator stops partway through**
→ Just run it again — it skips questions that already have rationales and picks up from where it left off... actually re-run is safe, it won't duplicate. But to be safe, run on the latest output file.

---

## 📝 Notes

- All data is stored locally in your browser (`localStorage`) — no account needed
- The app works fully offline once loaded
- API key is never stored in the HTML file — only used during generation
- Questions were sourced and rephrased from multiple CPHQ review publishers

---

*Built for personal CPHQ exam prep — May 2026 exam target 🎯*

