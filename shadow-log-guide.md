# Shadow Log — A Solo Leveling Workout Tracker

Shadow Log is a calisthenics/cardio tracker themed after *Solo Leveling*. Instead of a plain checklist, your workouts level you up, raise your Hunter Rank, and grow three stats (STR / AGI / VIT) — with a "Guild Job Board" that posts suggested daily workouts like bounty contracts, and a shareable "Guild Member Card" you can flex on Discord.

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
- Clearing your browser's site data will erase your progress, with no backup.

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

### Guild Job Board
- Each day posts a set of suggested "contracts" (exercises) based on a weekly roster you can customize: Strength day, Agility day, Vitality day, Full Hunt (mix of all three), or Guild Holiday (rest day). Edit the roster from "⚙ Edit guild roster" on the board.
- Contracts prioritize exercises you haven't done in a while, and show flavor text like *"Not hunted in 6 days."*
- **Gate Rank** (E through S, selectable on the board) scales how tough the suggested targets are — an E-Gate suggests 12 reps, an S-Gate suggests 110. It defaults to match your current Hunter Rank but you can raise or lower it any time.
- Hit **Accept Contract** to pre-fill that exercise into today's quest.

### Freelance Quest
- This is your manual override — log any exercise directly from the dropdown, or add a one-off custom exercise (soccer, disc golf, whatever) via the **⚙ gear icon** in the panel's corner, which also lets you remove exercises you don't want cluttering the dropdown (reversible any time).
- You're never required to follow the board — freelance logging is always available.

### Dashboard
- **Consistency (heatmap):** shows the last 12 weeks of activity, darker = more XP that day.
- **Progress (chart):** pick any exercise you've logged to see your daily totals (reps/seconds/minutes) over your last 14 sessions.
- **Quest History:** your last 15 logged days, most recent first — each one has a ✕ to remove it if you logged something by mistake. Removing a day automatically recalculates your Level, XP, and streak so nothing stays inflated.

### Hunter Profile & Guild Member Card
- Tap the **⚙ gear icon** (top-right corner of the app) to set your Hunter Name and upload an avatar photo.
- Your name and avatar show at the top of the app and get baked directly into your **Guild Member Card** — a shareable snapshot (Level, Rank, stats, streak) styled like a license card. Generate one from the "GUILD MEMBER CARD" panel and download it as an image to post in Discord.

### Resetting
- "Reset all data" at the bottom wipes everything for a fresh start — it asks for confirmation first, and can't be undone.

---

## A Few Tips
- Info bubbles (small "i" icons) sit next to Level, Rank, XP, STR/AGI/VIT, and Hunt Streak — tap any of them for a quick explanation of exactly how that number is calculated.
- Your streak, XP, and stats are permanent and never wiped unless you use Reset.
- If you get an updated version of this file later, opening it again won't erase your existing progress — your data lives in storage separate from the file itself (tied to your account in Claude, or to your browser in standalone mode).

Good luck, Hunter.
