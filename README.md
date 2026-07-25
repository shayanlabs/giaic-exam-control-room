# 🎯 GIAIC Final Exam — Control Room

> **P3-FDEAGA** · FDE–Agent Factory Model & Advanced General Agents
>
> A single-page, self-contained exam prep dashboard: a Kanban board, MoSCoW priority key, and an Eisenhower matrix — all in one HTML file, with progress saved automatically in the browser.

---

## ✨ What This Is

Preparing for the GIAIC Final Exam means juggling **8 official course modules**, dozens of sub-topics, flashcards, quizzes, and a marathon revision schedule. This board turns all of that into one visual command center so nothing falls through the cracks.

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
| 🗂️ **Kanban Board** | Move each topic through `Backlog → This Week → In Progress → Self-Test → Mastered` using `‹ ›` controls. |
| 🎯 **MoSCoW Priorities** | Every task is tagged **Must / Should / Could** so you know exactly what to study first. |
| ⏱️ **Eisenhower Matrix** | A quadrant guide for how to split daily study time between urgent and important work. |
| 🛰️ **Station Timeline** | A live-updating strip showing which prep phase you're currently in, based on today's date. |
| 📊 **Progress Bar** | Tracks how many of the 17 tasks are marked *Mastered*, updated in real time. |
| 🔍 **Filters** | Instantly filter the board by priority chip: All / Must / Should / Could. |
| 🔗 **Direct Links** | Each card links straight to the relevant page/section of the official course material. |
| 💾 **Persistent State** | Your board state is saved automatically — refresh the page and your progress stays intact. |
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
| 🟡 **Must** | Gold | Loop Engineering, Harness Engineering, Evals, Runtime (*Leaving the Laptop*), Roles — the 5 densest sub-topics; the bulk of the exam. |
| 🟢 **Should** | Teal | Ecosystem, General Agents on the Web — vocabulary-heavy, high-value once Must topics are solid. |
| ⚪ **Could** | Slate | Local AI: Agentic Coding — a small, hands-on module for spare time. |
| 🔴 **Won't (for now)** | Brick | Anything outside the 8 official syllabus links (extra book chapters, Python, etc). |

---

## ⏳ Eisenhower Matrix — Daily Time Allocation

| Quadrant | Focus | Guidance |
|---|---|---|
| 🔴 **Urgent + Important** | Fresh reading of Must topics: Loop, Harness, Evals, Runtime | Deep-focus hours go here |
| 🟢 **Important, not Urgent** | Flashcards, "Check Yourself" boxes, spaced revision, mock quizzes | Schedule it — don't skip it |
| 🟡 **Urgent, not Important** | Zia Tutor AI access, marathon section confirmation, exam date checks | Handle in under 2 minutes |
| ⚪ **Neither** | Bonus chapters, extra deep-dive videos | Only once everything else is green |

---

## 📚 How to Use

1. Open `index.html` in any browser (or visit the [live GitHub Pages link](#-live-preview)).
2. Move each topic card across the Kanban stages as you study it.
3. Use the priority filters to focus on **Must**-have topics first.
4. Every module's official page has an **"↗ open"** link — click it to jump straight to that section.
5. Each source chapter ends with **"Check Yourself"** and **"Test Your Understanding"** boxes + flashcards — treat these as your informal MCQ practice, since the format mirrors the real exam.
6. Hit **Reset progress** at the bottom if you want to start the board over.

---

## 🛠️ Tech Stack

- **Pure HTML/CSS/JS** — zero dependencies, zero build tools
- `IBM Plex Mono` + `Inter` via Google Fonts
- Browser-based key/value storage for persistent state

---

## 📁 Repository Structure

```
giaic-exam-control-room/
├── index.html   # The entire app — board, styles, and logic
└── README.md    # You are here
```

---

<p align="center">Built to make one exam feel like one board. 🚀</p>
