# GUI & Teamwork: Personal App Project
### A Multi-Part Programming Project

---

## Overview

In this project you will build a **desktop application using Python and Tkinter** — from a blank window all the way to a polished, functional app. Each Part builds directly on the last, so by the end you have one complete project you can be proud of.

You will also practice real-world developer habits: using **Git and GitHub** to track your progress, writing a **code review** of someone else's work, and reflecting on your own **career direction** as a programmer.

---

## Choose Your Path

Pick one before you write any code.

### 🗂 Path A: Personal Productivity App
Follow the provided spec. You will build a productivity app with a task manager, study timer, and grade calculator. The starter code in `app.py` gives you a working structure to build from — read through it before starting Part 1.

### 🎨 Path B: Your Own App
Design your own app. It must hit all the same technical requirements listed in each Part, but the theme, features, and purpose are entirely up to you. Fill out `my_app_spec.md` before you begin coding — this is your design document and your first Git commit.

> **Not sure?** Go with Path A. You can always personalize it with your own colors, fonts, and feature ideas as you go.

---

## Files in This Project

| File | What it is |
|------|-----------|
| `README.md` | This document — read it before anything else |
| `app.py` | Your main working file — you'll build in this across Parts 1–4 |
| `code_review_sample.py` | A provided code sample you'll review in Part 4 |
| `my_app_spec.md` | Design document template — Path B students fill this out first |

---

## Git Setup — Do This Before Part 1

You will use Git and GitHub to save your progress at the end of every Part. This mirrors how real developers track their work.

### Step 1: Create a GitHub Account
Go to [github.com](https://github.com) and sign up for a free account if you don't have one.

### Step 2: Create a New Repository
- Click the **+** icon → **New repository**
- Name it something like `productivity-app` or your own app's name
- Set visibility to **Public**
- Check **"Add a README file"**
- Click **Create repository**

### Step 3: Connect to Your Project

**On Replit:**
1. Open your Repl and look for the **Git** icon in the left sidebar (it looks like a branch)
2. Click **"Connect to GitHub"** and follow the authorization steps
3. Select **"Connect to an existing GitHub repository"** and choose the one you just created
4. Your project is now linked — you'll commit and push from this panel throughout the project

**On the command line (local development):**
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
```

### Step 4: Add Your Project Files
Upload or copy `app.py`, `code_review_sample.py`, `my_app_spec.md`, and `career_plan.txt` into your Repl or local folder.

### Step 5: Make Your First Commit

**On Replit:**
1. Open the Git panel — you'll see your new files listed under "Changes"
2. Click **+** next to each file to stage it
3. Type a commit message: `Initial commit: project files added`
4. Click **Commit & Push**

**On the command line:**
```bash
git add .
git commit -m "Initial commit: project files added"
git push origin main
```

> ✅ Open GitHub in your browser and confirm your files appear in the repository before moving on.

---

## How to Write a Good Commit Message

At the end of every Part you will commit your work. A commit message should describe *what you did*, not just that you did something.

| Weak | Strong |
|------|--------|
| `changes` | `Part 1: window and widgets set up, using pack layout` |
| `updated stuff` | `Part 2: tabs added, grid layout used in timer frame` |
| `done` | `Part 4: contrast fixed, input validation added after audit` |

Your commit history is part of your grade — make the messages meaningful.

---

## Part 1: The Window & Widgets

### Background

Desktop apps behave differently from scripts or websites. A script runs top-to-bottom and exits. A website lives in a browser and reloads. A desktop app:

- Opens a **persistent window** that stays open until the user closes it
- Is **event-driven** — nothing happens until the user does something (clicks, types, selects)
- **Remembers state** — what you typed, what you added to a list, whether a timer is running
- **Gives feedback** — it tells you when something goes wrong instead of crashing silently

Before writing any code, spend a few minutes with a desktop app you use regularly and notice these qualities. Your app will have all of them by the end of this project.

### Instructions

Open `app.py` and read through it top to bottom before changing anything. You'll see the overall structure: one class, an `__init__` method that sets everything up, and separate methods for each feature.

**Part 1 focuses on `setup_task_manager()`.** The basic structure is already there — your job is to make sure you understand each line, customize it for your app (Path B: replace it with your own first feature), and fill in the comment block at the top of the file.

**By the end of Part 1, your app must have:**

- [ ] A working window with a meaningful title and appropriate size
- [ ] The comment block at the top of `app.py` filled in (your name, project name, description)
- [ ] At least one `Label`
- [ ] At least one `Button` that responds to a click
- [ ] At least one `Entry` field for text input
- [ ] At least one `Listbox` or `Text` widget
- [ ] Widgets laid out using at least one layout manager (`pack` or `grid`)
- [ ] The app runs without errors

**Path B students:** Your first feature should match what you described in `my_app_spec.md`. Build that instead of the Task Manager — same widget requirements apply.

### End of Part 1 — Commit

**Replit:**
1. Open the Git panel, stage your changed files
2. Write a commit message describing what you built
3. Commit & Push

**Command line:**
```bash
git add app.py
git commit -m "Part 1: [describe what you built]"
git push origin main
```

---

## Part 2: Layouts & Navigation

### Background

Tkinter has three layout managers. You should choose based on what you're laying out:

- **`pack()`** — Stacks widgets in a line (top-to-bottom or left-to-right). Fast and simple. Good for headers, button rows, and vertically-stacked sections.
- **`grid()`** — Arranges widgets in rows and columns. Best for forms and anything that needs to line up horizontally.
- **`place()`** — Pixel-precise positioning. Rarely the right choice — avoid it unless you have a specific reason.

A `ttk.Notebook` gives you a tabbed interface, which is the cleanest way to organize multiple features in one window without making it feel cluttered.

> **Important rule:** Never mix `pack()` and `grid()` inside the *same frame*. You can use different layout managers in different frames — that's actually the goal.

### Instructions

Look at `create_menu()` and `create_tabs()` in `app.py` — the tab structure is already set up. Your job in Part 2 is to:

1. Rename the tabs to match your app's features
2. Make sure `setup_study_timer()` is populated with widgets (the structure is provided — read through it and make sure you understand how grid is being used differently from pack in the Task Manager tab)
3. Add a meaningful placeholder to the third tab
4. Update the About dialog in `show_about()` with your name and app description

**By the end of Part 2, your app must have:**

- [ ] A `ttk.Notebook` with at least 3 named tabs
- [ ] `grid()` used in at least one frame
- [ ] `pack()` used in at least one frame
- [ ] A menu bar with File (Save, Load, Exit) and Help (About) menus
- [ ] The About dialog updated with your name and app description
- [ ] A comment in your code explaining why you used each layout manager where you did
- [ ] All tabs visible and clickable (content can still be placeholder in tab 3)

**Path B students:** Replace the provided tab content with your own features. The layout requirements (grid in one frame, pack in another, menu bar) still apply.

### End of Part 2 — Commit

**Replit:**
1. Stage changes, write a commit message that mentions your layout choices
2. Commit & Push

**Command line:**
```bash
git add app.py
git commit -m "Part 2: [describe your tabs and layout decisions]"
git push origin main
```

---

## Part 3: Functional Code Behind the GUI

### Background

So far your app looks like something. Now it needs to *do* something. This part is where most of your logic lives — connecting buttons to real actions, validating what users type, and saving data so the app remembers things between sessions.

The timer introduces a Tkinter pattern worth understanding: **`root.after()`**. Because Tkinter's event loop is always running (waiting for clicks, keypresses, etc.), you can't use a regular `time.sleep()` loop for a countdown — it would freeze the whole window. Instead, `root.after(1000, some_function)` tells Tkinter: *"wait 1 second, then call this function."* The function then schedules itself again, creating a countdown that doesn't block anything else. The `_tick()` method in `app.py` shows exactly how this works — read through it carefully before trying to modify it.

### Instructions

**By the end of Part 3, your app must have:**

- [ ] At least **2 fully functional features** (Task Manager and Study Timer for Path A — or your chosen two features for Path B)
- [ ] At least **5 event handlers** in total (button clicks, key bindings, listbox selections, etc.)
- [ ] **Input validation** on every user input — empty fields and invalid values should show a `messagebox` warning, never a crash
- [ ] **Save** functionality — writes app data to a `.json` file using `filedialog`
- [ ] **Load** functionality — reads that `.json` file back and restores app state
- [ ] Every method has a one-line docstring describing what it does

**Path A — what to implement:**

- `add_task()`, `complete_task()`, `delete_task()` — all three Task Manager actions fully working
- `start_timer()`, `pause_timer()`, `reset_timer()` — timer working with start/pause/resume/reset behavior
- `save_data()` and `load_data()` — saves and restores task list (and timer minutes if you want)

The Grade Calculator tab can remain a placeholder for now. If you finish early, it's a great stretch goal.

**Path B:** Implement whichever two features are highest priority in your spec. Leave a comment in the code noting what's still to be built.

### End of Part 3 — Commit

**Replit:**
1. Stage all changes
2. Write a commit message that names the specific features you completed
3. Commit & Push

**Command line:**
```bash
git add app.py
git commit -m "Part 3: [list what you implemented]"
git push origin main
```

---

## Part 4: Ethical Design & Code Review

---

### Part 4A: Code Review

Open `code_review_sample.py` and run it. Read through the entire file carefully. Then create a new file called `code_review.txt` in your project and write your review there.

Your review must cover all five sections:

**1. What does this app do?**
In 2–3 sentences, describe what the app is supposed to do from a user's perspective.

**2. What works well?**
Identify at least **2 specific things** the code does correctly or clearly. Reference line numbers.

**3. What could break?**
Identify at least **2 things** that could cause an error or unexpected behavior. Describe exactly what a user would need to do to trigger the problem.

**4. Code quality issues**
Identify at least **2 issues** with readability or style — things like variable names, missing comments, duplicated logic, or unclear structure.

**5. One concrete fix**
Pick the single most important problem you found and write the corrected code. Show the before and after side by side.

> A useful code review is specific and actionable. "This is confusing" isn't helpful. "Line 8: the function name `b` should be `add_note` so its purpose is immediately clear" is helpful.

---

### Part 4B: Accessibility & Ethical UI Audit

Read through these principles, then look critically at your own app.

**Contrast** — Text needs to be readable against its background. Light grey on white fails. Dark text on a light background is the safe default.

**Keyboard navigation** — Can a user operate your whole app using only the keyboard? Tab should move between fields, Enter should activate the focused button.

**Clear language** — Labels and error messages should be plain and specific. "Please enter a task name" is better than "Error." "Save" is better than "Commit changes to disk."

**Error handling** — The app should never crash on bad input. It should always explain what went wrong and how to fix it.

**Data privacy** — Think about where your data goes. Your app saves to a local file the user chooses — that means data stays on their machine, which is good. Note this in your audit.

**Deliverable:** Add a section to `code_review.txt` titled `MY APP AUDIT` and include:

- [ ] One specific issue you found in your own app related to the principles above
- [ ] What you changed to fix it (show before/after code if relevant)
- [ ] One thing your app already does well from an ethical or inclusive design standpoint

### End of Part 4 — Commit

**Replit:**
1. Stage `app.py` (with your fixes applied) and `code_review.txt`
2. Commit message should mention both the review and your fixes
3. Commit & Push

**Command line:**
```bash
git add app.py code_review.txt
git commit -m "Part 4: code review complete, accessibility fixes applied"
git push origin main
```

---

## Part 5: Final Polish & Dev Reflection

Use the first part of this session to finish anything incomplete and fix any remaining bugs. Then add a section to `code_review.txt` (or a new `dev_log.txt`) called `DEV REFLECTION` and answer these three questions:

1. What communication and collaboration tools would a real development team use on a project like this? Name at least **3** (e.g. GitHub Issues, pull requests, Slack, project boards) and describe what each is used for.

2. Look at your Git commit history on GitHub. Does it tell the story of how this project developed? What would you do differently with your commits next time?

3. What was the hardest technical problem you ran into? What did you try, and what eventually worked?

### Final Commit

**Replit:**
1. Stage all remaining files
2. Write a final commit message summarizing the whole project in one sentence
3. Commit & Push

**Command line:**
```bash
git add .
git commit -m "Part 5: project complete — [one sentence about what you built]"
git push origin main
```

Then share your GitHub repository link with your instructor.

---

## Grading Overview

| Component | Points |
|-----------|--------|
| Part 1 — Window & Widgets | 15 |
| Part 2 — Layouts & Navigation | 20 |
| Part 3 — Functional Code | 30 |
| Part 4A — Code Review | 15 |
| Part 4B — Ethical UI Audit | 10 |
| Part 5 — Dev Reflection | 5 |
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