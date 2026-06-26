Awesome! This is another very common conflict in teams.

# Exercise 4 — Add/Add Conflict

## 🎯 Goal

Learn what happens when:

* Developer A creates a **new file**.
* Developer B also creates a **new file with the same name**.
* But the contents are different.

Git asks:

> **"Which new file do you actually want?"**

---

# Real-world example

Imagine two developers independently decide to create:

```text
config.py
```

Developer A writes:

```python
DATABASE = "mysql"
```

Developer B writes:

```python
DATABASE = "postgres"
```

Neither developer knew the other had already created `config.py`.

When the branches are merged, Git sees:

> "Both branches created a file called `config.py`, but they're different."

Git can't guess which version you want.

---

# Let's do it practically

## Step 1 — Finish the previous merge

If you're still in a merge (`develop|MERGING`), finish it first.

Since we decided to **keep** `notes.py`:

```bash
git add notes.py
git commit -m "Resolve modify/delete conflict by keeping notes.py"
```

Now check:

```bash
git branch
```

You should simply see:

```text
* develop
```

**No `|MERGING` should appear.**

---

## Step 2 — Create a new branch

```bash
git checkout -b feature/f4
```

---

## Step 3 — On `feature/f4`

Create a new file:

```text
config.py
```

Contents:

```python
APP_NAME = "Feature App"
```

Commit it:

```bash
git add .
git commit -m "Feature creates config.py"
```

---

## Step 4 — Switch back to `develop`

```bash
git checkout develop
```

---

## Step 5 — Create the same file

Create **another** `config.py`.

But this time write:

```python
APP_NAME = "Develop App"
```

Commit it:

```bash
git add .
git commit -m "Develop creates config.py"
```

---

# Stop here.

Let's think first.

---

On `develop`:

```python
APP_NAME = "Develop App"
```

On `feature/f4`:

```python
APP_NAME = "Feature App"
```

Notice something important:

* The file **didn't exist before**.
* Both branches **created it independently**.
* Both used the **same filename**.

---

## Question

If Git merges these branches, what should it do?

1. Keep the develop version automatically.
2. Keep the feature version automatically.
3. Stop and ask the developer.

**Reply with 1, 2, or 3, and tell me why.**

*(As before, we always predict first. That's how you'll build strong Git intuition.)*