# 🎯 GIAIC Final Exam — Control Room

> **P3-FDEAGA** · 100 MCQs · 140 min · 70% to pass
>
> A single-page, self-contained exam prep dashboard covering the full syllabus in 46 cards: a Kanban board, MoSCoW priority key, and an Eisenhower matrix — all in one HTML file, with progress saved automatically in your browser.

---

## ✨ What This Is

Preparing for the GIAIC Final Exam means juggling every official course module, its sub-pages and appendices, flashcards, quizzes, and a marathon revision schedule. This board breaks all of that down into 46 tracked cards — one visual command center so nothing falls through the cracks.

No build step, no dependencies to install, no backend — just open the page and start tracking.

---

## 🖥️ Live Preview

Enable **GitHub Pages** on this repo (`Settings → Pages → Deploy from branch: main / root`) and the board goes live at:

```
https://shayanlabs.github.io/giaic-exam-control-room/
```

---

## 🧩 Features

| Feature | Description |
|---|---|
| 🗂️ **Kanban Board** | Move each topic through `Backlog → Reading → This Week → Self-Test → Mastered`. |
| 🖐️ **Drag & Drop** | Grab any card and drop it into another column — works with mouse, touch, and pen. `‹ ›` buttons still work too. |
| 🎯 **MoSCoW Priorities** | Every task is tagged **Must / Should / Could** so you know exactly what to study first. |
| 🧩 **Module Filter** | Narrow the board down to one module at a time (Roles, Loop Eng, Harness, Evals, Runtime, etc.). |
| ⏱️ **Eisenhower Matrix** | A quadrant guide for how to split daily study time between urgent and important work. |
| 🛰️ **Station Timeline** | A live-updating strip showing which prep phase you're currently in, based on today's date. |
| 📊 **Progress Bar** | Tracks how many of the 46 cards are marked *Mastered*, updated in real time. |
| 🔍 **Priority Filters** | Instantly filter the board by priority chip: All / Must / Should / Could. |
| 🆕 **New-Card Badges** | Cards added in the full-coverage pass are flagged `NEW` so you know what's changed. |
| 🔗 **Direct Links** | Each card links straight to the relevant page/section of the official course material. |
| 💾 **Persistent State** | Saved to your browser's `localStorage` automatically — refresh or restart your browser and your progress stays intact. |
| 🔄 **Reset Option** | One click resets the entire board back to Backlog. |

---

## 🗓️ Prep Timeline

| Station | Phase | Dates |
|---|---|---|
| **1** | Foundation Build | Jul 25 – Aug 14 |
| **2** | Marathon Assembly | Aug 15 – Aug 30 |
| **3** | Final Calibration | Aug 31 – Exam week (~Sep 1–7) |

---

## 🚦 MoSCoW Priority Key

| Priority | Color | Covers |
|---|---|---|
| 🟡 **Must** | Gold | Loop Eng (15 concepts), Harness (12), Evals (12), Runtime (12), Roles, and FDE AF Model — about 65 concepts, the bulk of the exam. |
| 🟢 **Should** | Teal | Web Agents (12 + appendices), Ecosystem overview, System of Record, Choosing Your Vertical — full of key terms, easy marks once Must topics are solid. |
| ⚪ **Could** | Slate | Local AI (7 concepts), Zia Tutor / Zia Developer AI pages — small modules, save for last. |
| 🔴 **Won't (for now)** | Brick | Mode 2 chapters (Python, MCP, Digital FTE, deployment) — outside exam scope. |

---

## ⏳ Eisenhower Matrix — Daily Time Allocation

| Quadrant | Focus | Guidance |
|---|---|---|
| 🔴 **Urgent + Important** | Fresh reading of Must topics: Loop, Harness, Evals, Runtime, FDE AF Model | Two deep-focus blocks every day |
| 🟢 **Important, not Urgent** | Flashcards, "Check Yourself" boxes, "Test Your Understanding" quizzes, spaced repeats of weak topics | Put it on the calendar |
| 🟡 **Urgent, not Important** | Marathon section confirmation, Zia Tutor access, exam date checks | 5 minutes |
| ⚪ **Neither** | Mode 2 chapters, extra YouTube videos | Only once everything else is green |

---

## 📚 How to Use

1. Open `index.html` in any browser (or visit the [live GitHub Pages link](#-live-preview)).
2. Drag and drop a card into another column, or use the `‹ ›` buttons, as you move through each topic.
3. Use the priority filters and module filter to focus on **Must**-have topics, or one module at a time.
4. Every module's official page has an **"↗ open"** link — click it to jump straight to that section.
5. Each source chapter ends with **"Check Yourself"** and **"Test Your Understanding"** boxes + flashcards — treat these as your informal MCQ practice, since the format mirrors the real exam.
6. Hit **Reset progress** at the bottom if you want to start the board over.

---

## 🛠️ Tech Stack

- **Pure HTML/CSS/JS** — zero dependencies, zero build tools
- `IBM Plex Mono` + `Inter` via Google Fonts
- Pointer Events for drag-and-drop (mouse, touch, and pen from one code path)
- Browser `localStorage` for persistent state

---

## 📁 Repository Structure

```
giaic-exam-control-room/
├── index.html   # The entire app — board, styles, and logic
└── README.md    # You are here
```

---

<p align="center">Built to make one exam feel like one board. 🚀</p>
