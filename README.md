# GUI & Teamwork: Personal App Project
### A Multi-Part Programming Project

---

## Overview

In this project you will extend a working Python desktop application by designing and building a brand new feature of your own. You'll read existing code to understand how it works, then apply those same patterns to build something yourself from scratch.

You will also practice real-world developer habits: using **Git and GitHub** to track your work, writing a **code review** of someone else's code, and reflecting on your own career direction as a programmer.

---

## Files in This Project

| File | What it is |
|------|-----------|
| `README.md` | This document — read it before anything else |
| `app.py` | The main app — you will read this, then extend it |
| `code_review_sample.py` | A provided code sample you'll review in Part 3 |
| `career_plan.txt` | Career reflection prompts for Part 4 |

---

## Git Setup — Do This First

You will use Git and GitHub to save your progress at the end of every Part. This mirrors how real development teams track their work.

### Step 1: Create a GitHub Account
Go to [github.com](https://github.com) and sign up for a free account if you don't have one.

### Step 2: Fork This Repository
You are reading this README inside the project repository. Fork it so you have your own personal copy to work in.

1. Click **Fork** in the top-right corner of this page on GitHub
2. Leave all settings as-is and click **Create fork**

Your fork lives at `github.com/YOUR_USERNAME/REPO_NAME`. Any changes you make stay in your fork and don't affect the original.

### Step 3: Import Your Fork into Replit

**Option A — Rapid import (quickest):**
In your browser, go to:
```
https://replit.com/github.com/YOUR_USERNAME/REPO_NAME
```
Replace `YOUR_USERNAME` and `REPO_NAME` with your actual GitHub username and the repo name. Replit will detect the Python project and set it up automatically.

**Option B — Guided import:**
1. Go to [replit.com/import](https://replit.com/import) and sign in
2. Select **GitHub**
3. Connect your GitHub account if prompted
4. Find your forked repository and click **Import**

Either way, Replit will clone your fork and connect to it — you'll commit and push from Replit's Git panel throughout this project.

### Step 4: Verify Everything Works
1. Click **Run** to launch `app.py` and confirm the app opens without errors
2. Click the **Git** icon in the left sidebar — your files should appear under version control
3. Explore all three tabs and the menu before touching any code

### How to Commit at the End of Each Part

**On Replit:**
1. Click the **Git** icon in the left sidebar
2. Click **+** next to each changed file to stage it
3. Type a commit message in the box (see guidance below)
4. Click **Commit & Push**

**On the command line (local development):**
```bash
git add .
git commit -m "your message here"
git push origin main
```

### Writing a Good Commit Message

A commit message should describe *what you did*, not just that you did something.

| Weak | Strong |
|------|--------|
| `changes` | `Part 1: renamed app, read through all methods` |
| `added stuff` | `Part 2: grade calculator tab complete with weighted average logic` |
| `done` | `Part 3: code review written, contrast and validation fixed in my tab` |

Your commit history is part of your grade — make the messages count.

---

## Part 1: Read the Code & Set Up

**Outcomes:** Explain the characteristics and capabilities of Windows apps · Add widgets to a GUI using Tkinter

### Background

Before you write a single line of code, you need to understand what's already here. Open `app.py` and read through the entire file top to bottom. Don't skim — you'll be building something that has to fit into this structure, so understanding it now saves you a lot of confusion later.

As you read, look for answers to these questions:

- What does the `__init__` method do, and why does every setup call happen there?
- How does `setup_task_manager()` use both `pack` and `grid` in the same tab? Why are they in separate frames?
- How does `add_task()` know what the user typed? Trace it from the button click all the way to the listbox.
- What does `root.after(1000, self._tick)` do, and why can't you just use `time.sleep()` instead?
- What does `save_data()` actually write to disk? Open the JSON file after saving and look at it.

Desktop apps behave differently from scripts or websites in a few important ways:
- They are **persistent** — the window stays open until the user closes it
- They are **event-driven** — nothing happens until the user does something
- They **remember state** — data lives in variables while the app runs, and can be saved to a file
- They **give feedback** — a well-built app never crashes silently; it always tells the user what went wrong

### Instructions

Once you've read through the code and can answer the questions above, do the following:

- [ ] Fill in the comment block at the very top of `app.py` — your name, the project name, and a 2–3 sentence description of the app
- [ ] Update `self.root.title(...)` with a name that reflects what your version of the app will be
- [ ] Update the About dialog in `show_about()` with your name and a short description
- [ ] Run the app and try every feature — add tasks, complete them, delete them, run the timer, save and load data. Make sure you understand what every button does before moving on.

### End of Part 1 — Commit

Stage your changes and commit with a message describing what you read and what you changed.

---

## Part 2: Build Your Feature

**Outcomes:** Create advanced GUIs using different layouts in Tkinter · Develop functional code behind a graphical user interface in Tkinter

### The Task

The third tab — `tab_grades` — is currently a placeholder. Your job is to replace it with a fully working feature that you design and build yourself.

Look at how the Task Manager and Study Timer tabs are built. Your feature needs to follow the same patterns:

- A `setup_` method that creates all the widgets and layout for your tab
- Event handler methods that contain the actual logic
- Input validation — bad or empty input should show a `messagebox` warning, never a crash
- At least one integration with `save_data()` and `load_data()` so your feature's data persists

You will need to:
1. Rename `tab_grades` and the notebook tab label to match your feature
2. Replace `setup_grade_calculator()` with your own setup method (or rename and rewrite it)
3. Write your event handler methods
4. Add your data to the `save_data()` and `load_data()` methods

### Choose a Feature

Pick one of the following, or propose your own to your instructor first. Read all four descriptions before deciding — difficulty ratings are honest.

---

#### 🧮 Grade Calculator
**Difficulty: ★★☆☆**

Build a tool where the user enters assignment names, scores, and weights, and the app calculates a weighted average grade.

**What you'll need:**
- Entry fields for assignment name, score (e.g. `88`), and weight (e.g. `20` for 20%)
- An Add button that appends the entry to a display list
- A Listbox or Text widget showing all added assignments
- A Calculate button that computes the weighted average and displays the result
- Validation: score must be 0–100, weight must be a positive number, name can't be empty
- Save/load: the list of assignments should persist between sessions

**Hint on the math:** `weighted average = sum of (score × weight) / sum of all weights`

---

#### 📝 Notes
**Difficulty: ★★☆☆**

Build a note-taking tab where the user can write, save, and reload named notes.

**What you'll need:**
- An Entry field for the note title
- A `Text` widget for the note body (this is different from `Entry` — look it up)
- Buttons to Save Note, Load a selected note, and Clear the current note
- A Listbox or OptionMenu showing the titles of all saved notes
- Validation: title and body can't both be empty when saving
- Save/load: notes persist as a dictionary of `{title: body}` in your JSON file

**Hint:** `Text` widgets use `.get("1.0", tk.END)` to retrieve their contents — not `.get()` like Entry.

---

#### 📅 Task Calendar
**Difficulty: ★★★☆**

Extend the existing Task Manager by adding due dates to tasks, and build a calendar view that shows tasks organized by date.

**What you'll need:**
- Modify `add_task()` to also accept a due date (a simple `YYYY-MM-DD` Entry field is fine)
- A calendar view in your new tab — at minimum, a sorted list of upcoming tasks by due date
- A way to visually distinguish overdue tasks (tasks whose date is before today)
- Validation: date must be a valid format; invalid dates should show a warning
- Save/load: dates must be saved alongside task names

**Hint:** `from datetime import datetime` — use `datetime.strptime(date_string, "%Y-%m-%d")` to convert a string into a date object you can compare against `datetime.today()`.

---

#### 🎮 Focus Friend
**Difficulty: ★★★★**

Build a mini-game that rewards the user for staying productive. Points are earned by completing tasks and finishing timer sessions.

**What you'll need:**
- A points display and level indicator that update in real time
- Points awarded for completing a task (e.g. +10) and finishing a timer session (e.g. +25)
- A level-up system (e.g. every 100 points = new level) with a congratulations popup
- This feature must coordinate with the other tabs — `complete_task()` and the timer's finish condition both need to call into your feature when triggered
- Save/load: points and level persist between sessions

**Hint:** Because this feature reaches into other tabs' logic, study how `complete_task()` and `_tick()` work before writing a single line. You'll be adding a call to a new method (e.g. `self.award_points(10)`) inside those existing methods.

---

### Requirements Checklist

Regardless of which feature you chose, your tab must have:

- [ ] A renamed tab label that matches your feature
- [ ] A `setup_` method containing all widget and layout code for your tab
- [ ] At least **2 different widget types** not already used in your tab (check the quick reference at the bottom)
- [ ] `grid()` or `pack()` used deliberately — add a comment explaining your layout choice
- [ ] At least **2 event handler methods** with working logic
- [ ] Input validation on all user input — no crashes on empty or invalid values
- [ ] Your feature's data included in `save_data()` and loaded back in `load_data()`
- [ ] Every new method has a one-line docstring

### Stretch Goal: Add a Menu Item

Once your feature is working, add a menu item to the existing File or Help menu that does something useful for your feature — for example, "Clear All Notes", "Reset Score", or "Export Tasks". Look at `create_menu()` to see how existing menu items are structured, then add your own.

### End of Part 2 — Commit

Stage all your changes and write a commit message that names your feature and briefly describes what you implemented.

---

## Part 3: Ethical Design & Code Review

**Outcomes:** Discuss the legal and ethical components of user interfaces [Inclusive] · Participate in a peer code review

---

### Part 3A: Code Review

Open `code_review_sample.py` and run it. Read through the entire file carefully. Then create a new file called `code_review.txt` in your project and write your review there.

Your review must cover all five sections:

**1. What does this app do?**
In 2–3 sentences, describe what the app is supposed to do from a user's perspective.

**2. What works well?**
Identify at least **2 specific things** the code does correctly or clearly. Reference line numbers.

**3. What could break?**
Identify at least **2 things** that could cause an error or unexpected behavior. Describe exactly what a user would need to do to trigger the problem.

**4. Code quality issues**
Identify at least **2 issues** with readability or style — variable names, missing comments, duplicated logic, unclear structure.

**5. One concrete fix**
Pick the single most important problem and write the corrected code. Show the before and after.

> A useful code review is specific and actionable. "This is confusing" isn't helpful. "Line 8: the function name `b` should be `add_note` so its purpose is immediately clear" is helpful.

---

### Part 3B: Accessibility & Ethical UI Audit

Read through these principles, then look critically at your own app — especially the tab you built.

**Contrast** — Text needs to be readable against its background. Light grey on white fails. Dark text on a light background is the safe default.

**Keyboard navigation** — Can a user operate your whole app without a mouse? Tab should move between fields, Enter should activate the focused button.

**Clear language** — Labels and error messages should be plain and specific. "Please enter an assignment name" is better than "Error." "Save" is better than "Commit changes to disk."

**Error handling** — The app should never crash on bad input. It should always explain what went wrong and how to fix it.

**Data privacy** — Think about where user data goes. Your app saves to a local file the user chooses — data stays on their machine. Note this in your audit.

**Deliverable:** Add a section to `code_review.txt` titled `MY APP AUDIT` and include:

- [ ] 3 specific issues you found in your own app related to the principles above
- [ ] What you changed to fix each one (before/after code if relevant)
- [ ] One thing your app already does well from an ethical or inclusive design standpoint

### End of Part 3 — Commit

Stage `app.py` (with your fixes applied) and `code_review.txt` and commit.

---

## Part 4: Final Polish & Dev Reflection

**Outcomes:** Select and use appropriate communication tools for programmers

Use the first part of this session to finish anything incomplete and fix remaining bugs. Then add a section called `DEV REFLECTION` to your `code_review.txt` and answer these three questions in full sentences:

1. What communication and collaboration tools would a real development team use on a project like this? Name at least **3** (e.g. GitHub Issues, pull requests, Slack, project boards) and describe what each is used for.

2. Look at your Git commit history on GitHub. Does it tell the story of how this project developed? What would you do differently with your commits next time?

3. What was the hardest technical problem you ran into in Part 2? What did you try, and what eventually worked?

### Final Commit

Stage all remaining files and write a final commit message summarizing the whole project in one sentence. Then share your GitHub repository link with your instructor.

---

## Grading Overview

| Component | Points |
|-----------|--------|
| Part 1 — Code orientation & setup | 10 |
| Part 2 — Feature implementation | 55 |
| Part 3A — Code review | 15 |
| Part 3B — Ethical UI audit | 10 |
| Part 4 — Dev reflection | 5 |
| Git commit history (quality across all parts) | 5 |
| **Total** | **100** |

---

## Quick Reference: Tkinter Widgets

| Widget | What it's for |
|--------|--------------|
| `tk.Label` | Display text |
| `tk.Button` | Clickable button |
| `tk.Entry` | Single-line text input |
| `tk.Text` | Multi-line text area |
| `tk.Listbox` | Scrollable list of items |
| `tk.Scrollbar` | Attach to a Listbox or Text widget |
| `tk.Frame` | Invisible container for grouping widgets |
| `tk.Menu` | Menu bar |
| `ttk.Notebook` | Tabbed interface |
| `ttk.Frame` | Styled container (use inside Notebook tabs) |
| `messagebox` | Popup alerts and confirmations |
| `filedialog` | Open/save file dialogs |
| `tk.OptionMenu` | Dropdown selector |
| `tk.Spinbox` | Numeric input with up/down arrows |
| `tk.Checkbutton` | Checkbox |
