Awesome! 🔥

Now we're entering **professional Git**.

Many developers are comfortable with `git merge`, but they become confused when they see **exactly the same conflict during a rebase**.

By the end of this lesson, you'll know why.

---

# Exercise 8 — Rebase Conflicts

## 🎯 Goal

Understand:

* What `git rebase` does.
* Why conflicts happen during a rebase.
* How resolving a rebase conflict is slightly different from a merge conflict.

---

# Step 1 — First understand Merge vs Rebase

Forget Git commands for a minute.

Let's use a simple story.

---

## Suppose this is your history

```text
A ---- B        develop

 \
  C ---- D      feature
```

You created `feature` from commit `A`.

While you were working:

* `develop` got a new commit `B`.
* You created commits `C` and `D`.

---

## Option 1 — Merge

When you merge:

```bash
git merge feature
```

Git creates a **new merge commit**.

History becomes:

```text
        M
       / \
A ---- B
 \
  C ---- D
```

Notice:

* `C` and `D` stay exactly as they were.
* Git simply creates one new commit `M`.

---

## Option 2 — Rebase

Now instead of merging:

```bash
git rebase develop
```

Git says:

> "I'm going to pretend you started your work after `B`."

It does something clever.

It **replays** your commits.

History becomes:

```text
A ---- B ---- C' ---- D'
```

Notice:

```
C
```

became

```
C'
```

and

```
D
```

became

```
D'
```

These are **new commits**.

This is why people say:

> **Rebase rewrites history.**

---

# What does "replay" mean?

Imagine you're writing notes.

Originally:

```
Notebook 1

Page 1
Page 2
Page 3
```

Now someone gives you a newer notebook.

Instead of copying the whole notebook,

you replay your work.

```
New Notebook

Page 1
Page 2
(New pages)
```

Git does exactly that with commits.

---

# Now the important question

When Git is replaying commit `C`...

What if that commit no longer applies cleanly?

Example:

Original commit:

```python
name = "Alice"
```

But now, after replaying onto the latest `develop`, the file says:

```python
name = "Bob"
```

Git says:

> "I don't know how to replay this commit."

💥

Conflict.

---

# Here's the BIG difference

During a merge, Git says:

> "I'm combining two branches."

During a rebase, Git says:

> "I'm replaying one commit at a time."

This is the key difference.

---

# What happens during a rebase conflict?

Suppose Git is replaying:

```
Commit C
```

It stops and says:

```
Conflict.
```

You fix the file exactly like you already learned.

Then...

❌ You **do not** run:

```bash
git commit
```

This is where many beginners make mistakes.

Instead you run:

```bash
git rebase --continue
```

Why?

Because Git says:

> "Thanks for fixing commit C."

> "Now I'll continue replaying the remaining commits."

---

# Compare

## Merge conflict

```
Conflict
↓
Fix
↓
git add
↓
git commit
```

---

## Rebase conflict

```
Conflict
↓
Fix
↓
git add
↓
git rebase --continue
```

See the difference?

---

# Another useful command

Suppose you're rebasing.

You get 100 conflicts.

You think:

> "No thanks."

Instead of continuing:

```bash
git rebase --abort
```

Git returns everything to how it was before the rebase started.

Notice the similarity?

| Merge               | Rebase               |
| ------------------- | -------------------- |
| `git merge --abort` | `git rebase --abort` |

Very easy to remember.

---

# Quick understanding check

Imagine you're in the middle of a **rebase**.

You fix the conflict.

You run:

```bash
git add app.py
```

Now, what should you run next?

1.

```bash
git commit
```

2.

```bash
git rebase --continue
```

👉 Reply with **1** or **2**, and tell me **why**.

This one question is the biggest difference between merge conflicts and rebase conflicts.
