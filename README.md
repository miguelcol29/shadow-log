Hello
# Shadow Log — A Solo Leveling Workout Tracker

Shadow Log is a calisthenics/cardio tracker themed after *Solo Leveling*. Instead of a plain checklist, your workouts level you up, raise your Hunter Rank, grow three stats (STR / AGI / VIT), challenge you with scaling Daily Goals, pit you against a Weekly Boss, and let you save reusable Workout Templates — with a shareable "Guild Member Card" you can flex on Discord.

It's a single HTML file. How you open it determines where your progress is saved — see below.

---

## Getting Your Own Copy — and How Saving Works

There are two ways to run Shadow Log, and **each one saves your data differently.**

### Option 1: Inside Claude (account-synced)
1. Save the attached `shadow-log.html` file.
2. Open Claude (claude.ai or the app) and start a **new conversation**.
3. Upload/drag-and-drop `shadow-log.html` into the chat.
4. Ask Claude to open it as an artifact (e.g. *"open this as an artifact"*).
5. Your Level, XP, quest history, avatar, and everything else saves automatically to **your Claude account** — private to you, and it'll follow you if you open the same file again in a different conversation or on a different device, as long as you're signed in.

### Option 2: As a standalone file or GitHub Pages link (browser-saved)
If you open `shadow-log.html` directly — double-clicking it, dragging it into a browser tab, or visiting a GitHub Pages link — it works fully on its own, no Claude account needed. In this mode, progress saves to **that specific browser, on that specific device**, using its local storage.

What that means in practice:
- Come back in the same browser later → your progress is there.
- Switch browsers, switch devices, or use private/incognito mode → you'll see a fresh Level 1, since that's a different local storage.
- Clearing your browser's site data will erase your progress — unless you've exported a backup (see **Data Backup** below).

**The app tells you which mode you're in.** Look at the bottom of the page:
- ☁ **"Synced to your Claude account"** — you're in Claude, account-based saving.
- 💾 **"Standalone mode — progress saves to this browser only"** — you're running it directly, browser-based saving.

Neither mode is "better" — just pick based on what you want: Claude sync if you want your progress to follow your account anywhere, or standalone if you just want to click a link and go without needing Claude at all.

---

## How It Works

### Level, XP & Rank
- Every set you log earns XP: **1 XP per rep**, **0.4 XP per second held** (planks, holds), **3 XP per minute** of cardio.
- XP needed for your next level increases each time (roughly `55 × level^1.55`), so leveling slows down as you go.
- **Rank** is just a badge tied to your level — not a separate grind:

| Rank | Level Range |
|---|---|
| E | 1–9 |
| D | 10–19 |
| C | 20–29 |
| B | 30–39 |
| A | 40–49 |
| S | 50+ |

### STR / AGI / VIT
- These count **distinct exercises logged per day**, not XP — logging Push-Ups and Pull-Ups in the same day is +2 STR.
- Each stat has two tiers: **Tier I** runs 0–100, **Tier II** runs 100–1000 (progress carries over, doesn't reset), and it caps at **Tier MAX** once you pass 1000.

### Hunt Streak
- Counts consecutive days you've logged a quest.
- You get **1 Rest Day of grace per rolling 7-day period** — miss a single day and your streak survives. Miss two days in a row, or use your Rest Day again before it recharges, and it resets to 1.
- Every streak day adds **+1% bonus XP**, capped at **+25%**, applied automatically to whatever you log that day.
- Break a streak of **3 or more days** and the System may throw you a lifeline — see **Penalty Quest** below.

### Daily Goals & Gate Rank
- Every exercise has a **Daily Goal** — a real target to push toward (e.g. 50 push-ups), not just "log something." Set your own baseline per exercise via the **⚙ icon on the Freelance Quest panel**; leave it blank to use the sensible default.
- Goals are **cumulative for the day** — every set across every quest you log counts toward them. Hit your goal and it's cleared for the day.
- **Gate Rank** (E through S, selectable on the Job Board) scales your goals up, the same way gates have difficulty ranks in the show — D-Gate is 1.25× your baseline, C is 1.5×, climbing to **2.5× at S-Gate**. It defaults to your Hunter Rank but you can raise or lower it any time to push yourself harder (or ease off).
- **Tip:** when adding a set, leave the number field blank and hit Add Set — it automatically fills in your Daily Goal for that exercise, so you don't have to type it out if that's exactly what you're aiming for.

### Guild Job Board
- Each day posts a set of suggested "contracts" (exercises) based on a weekly roster you can customize: Strength day, Agility day, Vitality day, Full Hunt (mix of all three), or Guild Holiday (rest day). Edit the roster from "⚙ Edit guild roster" on the board.
- Contracts prioritize exercises you haven't done in a while, and show flavor text like *"Not hunted in 6 days."*
- Each contract card shows your gate-scaled **Daily Goal** with a live progress bar. Hit **Accept Contract** to select that exercise and start logging real sets toward it — accepting no longer auto-fills a single giant set, since the goal is meant to take multiple sets across the day.

### Weekly Boss
- Every **Monday**, a named boss spawns with an HP bar (deterministic per week — reloading the app won't reroll it, but next week gets a fresh one from a pool of 12, each with its own portrait art).
- **Every XP you earn Monday–Sunday deals that much damage** to the boss — streak bonuses included. No new logging required; it's computed live from your quests.
- Boss HP is **adaptive**: roughly 15% above your average weekly XP over the last 3 weeks (averaged only across weeks that actually have data, so your early weeks aren't deflated), with a rank-based minimum floor so it's never trivial:

| Gate Rank | Minimum HP Floor |
|---|---|
| E | 400 |
| D | 500 |
| C | 650 |
| B | 850 |
| A | 1,100 |
| S | 1,500 |

- HP **locks the moment the boss spawns** — it won't change mid-week even if your Gate Rank changes.
- **Slay it** (deplete its HP before Sunday ends) to claim a bounty worth 20% of its HP, awarded straight to your XP. **Fail to**, and it escapes — no penalty, just a record.
- A collapsible **Boss Log** ("📜 View boss log") keeps your last 12 weeks of results — slain or escaped.

### Penalty Quest
- If a streak of **3+ days** actually breaks (your Rest Day grace couldn't save it), the System offers a one-time trial that same day: clear three exercises — one each from STR/AGI/VIT — at **1.5× their gate-scaled Daily Goals** before midnight.
- Clear all three and your **full streak is restored** (plus credit for today), bonus XP included immediately.
- Miss the deadline and it simply expires — your streak stays broken, but nothing extra is lost.
- This offer appears **at most once every 14 days**, so it's a genuine second chance, not a safety net you can lean on weekly.

### Freelance Quest
Your main logging area, and the most feature-dense panel in the app — tap the **(i)** next to its title any time for a full in-app refresher. Here's what lives there:

- **Log anything:** pick an exercise from the dropdown, enter reps/seconds/minutes (or leave it blank to auto-fill your Daily Goal), hit **Add Set**, repeat for each set, then **Complete Quest**.
- **⚙ Manage Exercises** (gear icon, top-right of the panel): a full toolkit per exercise —
  - **Add** a custom exercise (soccer, disc golf, anything not in the default list)
  - **✎ Edit** — fix a typo or move an exercise to a different category (STR/AGI/VIT). Past logs keep their original name/category for historical accuracy; only future logging changes.
  - **Daily Goal** input — set your own baseline per exercise.
  - **⚖ Weight toggle** — enable to track load (lbs) per set for that exercise. Once on, a weight field appears next to the reps input everywhere you log that exercise (Freelance Quest, templates, backdated entries), and sets display as `12@25` notation.
  - **Remove/Restore** — hide an exercise from the dropdown and Job Board without deleting its history; fully reversible.
- **Workout Templates:** save a full workout (exercises + set/rep/weight numbers) once, then reuse it instead of rebuilding it from scratch every time. See the dedicated section below.
- **📅 Log a Past Day:** backdate a workout for any day in the last 14 days. No streak bonus applies (base XP only), but the entry fills in your streak history properly (it can bridge gaps and extend a streak backward) and still counts toward the active Weekly Boss if that date falls in the current week.

### Workout Templates
For workouts you repeat — Push Day, a park circuit, whatever your schedule looks like — save it once and stop rebuilding it every session.

- **Two ways to create one:**
  - **💾 Save as Template** (appears after completing any quest) — captures exactly what you just logged, sets and weights included, as a new named template.
  - **📋 Manage Templates → + Create New Template** — build one from scratch ahead of time using the same exercise-and-set picker, without needing to log a real workout first.
- **Using a saved template:** pick it from the dropdown above the exercise selector, then choose:
  - **⚡ Log** — Quick Log. Instantly logs every exercise and set exactly as saved, after a confirmation screen listing everything about to be logged (so nothing goes in blind). Fastest path — one tap plus a confirm.
  - **↗ Load** — drops the template into the builder as normal, editable pills so you can tweak a number, add an extra set, or drop an exercise before hitting Complete Quest. Best for days that don't go exactly to plan.
- **Editing a template:** 📋 Manage Templates → **Edit** on any template — rename it, add exercises, remove exercises, or adjust saved set/weight values. Changes only apply going forward.
- **Deleting a template:** same menu, **Delete** (asks for confirmation first).
- Templates have no limit — create as many as you want.

### Achievements & Titles
- The **ACHIEVEMENTS** panel tracks 19 unlockable milestones — streak length, level, days hunted, goal clears, S-Gate clears, boss kills, penalty-quest redemption, stat tiers, variety, and template usage (saving your first template, Quick Logging 10 times). Locked ones show dimmed with a 🔒; unlocked ones glow gold.
- Each achievement grants a **title** you can equip (one at a time) — it displays under your name at the top of the app and gets drawn directly onto your **Guild Member Card**.
- Progress you already had before a given achievement existed unlocks retroactively and silently the next time you open the app.

### Dashboard
- **Consistency (heatmap):** shows the last 12 weeks of activity, darker = more XP that day.
- **Progress (chart):** pick any exercise you've logged to see your daily totals (reps/seconds/minutes) over your last 14 sessions.
- **Quest History:** your last 15 logged days, most recent first, including weight notation where applicable — each one has a ✕ to remove it if you logged something by mistake. Removing a day automatically recalculates your Level, XP, and streak so nothing stays inflated. (Achievement and boss-kill honors are never revoked by this, even retroactively.)

### Hunter Profile & Guild Member Card
- Tap the **⚙ gear icon** (top-right corner of the app) to set your Hunter Name, upload an avatar photo, and manage your data backup.
- Your name, equipped title, and avatar show at the top of the app and get baked directly into your **Guild Member Card** — a shareable snapshot (Level, Rank, stats, streak, title) styled like a license card. Generate one from the "GUILD MEMBER CARD" panel and download it as an image to post in Discord.

### Data Backup
- In **⚙ Settings**, under "DATA BACKUP": **Export Backup** downloads your entire save (level, XP, logs, achievements, boss history, templates, everything) as a JSON file. **Import Backup** restores from one, after showing you what's inside and confirming — since it replaces whatever is currently saved.
- This is the safety net for standalone/browser-saved mode (export before clearing browser data, or to move progress to another device), and it also works as a manual sync between a Claude-hosted copy and a standalone one, since both use the same data format.

### Resetting
- "Reset all data" at the bottom wipes everything for a fresh start — it asks for confirmation first, and can't be undone. Consider exporting a backup first if there's any chance you'll want the old data back.

---

## A Few Tips
- Info bubbles (small "i" icons) sit next to Level, Rank, XP, STR/AGI/VIT, Hunt Streak, Gate Rank, Weekly Boss, Penalty Quest, and Freelance Quest — tap any of them for a quick explanation of exactly how that number or mechanic works.
- Leave the reps/seconds/minutes field blank when adding a set to auto-fill your Daily Goal for that exercise — handy when you're hitting your target exactly.
- Your streak, XP, stats, achievements, templates, and boss records are permanent and never wiped unless you use Reset.
- If you get an updated version of this file later, opening it again won't erase your existing progress — your data lives in storage separate from the file itself (tied to your account in Claude, or to your browser in standalone mode). Exporting a backup beforehand is always a safe habit when updating.

Good luck, Hunter.
