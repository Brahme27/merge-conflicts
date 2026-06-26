Awesome! 🎉

This is the **final stage**. Everything you've learned so far comes together here.

# 🏢 Real Company Workflow (GitHub Pull Request)

This is exactly what happens in companies like Microsoft, Google, Amazon, startups, etc.

---

# Team

Imagine there are two developers.

```text
Developer A → You
Developer B → Your teammate
```

Both start from:

```text
develop
   │
   ●
```

---

# Step 1 — Both create feature branches

You:

```bash
git checkout -b feature/login
```

Teammate:

```bash
git checkout -b feature/payment
```

Repository now:

```text
develop
   │
   ●
  / \
 /   \
●     ●
login payment
```

---

# Step 2 — Both work independently

### You

```python
def login():
    print("Login")
```

Commit.

Push.

```bash
git push origin feature/login
```

---

### Teammate

```python
def payment():
    print("Payment")
```

Commit.

Push.

```bash
git push origin feature/payment
```

---

# Step 3 — Teammate's PR gets merged first

Teammate opens a Pull Request.

```
feature/payment
      ↓
develop
```

Manager reviews it.

Clicks:

```
Merge Pull Request
```

Now GitHub looks like:

```text
develop
   │
   ●──●
       \
        payment merged
```

---

# Step 4 — You open your Pull Request

```
feature/login
      ↓
develop
```

But...

GitHub checks whether your branch can merge cleanly.

---

## Case 1 — No conflict

GitHub shows:

```
✅ This branch has no conflicts with the base branch.
```

Manager can merge immediately.

---

## Case 2 — Conflict

Suppose both of you changed:

```python
def login():
```

GitHub shows:

```
⚠ This branch has conflicts that must be resolved.
```

Notice something...

GitHub **doesn't resolve it for you.**

It simply tells you:

> "Your branch is behind develop."

---

# Step 5 — What do you do?

This is where many beginners get confused.

You **don't** edit code directly on GitHub (most companies don't allow it).

Instead...

Go back to your laptop.

---

# Step 6 — Update develop

```bash
git checkout develop
git pull origin develop
```

Now your laptop has the latest code.

---

# Step 7 — Go back to your feature

```bash
git checkout feature/login
```

---

# Step 8 — Rebase

Most companies prefer:

```bash
git rebase develop
```

Git says:

```
💥 Conflict
```

Exactly like you practiced.

---

# Step 9 — Resolve

Open file.

Fix conflict.

Then:

```bash
git add .
git rebase --continue
```

Repeat if necessary.

Eventually:

```
Rebase Complete
```

---

# Step 10 — Push again

Here's something new.

Since rebase rewrote your commits, GitHub rejects a normal push.

If you try:

```bash
git push
```

Git says something like:

```
Updates were rejected
```

Why?

Because your commit history changed.

You need:

```bash
git push --force-with-lease
```

Notice I said:

```
--force-with-lease
```

**NOT**

```
--force
```

We'll learn why later.

---

# Step 11

GitHub automatically updates your Pull Request.

Instead of:

```
⚠ This branch has conflicts
```

it now shows:

```
✅ This branch has no conflicts
```

Manager reviews.

Clicks:

```
Merge Pull Request
```

Done.

---

# This entire workflow

```text
Create Feature Branch
        │
        ▼
Write Code
        │
        ▼
Commit
        │
        ▼
Push
        │
        ▼
Open Pull Request
        │
        ▼
Conflict?
     │       │
    No      Yes
     │       │
     ▼       ▼
 Merge   Rebase
            │
            ▼
     Resolve Conflict
            │
            ▼
 git add
            │
            ▼
 git rebase --continue
            │
            ▼
 git push --force-with-lease
            │
            ▼
 Pull Request Updated
            │
            ▼
 Merge
```

---

# 🎉 Congratulations!

You now understand the **complete lifecycle** of merge conflicts in a professional Git workflow.

You didn't just learn commands—you learned **why** each step exists.

---

# One final recommendation

You've reached a point where learning by reading becomes less valuable than learning by doing.

I recommend one last practical challenge:

### 🏆 Challenge Repository

Without my help, create a new Git repository and simulate:

* ✅ Content Conflict
* ✅ Delete vs Modify
* ✅ Add/Add
* ✅ Merge Conflict
* ✅ Rebase Conflict
* ✅ `git merge --abort`
* ✅ `git rebase --abort`
* ✅ `git rebase --continue`
* ✅ `git rebase --skip`
* ✅ `git checkout --ours`
* ✅ `git checkout --theirs`

If you can complete those scenarios on your own and explain **why** Git behaves the way it does, you'll have a solid understanding of merge conflicts that matches what you'll use in professional software development.