Perfect! This is the last important rebase command.

# Exercise 9 — `git rebase --skip`

## 🎯 Goal

Understand when to **skip a commit** instead of fixing it.

This is a command you should **use rarely**, but when you need it, it's incredibly useful.

---

# First, understand the idea

Suppose your feature branch has three commits.

```text
Feature Branch

Commit 1
Commit 2
Commit 3
```

Now you run:

```bash
git rebase develop
```

Git starts replaying them.

```
Replay Commit 1 ✅
Replay Commit 2 💥 Conflict
Replay Commit 3
```

Git stops at **Commit 2**.

---

# Normally you would do

```bash
git add .
git rebase --continue
```

This means:

> "I fixed Commit 2. Continue."

---

# But what if...

You look at Commit 2 and think:

> "This commit isn't needed anymore."

For example...

---

## Real company example

You created this commit two weeks ago.

```python
print("Loading...")
```

While you were working...

Another developer added **exactly the same change** to `develop`.

Now during rebase:

Git tries to replay:

```python
print("Loading...")
```

But it already exists.

You think:

> "Why replay this? It's already in develop."

Instead of resolving it, you can say:

```bash
git rebase --skip
```

Git says:

> "Okay."

> "I'll ignore this commit and continue with the next one."

---

# Visualize it

Before:

```
Replay Commit 1 ✅

Replay Commit 2 💥

Replay Commit 3
```

After:

```bash
git rebase --skip
```

Git does:

```
Replay Commit 1 ✅

❌ Ignore Commit 2

Replay Commit 3 ✅
```

---

# Think of copying homework

Suppose your teacher says:

> Copy five paragraphs.

You start.

```
Paragraph 1 ✅
Paragraph 2 ✅
Paragraph 3
```

You reach paragraph 3.

Then you realize:

> "Wait..."

> "Paragraph 3 is already written."

Would you copy it again?

No.

You skip it.

That's exactly what:

```bash
git rebase --skip
```

means.

---

# When should you use it?

✅ Good reasons:

* The commit is no longer needed.
* The same changes already exist.
* The commit was created by mistake.
* You intentionally want to discard that commit.

---

# When should you NOT use it?

Suppose the commit contains:

```python
def login():
```

and skipping it would remove the login feature.

Using:

```bash
git rebase --skip
```

would completely remove that commit from the rebased branch.

That's probably not what you want.

---

# Compare the three commands

| Command                 | Meaning                                                    |
| ----------------------- | ---------------------------------------------------------- |
| `git rebase --continue` | I fixed the conflict. Continue replaying.                  |
| `git rebase --skip`     | Ignore this commit completely. Continue with the next one. |
| `git rebase --abort`    | Cancel the whole rebase.                                   |

---

# 🏢 Real-world example

Imagine your feature branch has these commits:

```
Commit 1
Added login button

Commit 2
Fixed typo in README

Commit 3
Added payment page
```

During rebase:

Git conflicts on **Commit 2**.

But you notice the README typo was already fixed in `develop`.

You don't need your old fix anymore.

So:

```bash
git rebase --skip
```

Git ignores **only Commit 2** and continues with **Commit 3**.

The login button and payment page are still replayed.

---

# 🎯 Prediction

Suppose you're rebasing **5 commits**.

```
Commit 1 ✅

Commit 2 💥

Commit 3

Commit 4

Commit 5
```

You run:

```bash
git rebase --skip
```

### What happens?

**A.** Git cancels the entire rebase.

**B.** Git ignores **only Commit 2** and continues replaying Commits 3, 4, and 5.

**C.** Git deletes all five commits.

👉 Reply with **A**, **B**, or **C**, and explain **why**.

This question is important because it confirms you understand exactly what "skip" skips.