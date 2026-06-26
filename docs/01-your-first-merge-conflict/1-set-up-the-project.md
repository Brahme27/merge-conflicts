Perfect. This is actually the best way to learn merge conflicts. We'll make **very tiny changes** so you understand *why* each conflict happens instead of just memorizing commands.

We'll use **Python** because it's easy to read.

# What we'll build

A very small project.

```
merge-conflict-demo/
│
└── app.py
```

We'll pretend:

* `develop` = Main development branch
* `feature/f1` = Your feature branch

We'll create different kinds of conflicts one by one.

---

# What you'll learn

By the end, you'll know practically:

* ✅ What a merge conflict is
* ✅ Why it happens
* ✅ How Git detects it
* ✅ How to read conflict markers
* ✅ How to resolve conflicts
* ✅ Same-line conflicts
* ✅ Different-line changes (no conflict)
* ✅ Delete vs Modify conflict
* ✅ Rename conflicts
* ✅ Add/Add conflict
* ✅ Merge vs Rebase conflicts
* ✅ How VS Code helps
* ✅ Useful Git commands during conflicts
* ✅ Best practices to avoid conflicts

Everything will be done practically.

---

# Part 1 — Create our starting point

Make sure you're on the **develop** branch.

Create `app.py`

```python
print("Hello")
```

Commit it.

```bash
git add .
git commit -m "Initial commit"
```

---

Now switch to your feature branch.

```bash
git checkout feature/f1
```

Verify both branches currently have exactly the same file.

```
app.py

print("Hello")
```

---

### Stop here.

Tell me:

> **Done**

Once you've done this, we'll move to the **first merge conflict**, which is the **most common conflict in real software development**. We'll create it ourselves, see exactly why Git gets confused, and resolve it together.