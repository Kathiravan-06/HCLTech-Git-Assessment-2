# Part 2 – Branching and Merging


---

## Q11. Building a Feature Without Touching main

**Scenario:**

Anitha's team keeps `main` stable at all times. She has been asked to build a search feature for the team's shopping app. She needs a separate line of work where she can commit freely without affecting `main`.

**Repository State:**

| Branch | Purpose |
|---|---|
| main (current) | Stable production code |

**Task:**

Write the Git commands to:

1. Create a new branch named `feature/search` and switch to it in a single command.
2. Confirm the current branch.
3. List all local branches.

**Assumption:** The repository is clean and the current branch is `main`.

---

## Q12. Renaming and Cleaning Up Branches

**Scenario:**

A developer created a branch named `featur/login` by mistake, and it contains the login work. Another branch, `feature/signup`, was merged into `main` last week and is no longer needed. Both exist locally, and `feature/signup` was also pushed to `origin`.

**Repository State:**

| Branch | State |
|---|---|
| featur/login | Misspelled name, work in progress |
| feature/signup | Already merged into main, also on origin |
| main | Stable |

**Task:**

Write the Git commands to:

1. Rename `featur/login` to `feature/login`.
2. Delete the local branch `feature/signup` safely (only if it is fully merged).
3. Delete `feature/signup` from the remote repository `origin`.

**Assumption:** The current branch is `main` and the working directory is clean.

---

## Q13. Merging a Finished Feature in a Straight Line

**Scenario:**

The search feature is finished. Since Anitha created `feature/search` from `main`, nobody has committed anything new to `main`. The team lead wants the history to stay a single straight line with no extra merge commit.

**Repository State:**

Commit history:

| Branch | Commits (oldest to newest) |
|---|---|
| main | C1, C2 |
| feature/search | C1, C2, C3, C4 |

**Task:**

Write the Git commands to:

1. Switch to `main`.
2. Merge `feature/search` so that Git refuses to merge if a fast-forward is not possible.
3. Display the history as a one-line graph to verify the result.

**Assumption:** The working directory is clean and the branches are exactly as shown in the table.

---

## Q14. Merging Parallel Work with a Merge Commit

**Scenario:**

Two developers worked in parallel. Vikram added new commits directly to `main`, while Lakshmi built a reports module in `feature/reports`. They edited different files, so no conflict is expected. The team wants the merge to be visible in the history as a separate merge commit.

**Repository State:**

Commit history (after the common ancestor C2):

| Branch | Commits |
|---|---|
| main | C3 (Vikram: fix tax calculation) |
| feature/reports | C4, C5 (Lakshmi: reports module) |

**Task:**

Write the Git commands to:

1. Switch to `main`.
2. Merge `feature/reports` and always create a merge commit with the message `Merge feature/reports into main`.
3. Display the graph to confirm the merge commit.

**Assumption:** Both branches exist locally, the working directory is clean, and there are no conflicts.

---

## Q15. Resolving a Merge Conflict in the Website Title

**Scenario:**

Vikram changed the page title in `index.html` directly on `main`. At the same time, Lakshmi changed the same line on her branch `feature/footer`. When Vikram tries to merge her branch, Git reports a conflict. After discussion, the team decided the final title must be `TechSoft Student Portal`.

**Repository State:**

`index.html` after the merge attempt:

```html
<<<<<<< HEAD
<title>TechSoft Portal</title>
=======
<title>TechSoft Student Portal</title>
>>>>>>> feature/footer
```

**Task:**

1. Write the command that starts the merge and the command that lists the files with conflicts.
2. Write the final content of the conflicting lines in `index.html` after resolving the conflict.
3. Write the Git commands to mark the file as resolved and complete the merge.

**Assumption:** Vikram is on `main`, the merge was started with `feature/footer`, and `index.html` is the only conflicted file.

---

## Q16. Cancelling a Risky Merge

**Scenario:**

A developer starts merging `feature/payment` into `main`, and Git reports conflicts in three files. The team lead then announces that the payment feature is not ready for release and must not be merged now. The developer has not edited any of the conflicted files.

**Repository State:**

Status after the merge attempt:

| File | Status |
|---|---|
| cart.c | Both modified (conflict) |
| payment.c | Both modified (conflict) |
| orders.c | Both modified (conflict) |

**Task:**

Write the Git commands to:

1. List only the files that are currently in conflict.
2. Cancel the merge and return the repository to the state it was in before the merge started.
3. Verify that the working directory is clean.

**Assumption:** The current branch is `main` and the merge is still in progress.

---

## Q17. Rebasing a Feature onto the Latest main

**Scenario:**

Naveen created `feature/profile` from `main` two days ago. Since then, teammates have added two new commits to `main`. The team policy says every feature branch must be rebased onto the latest `main` before it is merged, so that the final history stays linear. The `feature/profile` branch has not been pushed anywhere.

**Repository State:**

Commit history:

| Branch | Commits (oldest to newest) |
|---|---|
| main | C1, C2, C3, C4 |
| feature/profile | C1, C2, P1, P2 |

**Task:**

Write the Git commands to:

1. Switch to `feature/profile` and rebase it onto `main`.
2. Display the one-line history to confirm that P1 and P2 now sit after C4.
3. Switch to `main` and merge `feature/profile` with a fast-forward.

**Assumption:** There are no conflicts, the working directory is clean, and the local `main` is already up to date.

---

## Q18. Conflict in the Middle of a Rebase

**Scenario:**

Ishita is rebasing `feature/discount` onto `main`. Git stops with a conflict in `pricing.c`, because `main` changed the same line to set a discount of 10 and her branch set it to 15. The business team has confirmed that the correct final discount is 15.

**Repository State:**

`pricing.c` during the rebase:

```c
<<<<<<< HEAD
#define DISCOUNT_RATE 10
=======
#define DISCOUNT_RATE 15
>>>>>>> a4f21c9 (Increase discount to 15)
```

**Task:**

1. Write the final content of the conflicting line in `pricing.c`.
2. Write the Git commands to mark the conflict as resolved and continue the rebase.
3. Write the Git command Ishita could use instead if she decided to cancel the whole rebase and return to the state before it started.

**Assumption:** The rebase is currently paused with `pricing.c` as the only conflicted file.

---

## Q19. Merge or Rebase on a Shared Branch?

**Scenario:**

The branch `feature/api` was pushed to `origin`, and two teammates, Arun and Kavya, have already pulled it and are committing to it. Meanwhile `main` has moved ahead. The developer who started the branch suggests rebasing `feature/api` onto `main` and force-pushing, because it gives a cleaner history.

**Repository State:**

| Branch | Pushed? | Who is using it? |
|---|---|---|
| feature/api | Yes | Three developers |
| main | Yes | Whole team |

**Task:**

1. Decide whether to merge or rebase in this situation, and justify your choice in two or three sentences.
2. Write the Git commands to bring the latest `main` into `feature/api` using your chosen approach and share the result with the team.

**Assumption:** The current branch is `feature/api`, the working directory is clean, and the remote is `origin`.

---

## Q20. Release Week: Feature Branch to Production

**Scenario:**

A team of three is preparing a release of their invoicing system. You must build the invoice feature on its own branch and deliver it to `main` properly. While you are working, a teammate pushes a change to `main` that edits the same lines of `invoice.c` you changed, so you will meet a conflict. The team wants the feature merged with a visible merge commit, and the finished branch removed afterwards.

**Repository State:**

| Item | State |
|---|---|
| Local main | Up to date with origin/main |
| Your task | Create invoice feature |
| Teammate | Will push a conflicting change to invoice.c |
| Remote | origin |

**Task:**

Write the Git commands, in order, to:

1. Create and switch to `feature/invoice`, then commit your changes to `invoice.c` with the message `Add invoice generation`.
2. Fetch the latest changes and merge `origin/main` into `feature/invoice`.
3. Resolve the conflict in `invoice.c` (keep both changes), stage the file, and complete the merge.
4. Push `feature/invoice` to `origin`.
5. Switch to `main`, merge `feature/invoice` with a merge commit, and push `main`.
6. Delete `feature/invoice` locally and on `origin`.

**Assumption:** The conflict appears only in `invoice.c` and you have permission to push to `origin`.

---


