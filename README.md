# Git Merge and Rebase Conflicts: A Hands-On Course

A practical, beginner-friendly walkthrough of Git merge and rebase conflicts.

Instead of memorizing commands, you create each type of conflict yourself, read
exactly what Git tells you, and resolve it by hand. By the end you will understand
*why* Git behaves the way it does, which is the part most developers never learn.

The lessons use tiny Python files (one or two lines each) so that nothing gets in
the way of the actual concept being taught.

---

## Who this is for

- Beginners who find merge conflicts confusing or intimidating.
- Developers who can *use* Git but struggle to *explain* why conflicts happen.
- Anyone preparing for real team work or interviews where Git questions come up.

No prior experience with conflicts is assumed. You only need Git installed and a
terminal.

---

## What you will learn

By working through the course you will be able to:

- Explain what a merge conflict actually is and why Git stops instead of guessing.
- Read and resolve conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
- Understand *hunks*, and why "different lines" do not always mean "no conflict."
- Recognize and resolve the three most common conflict types:
  - Content conflict (both sides change the same code)
  - Delete vs Modify (one side deletes a file, the other edits it)
  - Add/Add (both sides create a new file with the same name)
- Use the everyday conflict commands the right way:
  - `git status` to understand the current situation
  - `git merge --abort` to safely cancel a merge
  - `git checkout --ours` / `git checkout --theirs` to pick a side quickly
- Understand merge vs rebase, and why a rebase replays your commits one by one.
- Handle rebase conflicts with `git rebase --continue`, `--skip`, and `--abort`.
- Follow the complete professional workflow: rebase onto `develop`, resolve
  conflicts, and update a pull request with `git push --force-with-lease`.

---

## How the course is structured

Each part teaches one idea and follows the same rhythm: set up a small scenario,
predict what Git will do, run it, then understand *why* it happened.

The lessons live in [docs/](docs/) and are numbered so they read in order.

| Part | Topic | What it covers |
| ---- | ----- | -------------- |
| 1 | [Your First Merge Conflict](docs/01-your-first-merge-conflict/) | Create a same-line conflict, read the markers, resolve and commit. |
| 2 | [When Changes Do Not Conflict](docs/02-when-changes-dont-conflict/) | Why Git can merge automatically, and what a hunk is. |
| 3 | [Delete vs Modify Conflict](docs/03-delete-vs-modify-conflict/) | File-level conflicts that have no conflict markers. |
| 4 | [Add/Add Conflict](docs/04-add-add-conflict/) | Two branches create the same file, plus how often each conflict happens. |
| 5 | [git status and Aborting a Merge](docs/05-git-status-and-aborting-a-merge/) | Reading `git status` mid-merge and safely cancelling with `git merge --abort`. |
| 6 | [Ours, Theirs, and Rebasing](docs/06-ours-theirs-and-rebasing/) | `--ours` / `--theirs`, merge vs rebase, and your first rebase conflict. |
| 7 | [Rebase Skip and Team Workflow](docs/07-rebase-skip-and-team-workflow/) | `git rebase --skip`, the GitHub pull request flow, and `--force-with-lease`. |

### Suggested order

Start at Part 1 and go straight through. Later parts build directly on earlier
ones (for example, rebase conflicts in Part 6 reuse everything from Parts 1 to 5).

---

## The sample files

The `.py` files in the project root are the small working files used during the
exercises. They are intentionally tiny so the conflict, not the code, stays in
focus:

- `app.py`, `calculator.py` — files edited to produce content and rebase conflicts.
- `notes.py` — used for the Delete vs Modify exercise.
- `config.py` — used for the Add/Add exercise.
- `final.py`, `profile.py` — used in the team pull request workflow.

You do not need to read these as real programs. Feel free to recreate or overwrite
them as you follow along.

---

## How to use this course

1. Read a lesson in [docs/](docs/).
2. Run the commands yourself in this repository (or a throwaway copy of it).
3. Before each merge or rebase, pause and predict the outcome.
4. Compare what actually happened with the explanation in the lesson.

The goal is not to finish quickly. It is to reach the point where you can look at
any conflict and answer one question: *what decision is Git unable to make on its
own?*

---

## A note on the docs folder

The `docs/` folder is currently listed in [.gitignore](.gitignore), so it is not
tracked by Git. If you want the lessons to travel with the repository (for example,
when sharing it with others), remove the `docs` line from `.gitignore` and commit
the folder.
