Excellent. We'll now create your **first merge conflict**.

This is the **most common** type of merge conflict you'll see in real projects.

# Step 2 — Change the same line in both branches

Right now both branches have:

```python
print("Hello")
```

## Step A — Stay on `feature/f1`

Check your branch:

```bash
git branch
```

You should see:

```text
* feature/f1
```

Now edit `app.py` to:

```python
print("Hello from Feature")
```

Save the file.

Now commit it.

```bash
git add .
git commit -m "Feature changes greeting"
```

---

## Step B — Switch to `develop`

```bash
git checkout develop
```

Now edit the **same line**.

Instead of:

```python
print("Hello")
```

write:

```python
print("Hello from Develop")
```

Save it.

Commit it.

```bash
git add .
git commit -m "Develop changes greeting"
```

---

## Before merging, let's understand what's happening

Imagine there is one notebook.

Originally it had:

```text
Hello
```

### Person A (`feature/f1`) writes:

```text
Hello from Feature
```

### Person B (`develop`) writes:

```text
Hello from Develop
```

Now Git is asked:

> "Combine these two notebooks."

Git looks at the same line and thinks:

> "Both people changed this exact line differently. I cannot decide which one is correct."

So Git **stops** instead of guessing.

That's a merge conflict.

---

## Don't merge yet.

At this point you should have:

### `feature/f1`

```python
print("Hello from Feature")
```

### `develop`

```python
print("Hello from Develop")
```

Each branch has its own committed change.

---

Reply with **Done**, and in the next step you'll run **one merge command**, see Git produce your first real merge conflict, inspect the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`), and learn exactly what each one means before resolving it.