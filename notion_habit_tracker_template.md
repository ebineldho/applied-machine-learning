# 🧭 Habit Tracker Pro

> A clean, beginner-friendly, premium Notion habit tracker template built as a **single page** with **one core database** and multiple views.

---

## 1) Page Setup (Top Section)

- **Page title (H1):** `🧭 Habit Tracker Pro`
- **Page icon:** `🎯`
- **Cover image (Notion built-in suggestion):** Unsplash cover with a minimal desk/journal theme (e.g., “Productivity” or “Wellness” preset).

### Header content (paste at top of page)

## Welcome

Welcome to your daily habit system. Small consistent actions create big long-term change.

**Today:** `@today`

> “You do not rise to the level of your goals. You fall to the level of your systems.” — James Clear

---

## Quick Daily Snapshot

**Progress Bar:** `▓▓▓▓░░░░░░ 40%`

> You can update this manually each day, or mirror value from a filtered view count.

**Quick Stats:**
- ✅ Completed Today: `3`
- 🔥 Longest Streak: `10`
- 📅 Total Check-ins This Month: `45`

---

## Guidance

<details>
<summary>🎯 <strong>How to Use This Tracker</strong></summary>

1. Add your habits in the **➕ Add New Habit** view.  
2. Each day, open **📅 Today's Habits** and log your **Value Logged** + check **Completed?**.  
3. Review your consistency each week in **🗓️ Weekly Review**.  
4. Update your **Streak** number each day you complete a habit consecutively.

</details>

> 📈 **Daily Progress**  
> Today: **[X] of [X] habits completed — ▓▓▓▓░░░░░░ 40%**

<details>
<summary>🔥 <strong>Streak Tips</strong></summary>

- A streak resets when **Completed?** is unchecked for the day.  
- Update your streak number each morning.  
- Aim for **66 days** — a common habit formation milestone.

</details>

---

## 2) Core Database: Habit Log

Create **one database only** named **Habit Log**.

### Properties

1. **Habit Name** — `Title`
2. **Category** — `Select` with options:
   - 💪 Strength
   - 🧘 Recovery
   - 🥗 Nutrition
   - 💧 Hydration
   - 🏃 Cardio
   - 😴 Sleep
3. **Frequency** — `Select` (`Daily`)
4. **Target** — `Number`
5. **Unit** — `Select`:
   - minutes
   - reps
   - glasses
   - pages
   - times
   - hours
6. **Date** — `Date`
7. **Completed?** — `Checkbox`
8. **Value Logged** — `Number`
9. **Notes** — `Text`
10. **Streak** — `Number`
11. **Week Number** — `Formula`
12. **Completion %** — `Formula`
13. **Progress Bar** — `Formula`
14. **Streak Fire** — `Formula`

### Formula: Week Number

```notion
formatDate(prop("Date"), "W")
```

### Formula: Completion %

```notion
if(prop("Target") > 0, round((prop("Value Logged") / prop("Target")) * 100), 0)
```

### Formula: Progress Bar

```notion
slice("▓▓▓▓▓▓▓▓▓▓", 0, floor(prop("Completion %") / 10)) +
slice("░░░░░░░░░░", 0, 10 - floor(prop("Completion %") / 10)) +
" " + format(prop("Completion %")) + "%"
```

### Formula: Streak Fire

```notion
if(prop("Streak") >= 7, "🔥🔥🔥", if(prop("Streak") >= 3, "🔥🔥", if(prop("Streak") >= 1, "🔥", "💤")))
```

---

## 3) Required Views (All from the same Habit Log database)

## 📅 Today's Habits
- **Layout:** Table
- **Filter:** `Date` → `is` → `Today`
- **Visible properties:** Habit Name, Category, Progress Bar, Completed?, Value Logged, Target, Unit, Streak Fire
- **Sort:** Completed? → Ascending (unchecked first)

## 🗓️ Weekly Review
- **Layout:** Gallery or Table
- **Filter:** `Date` → `is within` → `This week`
- **Group:** Habit Name
- **Visible properties:** Habit Name, Date, Completed?, Value Logged, Progress Bar
- **Sort:** Date → Ascending

## 📊 Monthly Overview
- **Layout:** Table
- **Filter:** `Date` → `is within` → `This month`
- **Group:** Week Number
- **Visible properties:** Habit Name, Date, Completed?, Streak, Progress Bar
- **Sort:** Date → Ascending

## 🏆 Streak Leaderboard
- **Layout:** Table
- **Filter:** None
- **Visible properties:** Habit Name, Streak, Streak Fire, Category, Completion %
- **Sort:** Streak → Descending

## ➕ Add New Habit
- **Layout:** Table
- **Filter:** None
- **Visible properties:** Habit Name, Category, Frequency, Target, Unit

---

## 4) Sample Data (15 entries)

Use these rows so the template looks complete immediately. Set date values to **today**, **yesterday**, and **2 days ago**.

| Habit Name | Category | Frequency | Target | Unit | Date | Completed? | Value Logged | Notes | Streak |
|---|---|---:|---:|---|---|---|---:|---|---:|
| 💧 Drink Water | 💧 Hydration | Daily | 8 | glasses | Today | ✅ | 8 | Hit full hydration | 5 |
| 💧 Drink Water | 💧 Hydration | Daily | 8 | glasses | Yesterday | ✅ | 7 | Slightly under target | 4 |
| 💧 Drink Water | 💧 Hydration | Daily | 8 | glasses | 2 days ago | ✅ | 8 | Perfect day | 3 |
| 🏃 Morning Run | 🏃 Cardio | Daily | 30 | minutes | Today | ✅ | 30 | Easy pace | 3 |
| 🏃 Morning Run | 🏃 Cardio | Daily | 30 | minutes | Yesterday | ✅ | 20 | Short session | 2 |
| 🏃 Morning Run | 🏃 Cardio | Daily | 30 | minutes | 2 days ago | ✅ | 30 | Full run | 1 |
| 💪 Strength Training | 💪 Strength | Daily | 1 | times | Today | ✅ | 1 | Full body workout | 7 |
| 💪 Strength Training | 💪 Strength | Daily | 1 | times | Yesterday | ✅ | 1 | Push day | 6 |
| 💪 Strength Training | 💪 Strength | Daily | 1 | times | 2 days ago | ✅ | 1 | Pull day | 5 |
| 😴 Sleep 8 Hours | 😴 Sleep | Daily | 8 | hours | Today | ✅ | 8 | Solid sleep | 2 |
| 😴 Sleep 8 Hours | 😴 Sleep | Daily | 8 | hours | Yesterday | ❌ | 6 | Late night | 1 |
| 😴 Sleep 8 Hours | 😴 Sleep | Daily | 8 | hours | 2 days ago | ✅ | 8 | Good recovery | 1 |
| 🥗 Eat Vegetables | 🥗 Nutrition | Daily | 3 | times | Today | ✅ | 3 | Great meals | 10 |
| 🥗 Eat Vegetables | 🥗 Nutrition | Daily | 3 | times | Yesterday | ✅ | 2 | Missed dinner portion | 9 |
| 🥗 Eat Vegetables | 🥗 Nutrition | Daily | 3 | times | 2 days ago | ✅ | 3 | Strong nutrition | 8 |

---

## 5) Premium Polish Checklist

- Keep spacing generous; avoid crowded blocks.
- Use dividers (`---`) between all major sections.
- Keep emojis functional, not excessive.
- Keep “Today’s Habits” as the first database view for daily execution.
- Pin this page to favorites for quick daily access.

---

## 6) Final Verification Checklist

- [x] 1 database with all required properties
- [x] 5 named views with correct filters/sorts
- [x] Progress Bar formula included
- [x] Streak Fire formula included
- [x] Sample data scaffold (5 habits × 3 days)
- [x] Instructional callout/toggle content included
- [x] Clean minimal layout with H1/H2 + dividers
- [x] Page icon + cover recommendation included

