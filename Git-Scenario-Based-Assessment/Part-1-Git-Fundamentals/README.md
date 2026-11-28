# Part 1 – Git Fundamentals

---

## Q1. Starting Version Control for a Billing Project

**Scenario:**

Meera is a first-year student building a billing program in C. Her project folder `billing-app` contains three files, but the folder is not yet under version control. She wants Git to start tracking the project.

**Repository State:**

| File | Git Status |
|---|---|
| billing.c | Not tracked (no repository yet) |
| utils.c | Not tracked (no repository yet) |
| README.md | Not tracked (no repository yet) |

**Task:**

Write the Git commands to:

1. Initialise a new Git repository inside the `billing-app` folder, with `main` as the first branch.
2. Display the repository status so that the three files are listed as untracked.

**Assumption:** Git is installed and the terminal is already open inside the `billing-app` folder.

---

## Q2. Configuring Identity and Making the First Commit

**Scenario:**

Arjun has just installed Git on a new laptop and created a repository for his college website. The folder contains `index.html` and `style.css`. Git does not yet know his name and email, so his commits would not carry the correct author details.

**Repository State:**

| File | Status |
|---|---|
| index.html | Untracked |
| style.css | Untracked |

**Task:**

Write the Git commands to:

1. Set the user name to `Arjun Kumar` and the email to `arjun@example.com` for every repository on this computer.
2. Stage both files.
3. Create the first commit with the message `Add initial landing page`.

**Assumption:** The repository is already initialised and the terminal is inside the project folder.

---

## Q3. Committing Only the Finished Work

**Scenario:**

Divya is working on an attendance tool. She has finished the attendance report, but her personal file `notes.txt` contains rough ideas that she does not want in the project history yet.

**Repository State:**

| File | Status |
|---|---|
| attendance.py | Modified |
| report.py | New (untracked) |
| notes.txt | Modified |

**Task:**

Write the Git commands to:

1. Stage only `attendance.py` and `report.py`.
2. Commit them with the message `Add attendance report`.
3. Check the status to confirm that `notes.txt` is still modified but not committed.

**Assumption:** All three files are in the project root and `notes.txt` is already tracked by Git.

---

## Q4. Joining a Team by Cloning the Repository

**Scenario:**

Priya has joined the TechSoft team. The company stores its inventory project on GitHub at:

`https://github.com/techsoft/inventory-system.git`

She wants a local copy on her laptop, in a folder named `inventory` instead of the default folder name.

**Task:**

Write the Git commands to:

1. Clone the repository into a local folder named `inventory`.
2. Move into that folder.
3. Show the commit history with one line per commit.

**Assumption:** Git is installed and Priya has permission to read the repository.

---

## Q5. Publishing a Local Project to GitHub

**Scenario:**

Karthik has been building a library management app on his laptop. His local repository `library-app` already has three commits on the `main` branch. He has now created an empty repository on GitHub at:

`git@github.com:karthik/library-app.git`

He wants to upload his work.

**Repository State:**

| Branch | Commits | Remote configured |
|---|---:|---|
| main | 3 | None |

**Task:**

Write the Git commands to:

1. Connect the local repository to the GitHub repository using the remote name `origin`.
2. Push the `main` branch and set it as the upstream branch, so that later `git push` and `git pull` need no extra arguments.
3. List the configured remotes to verify the connection.

**Assumption:** The terminal is inside `library-app` and Karthik can already authenticate with GitHub.

---

## Q6. Push Rejected: Syncing with Teammates

**Scenario:**

Two developers share the `main` branch of a payroll project. Sneha committed a change locally and ran `git push`, but Git rejected it with the message below. A teammate had already pushed new commits. Sneha wants to review what her teammate changed before combining it with her own work.

**Error shown after git push:**

```text
! [rejected]     main -> main (fetch first)
error: failed to push some refs to 'origin'
```

**Task:**

Write the Git commands to:

1. Download the latest remote changes without merging them yet.
2. Review the commits that exist on `origin/main` but not on the local `main`.
3. Merge the remote changes into the local `main` branch.
4. Push the combined result to the remote.

**Assumption:** The remote is named `origin`, the current branch is `main`, and the merge completes without conflicts.

---

## Q7. Keeping Passwords and Build Files Out of Git

**Scenario:**

A team is building a C application. The project folder contains source files, a configuration file with the database password, a build folder created by the compiler, and log files. Only the source files should be shared. One log file, `audit.log`, must still be tracked because the auditors need it.

**Repository State:**

| Path | Should Git track it? |
|---|---|
| main.c | Yes |
| utils.c | Yes |
| config.env (contains DB password) | No |
| build/ (compiler output folder) | No |
| debug.log, error.log | No |
| audit.log | Yes (exception) |

**Task:**

Write the content of the `.gitignore` file, and then the Git commands to:

1. Check the status to confirm that only `main.c`, `utils.c`, `audit.log` and `.gitignore` are shown as untracked.
2. Stage and commit these files with the message `Add source files and gitignore`.

**Assumption:** The repository is initialised, nothing has been committed yet, and the files above exist in the project root.

---

## Q8. A Password Was Already Committed

**Scenario:**

Rahul committed and pushed `config.env`, which contains a database password. After noticing, he added `config.env` to `.gitignore`, but `git status` still reports changes to the file every time he edits it.

He must stop Git from tracking the file, yet keep the file on his computer because the app needs it.

**Repository State:**

| Item | State |
|---|---|
| config.env | Tracked and already pushed to origin |
| .gitignore | Contains the line config.env |
| Local copy of config.env | Must stay on disk |

**Task:**

1. Write the Git commands to remove `config.env` from tracking without deleting the local file, commit the change with the message `Stop tracking config.env`, and push it.
2. In one or two sentences, explain why adding the file to `.gitignore` alone did not stop Git from tracking it.
3. In one sentence, state what else Rahul should do about the password that was pushed.

**Assumption:** The remote is `origin`, the branch is `main`, and the terminal is inside the project folder.

---

## Q9. Moving from HTTPS to SSH

**Scenario:**

Rahul keeps being asked for credentials every time he pushes to GitHub over HTTPS, and GitHub no longer accepts his account password for Git operations. His team lead asks him to set up SSH authentication. His payroll repository currently uses an HTTPS remote.

**Repository State:**

| Remote | URL |
|---|---|
| origin | https://github.com/rahul/payroll.git |

**Task:**

Write the commands to:

1. Generate an ed25519 SSH key pair with the comment `rahul@example.com`.
2. Start the SSH agent and add the new private key to it.
3. Display the public key so it can be copied into the GitHub account settings.
4. Test the SSH connection to GitHub.
5. Change the URL of `origin` to `git@github.com:rahul/payroll.git` and verify the change.

**Assumption:** A Linux or macOS terminal is being used, the default key location is selected, and Rahul will paste the public key into GitHub himself.

---

## Q10. Fixing the Last Commit Before Pushing

**Scenario:**

Sneha committed her login page with the message `Add loginn page`. She then noticed two mistakes: the message has a spelling error, and she forgot to include `login.css`. The commit is still only on her laptop and has not been pushed.

**Repository State:**

Local history (newest first):

| Commit | Message | Pushed? |
|---|---|---|
| a1b2c3d | Add loginn page | No |
| 9f8e7d6 | Add database connection | Yes |

Working directory:

| File | Status |
|---|---|
| login.css | New (untracked) |

**Task:**

1. Write the Git commands to add `login.css` to the last commit and correct the message to `Add login page`, without creating a new commit. Then show the history to verify.
2. Explain in one or two sentences why this approach should not be used on a commit that has already been pushed to a shared branch.

**Assumption:** The current branch is `main` and the typo commit is the latest commit.

---


