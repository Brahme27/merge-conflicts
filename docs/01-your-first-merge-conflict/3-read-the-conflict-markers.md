Great! Now you'll see your **first real merge conflict**.

---

# Step 3 — Merge `feature/f1` into `develop`

First, make sure you're on the `develop` branch.

```bash
git branch
```

You should see:

```text
* develop
```

Now run:

```bash
git merge feature/f1
```

---

## What do you expect?

Many beginners think Git will automatically combine the code.

But remember:

**Before merging**

### `develop`

```python
print("Hello from Develop")
```

### `feature/f1`

```python
print("Hello from Feature")
```

Both branches changed **the same line**.

Git cannot know which one you want.

So instead of making a wrong decision, it stops.

You'll see something similar to:

```text
Auto-merging app.py
CONFLICT (content): Merge conflict in app.py
Automatic merge failed; fix conflicts and then commit the result.
```

This is **not an error**. It's Git asking for your decision.

---

## Now open `app.py`

You'll probably see something like this:

```python
<<<<<<< HEAD
print("Hello from Develop")
=======
print("Hello from Feature")
>>>>>>> feature/f1
```

Let's understand every line.

### `<<<<<<< HEAD`

This means:

> "This is the code from the branch you're currently on."

You're currently on:

```
develop
```

So Git shows:

```python
print("Hello from Develop")
```

---

### `=======`

This is just a separator.

Think of it as:

```
-------------------------
```

It separates the two versions.

---

### `>>>>>>> feature/f1`

Everything below the separator belongs to:

```python
print("Hello from Feature")
```

This is the incoming branch (`feature/f1`).

---

## Think of it like this

```
Current branch (develop)
        ↓
<<<<<<< HEAD
print("Hello from Develop")

========

print("Hello from Feature")
        ↑
Incoming branch (feature/f1)

>>>>>>> feature/f1
```

Git is asking:

> "Which version should become the final code?"

**You** decide.

---

## 🚫 Don't resolve it yet.

I want you to first **see the conflict markers with your own eyes** and understand them.

Reply with:

1. The exact conflict you see in `app.py` (copy and paste it here), or
2. Simply say **"I see it"** if it matches what I showed.

Then we'll resolve it together and you'll understand what each Git command does after resolving a conflict.
