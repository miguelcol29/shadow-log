# Shadow Log — A Solo Leveling Workout Tracker

Shadow Log is a calisthenics/cardio tracker themed after *Solo Leveling*. Instead of a plain checklist, your workouts level you up, raise your Hunter Rank, grow three stats (STR / AGI / VIT), challenge you with scaling Daily Goals, and pit you against a Weekly Boss — with a shareable "Guild Member Card" you can flex on Discord.

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
- **Gate Rank** (E through S, selectable on the Job Board) scales your goals up, the same way gates have difficulty ranks in the show — an S-Gate goal is roughly **9× harder** than an E-Gate one. It defaults to your Hunter Rank but you can raise or lower it any time to push yourself harder (or ease off).

### Guild Job Board
- Each day posts a set of suggested "contracts" (exercises) based on a weekly roster you can customize: Strength day, Agility day, Vitality day, Full Hunt (mix of all three), or Guild Holiday (rest day). Edit the roster from "⚙ Edit guild roster" on the board.
- Contracts prioritize exercises you haven't done in a while, and show flavor text like *"Not hunted in 6 days."*
- Each contract card shows your gate-scaled **Daily Goal** with a live progress bar. Hit **Accept Contract** to select that exercise and start logging real sets toward it — accepting no longer auto-fills a single giant set, since the goal is meant to take multiple sets across the day.

### Weekly Boss
- Every **Monday**, a named boss spawns with an HP bar (deterministic per week — reloading the app won't reroll it, but next week gets a fresh one from a pool of 12).
- **Every XP you earn Monday–Sunday deals that much damage** to the boss — streak bonuses included. No new logging required; it's computed live from your quests.
- Boss HP is **adaptive**: roughly 15% above your average weekly XP over the last 3 weeks, with a rank-based minimum floor so it's never trivial. HP locks the moment the boss spawns.
- **Slay it** (deplete its HP before Sunday ends) to claim a bounty worth 20% of its HP, awarded straight to your XP. **Fail to**, and it escapes — no penalty, just a record.
- A collapsible **Boss Log** ("📜 View boss log") keeps your last 12 weeks of results — slain or escaped.

### Penalty Quest
- If a streak of **3+ days** actually breaks (your Rest Day grace couldn't save it), the System offers a one-time trial that same day: clear three exercises — one each from STR/AGI/VIT — at **1.5× their gate-scaled Daily Goals** before midnight.
- Clear all three and your **full streak is restored** (plus credit for today), bonus XP included immediately.
- Miss the deadline and it simply expires — your streak stays broken, but nothing extra is lost.
- This offer appears **at most once every 14 days**, so it's a genuine second chance, not a safety net you can lean on weekly.

### Freelance Quest
- This is your manual override — log any exercise directly from the dropdown, or add a one-off custom exercise (soccer, disc golf, whatever) via the **⚙ gear icon** in the panel's corner. The same panel lets you set custom Daily Goals per exercise and remove exercises you don't want cluttering the dropdown (fully reversible any time).
- You're never required to follow the board — freelance logging is always available.

### Achievements & Titles
- The **ACHIEVEMENTS** panel tracks 17 unlockable milestones — streak length, level, days hunted, goal clears, boss kills, penalty-quest redemption, stat tiers, and more. Locked ones show dimmed with a 🔒; unlocked ones glow gold.
- Each achievement grants a **title** you can equip (one at a time) — it displays under your name at the top of the app and gets drawn directly onto your **Guild Member Card**.
- Progress you already had before this feature existed unlocks retroactively and silently the first time you open the updated app.

### Dashboard
- **Consistency (heatmap):** shows the last 12 weeks of activity, darker = more XP that day.
- **Progress (chart):** pick any exercise you've logged to see your daily totals (reps/seconds/minutes) over your last 14 sessions.
- **Quest History:** your last 15 logged days, most recent first — each one has a ✕ to remove it if you logged something by mistake. Removing a day automatically recalculates your Level, XP, and streak so nothing stays inflated. (Achievement and boss-kill honors are never revoked by this, even retroactively.)

### Hunter Profile & Guild Member Card
- Tap the **⚙ gear icon** (top-right corner of the app) to set your Hunter Name, upload an avatar photo, and manage your data backup.
- Your name, equipped title, and avatar show at the top of the app and get baked directly into your **Guild Member Card** — a shareable snapshot (Level, Rank, stats, streak, title) styled like a license card. Generate one from the "GUILD MEMBER CARD" panel and download it as an image to post in Discord.

### Data Backup
- In **⚙ Settings**, under "DATA BACKUP": **Export Backup** downloads your entire save (level, XP, logs, achievements, boss history, everything) as a JSON file. **Import Backup** restores from one, after showing you what's inside and confirming — since it replaces whatever is currently saved.
- This is the safety net for standalone/browser-saved mode (export before clearing browser data, or to move progress to another device), and it also works as a manual sync between a Claude-hosted copy and a standalone one, since both use the same data format.

### Resetting
- "Reset all data" at the bottom wipes everything for a fresh start — it asks for confirmation first, and can't be undone. Consider exporting a backup first if there's any chance you'll want the old data back.

---

## A Few Tips
- Info bubbles (small "i" icons) sit next to Level, Rank, XP, STR/AGI/VIT, Hunt Streak, Gate Rank, Weekly Boss, and Penalty Quest — tap any of them for a quick explanation of exactly how that number or mechanic works.
- Your streak, XP, stats, achievements, and boss records are permanent and never wiped unless you use Reset.
- If you get an updated version of this file later, opening it again won't erase your existing progress — your data lives in storage separate from the file itself (tied to your account in Claude, or to your browser in standalone mode). Exporting a backup beforehand is always a safe habit when updating.

Good luck, Hunter.
