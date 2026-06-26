Awesome! ⭐

This is one of the most misunderstood Git topics, so we'll go **slowly**.

---

# Exercise 7 — `--ours` and `--theirs`

## 🎯 Goal

Instead of manually editing a conflicted file, let Git resolve it for you.

---

# First, understand the idea

Remember this conflict?

```python
<<<<<<< HEAD
print("Hello from Develop")
=======
print("Hello from Feature")
>>>>>>> feature/f1
```

Previously, **you manually deleted** the markers and kept the code you wanted.

That works.

But imagine the file has **2,000 lines**.

You don't want to edit it manually.

Git has shortcuts.

---

# `--ours`

Means:

> **Keep the version from my current branch.**

Suppose you're on:

```text
develop
```

and you run:

```bash
git checkout --ours app.py
```

Git replaces the conflicted file with:

```python
print("Hello from Develop")
```

The conflict markers disappear.

Git keeps **your branch's version**.

---

# `--theirs`

Means:

> **Keep the version from the branch I'm merging into mine.**

If you run:

```bash
git checkout --theirs app.py
```

Git replaces the file with:

```python
print("Hello from Feature")
```

Again, no conflict markers.

---

# Think of it like two papers

You have:

```
Your paper (develop)

Their paper (feature)
```

Git asks:

> Which one do you want?

Instead of editing them together, you can simply say:

```text
Keep mine.
```

or

```text
Keep theirs.
```

---

# Why are they called "ours" and "theirs"?

This confuses almost everyone.

Imagine you're standing on the `develop` branch.

```
You
 ↓
develop
```

Git thinks:

```
Ours = develop
Theirs = feature
```

So if you're on `develop`:

| Command                        | Keeps             |
| ------------------------------ | ----------------- |
| `git checkout --ours app.py`   | `develop` version |
| `git checkout --theirs app.py` | `feature` version |

---

# Here's the important part

The meaning **depends on where you're standing**.

If you switch branches:

```
feature
```

Now Git thinks:

```
Ours = feature
Theirs = develop
```

So **"ours" does not always mean `develop`**.

It means:

> **The branch I'm currently on.**

That's a very important distinction.

---

# Example

You're on:

```
develop
```

Conflict:

```python
<<<<<<< HEAD
name = "Develop"
=======
name = "Feature"
>>>>>>> feature
```

---

You run:

```bash
git checkout --ours app.py
```

Result:

```python
name = "Develop"
```

---

Or:

```bash
git checkout --theirs app.py
```

Result:

```python
name = "Feature"
```

---

Then in both cases you still need:

```bash
git add app.py
git commit
```

Why?

Because choosing a version **doesn't finish the merge**.

It only resolves that file.

You still have to tell Git:

> "I'm done."

---

# Real-world usage

Imagine a generated file like:

```
package-lock.json
```

You don't care about combining it.

You simply want your team's version.

Instead of manually editing hundreds of lines:

```bash
git checkout --theirs package-lock.json
git add package-lock.json
```

Done.

---

# 🧠 Quick check

You're on the `develop` branch.

You get a conflict in:

```
app.py
```

You decide:

> "I don't want my changes. I want exactly what is on `feature/login`."

Which command would you use?

1.

```bash
git checkout --ours app.py
```

2.

```bash
git checkout --theirs app.py
```

And **most importantly**, tell me **why**.

This "why" is the part that makes this concept stick forever.