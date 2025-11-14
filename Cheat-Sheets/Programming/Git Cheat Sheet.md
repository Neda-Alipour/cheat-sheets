# 🟩 Git Cheat Sheet


\## 🧠 \*\*Core Git Concepts\*\*



| Concept                  | Description                                                                                                       |

| ------------------------ | ----------------------------------------------------------------------------------------------------------------- |

| \*\*Repository (Repo)\*\*    | A directory where Git tracks all changes. Can be local or remote (e.g., GitHub).                                  |

| \*\*Commit\*\*               | A snapshot of changes. Each commit has a unique ID (hash).                                                        |

| \*\*Branch\*\*               | A pointer to a specific line of development. `main` or `master` is usually the default branch.                    |

| \*\*HEAD\*\*                 | The current commit your working directory is based on. Usually points to the latest commit on the current branch. |

| \*\*Staging Area (Index)\*\* | A place where changes are prepared before committing.                                                             |

| \*\*Remote\*\*               | A version of your repository hosted elsewhere (e.g., GitHub, GitLab).                                             |

| \*\*Merge\*\*                | Combines changes from one branch into another.                                                                    |

| \*\*Rebase\*\*               | Moves or combines commits from one branch onto another, rewriting history.                                        |

| \*\*Detached HEAD\*\*        | When HEAD points directly to a commit instead of a branch.                                                        |

| \*\*Conflict\*\*             | Happens when two branches change the same part of a file differently.                                             |



---



\## ⚙️ \*\*Setup \& Configuration\*\*




git config --global user.name "Your Name"

git config --global user.email "you@example.com"

git config --list                      # View config




---



\## 📁 \*\*Creating \& Cloning Repos\*\*



git init                               # Initialize a new repository

git clone <url>                        # Clone an existing repo

git clone <url> <folder>               # Clone into a specific folder




---



\## 🔍 \*\*Status, Diff, and Log\*\*




git status                             # Show status of working directory

git diff                               # Show unstaged changes

git diff --staged                      # Show staged changes

git log                                # View commit history

git log --oneline --graph --decorate   # Compact visual log

git show <commit>                      # Show details about a commit




---



\## 💾 \*\*Adding \& Committing\*\*




git add <file>                         # Stage a file

git add .                              # Stage all modified files

git commit -m "Message"                # Commit staged changes

git commit -am "Message"               # Add + commit tracked files

git restore --staged <file>            # Unstage a file




---



\## 🌿 \*\*Branching \& Merging\*\*




git branch                             # List branches

git branch <name>                      # Create a branch

git checkout <name>                    # Switch branch

git checkout -b <name>                 # Create and switch

git merge <branch>                     # Merge branch into current

git branch -d <name>                   # Delete a branch

git branch -D <name>                   # Force delete




---



\## 🪄 \*\*Rebase \& Cherry-Pick\*\*




git rebase <branch>                    # Rebase onto another branch

git rebase -i HEAD~3                   # Interactive rebase (last 3 commits)

git cherry-pick <commit>               # Apply a specific commit




---



\## 🌍 \*\*Working with Remotes\*\*




git remote -v                          # List remotes

git remote add origin <url>            # Add a remote

git push -u origin main                # Push branch to remote (first time)

git push                               # Push changes

git pull                               # Fetch + merge changes

git fetch                              # Download changes but don’t merge

git fetch --all                        # Fetch from all remotes




---



\## 🧹 \*\*Undoing Changes\*\*




git restore <file>                     # Discard unstaged changes

git checkout <commit> -- <file>        # Restore file to a specific commit

git reset HEAD~1                       # Undo last commit (keep changes)

git reset --hard HEAD~1                # Undo last commit (discard changes)

git revert <commit>                    # Make a new commit that undoes the specified commit




---



\## 🧩 \*\*Tagging\*\*



git tag                                # List tags

git tag <name>                         # Create a lightweight tag

git tag -a <name> -m "Message"         # Annotated tag

git push origin <tag>                  # Push a tag

git push origin --tags                 # Push all tags





---



\## 🧰 \*\*Stashing\*\*



git stash                              # Save uncommitted changes

git stash list                         # List stashes

git stash apply                        # Reapply last stash

git stash pop                          # Apply and delete last stash

git stash drop                         # Delete last stash



---



\## 🧭 \*\*Collaboration Flow (Typical)\*\*



1\. `git pull origin main` – Get latest code

2\. `git checkout -b feature/new-feature` – Create new branch

3\. Make changes → `git add .` → `git commit -m "Add new feature"`

4\. `git push origin feature/new-feature` – Push to remote

5\. Open a Pull Request (PR)

6\. Merge PR on remote and delete branch



---



\## ⚠️ \*\*Common Fixes\*\*



| Situation                         | Solution                                |

| --------------------------------- | --------------------------------------- |

| Undo last commit but keep changes | `git reset HEAD~1`                      |

| Remove all local changes          | `git reset --hard HEAD`                 |

| Resolve merge conflicts           | Edit files → `git add .` → `git commit` |

| Restore deleted file              | `git checkout HEAD -- <file>`           |

| Rename a branch                   | `git branch -m <old> <new>`             |



---



\## 🧾 \*\*Aliases (optional, for productivity)\*\*




git config --global alias.st status

git config --global alias.co checkout

git config --global alias.br branch

git config --global alias.cm "commit -m"

git config --global alias.lg "log --oneline --graph --decorate --all"




