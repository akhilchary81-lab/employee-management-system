Day 5 Report — Git Revision & Team Collaboration

Project: Employee Management SystemDay: Day 5Topic: Git Revision, Branching, Pull Requests, Merge Conflicts & Recovery

1. Git Revision

Git is a distributed version control system used to track changes in project files and support team collaboration.

Git commands revised

git init
git status
git add .
git commit -m "message"
git log
git log --oneline
git branch
git checkout
git checkout -b branch-name
git pull
git push
git remote -v
git merge
git diff
git restore
git reset
git reflog

Basic Git workflow

Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
  git commit
       ↓
Local Repository
       ↓
   git push
       ↓
GitHub Repository

2. Repository Structure

The Employee Management System repository was organized using a main branch, a development branch, feature branches, and a bug-fix branch.

Employee-Management-System/
│
├── README.md
├── login/
│   └── login.txt
├── profile/
│   └── profile.txt
└── search/
    ├── search.txt
    └── search_bugfix.txt

Branch structure

main
  ↓
develop
  ├── feature/login
  ├── feature/profile
  ├── feature/search
  └── bugfix/search

3. .gitignore

The .gitignore file is used to prevent unnecessary or sensitive files from being tracked by Git.

Example:

# Logs
*.log

# Temporary files
*.tmp
*.temp

# IDE files
.vscode/
.idea/

# Operating system files
.DS_Store
Thumbs.db

# Environment files
.env

After creating .gitignore:

git add .gitignore
git commit -m "Add gitignore configuration"
git push

4. Commit Strategy

Meaningful commits were used so that every commit describes one logical change.

Examples

git commit -m "Initial commit for Employee Management System"
git commit -m "Add employee login functionality"
git commit -m "Add employee profile functionality"
git commit -m "Add employee search functionality"
git commit -m "Fix empty search input validation"

Commit rules followed

Keep commits small and focused.

Use clear commit messages.

Commit completed logical changes.

Avoid meaningless messages such as test, changes, or update.

5. Branching Strategy

A feature-branch workflow was used.

Main branches

mainContains the final stable/released version.

developContains integrated development work before the final release.

Feature branches

feature/login
feature/profile
feature/search

Bug-fix branch

bugfix/search

Workflow

main
  ↓
develop
  ↓
feature branch
  ↓
Code changes
  ↓
Commit
  ↓
Push
  ↓
Pull Request
  ↓
Review
  ↓
Merge → develop

6. Pull Request Workflow

The Pull Request workflow used in the team simulation was:

Create a feature or bug-fix branch from develop.

Make the required code/file changes.

Check the changes using git status.

Stage the changes using git add.

Create a meaningful commit.

Push the branch to GitHub.

Create a Pull Request from the feature branch to develop.

Review the code.

Approve the Pull Request.

Merge the Pull Request into develop.

Pull the latest develop branch locally.

After testing, create a final Pull Request from develop to main.

Review and merge the final release.

Final workflow:

feature/login  ─┐
feature/profile ─┤
feature/search  ─┤→ develop → main
bugfix/search   ─┘

7. Merge Conflict

A merge conflict occurs when Git cannot automatically combine changes from two branches.

For example, if two branches modify the same lines of the same file, Git may stop the merge and report a conflict.

Typical message:

CONFLICT (content): Merge conflict in filename
Automatic merge failed; fix conflicts and then commit the result.

A conflict can be checked with:

git status

8. Conflict Resolution

The conflict-resolution process is:

Step 1 — Check the conflict

git status

Step 2 — Open the conflicted file

A conflicted file may contain markers such as:

<<<<<<< HEAD
Current branch changes
=======
Incoming branch changes
>>>>>>> branch-name

Step 3 — Decide which content to keep

Edit the file and remove the conflict markers:

<<<<<<<
=======
>>>>>>>

Step 4 — Stage the resolved file

git add filename

Step 5 — Complete the merge

git commit -m "Resolve merge conflict"

Step 6 — Push the result

git push

9. Git Recovery Commands

Important Git recovery commands practiced/revised:

Check previous actions

git reflog

git reflog shows previous movements of HEAD and is useful for recovering lost commits.

Restore an unstaged file

git restore filename

Unstage a file

git restore --staged filename

View previous commits

git log --oneline

Recover using a commit

git checkout <commit-id>

Reset to a previous commit

git reset --hard <commit-id>

Note: git reset --hard can permanently discard uncommitted changes, so it should be used carefully.

Cancel an unfinished merge

git merge --abort

Cancel an unfinished rebase

git rebase --abort

10. Problems Faced

Problem 1 — Divergent branches

While pulling from GitHub, Git displayed:

fatal: Need to specify how to reconcile divergent branches.

The local and remote branches had different commits.

The push also displayed:

[rejected] main -> main (non-fast-forward)

Resolution

The remote changes were integrated before pushing again:

git pull origin main --no-rebase

After resolving any conflicts if required:

git push -u origin main

Problem 2 — Understanding branch direction

During the team simulation, it was necessary to understand the correct Pull Request direction.

Feature branches were merged into:

feature/* → develop

The final release was:

develop → main

Problem 3 — Understanding merge conflicts

A merge conflict occurs when Git cannot automatically decide which changes should remain. The solution is to inspect the conflicted file, manually resolve the content, stage it, commit the resolution, and continue.

11. Screenshots

The following screenshots should be added to the final Day 5 submission.

Screenshot 1 — Repository

Show the GitHub Employee Management System repository.

Add screenshot here:

[Insert Screenshot — GitHub Repository]

Screenshot 2 — Branches

Show:

main
develop
feature/login
feature/profile
feature/search
bugfix/search

Add screenshot here:

[Insert Screenshot — GitHub Branches]

Screenshot 3 — Login Pull Request

Show:

feature/login → develop

Add screenshot here:

[Insert Screenshot — Login PR]

Screenshot 4 — Profile Pull Request

Show:

feature/profile → develop

Add screenshot here:

[Insert Screenshot — Profile PR]

Screenshot 5 — Search Pull Request

Show:

feature/search → develop

Add screenshot here:

[Insert Screenshot — Search PR]

Screenshot 6 — Bug-Fix Pull Request

Show:

bugfix/search → develop

Add screenshot here:

[Insert Screenshot — Bug Fix PR]

Screenshot 7 — Merge Conflict

Show the Git conflict message or conflicted file.

Add screenshot here:

[Insert Screenshot — Merge Conflict]

Screenshot 8 — Conflict Resolution

Show the resolved file and successful commit/merge.

Add screenshot here:

[Insert Screenshot — Conflict Resolution]

Screenshot 9 — Final PR

Show:

develop → main

Add screenshot here:

[Insert Screenshot — Final Release PR]

Screenshot 10 — Final Git Status

Show:

git status

with:

nothing to commit, working tree clean

Add screenshot here:

[Insert Screenshot — Final Git Status]

12. What I Learned

During Day 5, I learned how Git is used in a real team development environment.

I learned how to:

Create and manage Git repositories.

Create main and develop branches.

Create feature and bug-fix branches.

Make meaningful commits.

Push branches to GitHub.

Create and review Pull Requests.

Merge feature branches into develop.

Merge develop into main for the final release.

Understand and resolve merge conflicts.

Use .gitignore to exclude unnecessary files.

Use git reflog, git restore, git reset, and other recovery commands.

Troubleshoot divergent branches and non-fast-forward push errors.

Follow a structured Git workflow for team collaboration.

Final workflow learned

Developer
    ↓
Feature/Bugfix Branch
    ↓
Code Changes
    ↓
Commit
    ↓
Push
    ↓
Pull Request
    ↓
Code Review
    ↓
Merge → develop
    ↓
Testing
    ↓
Final Pull Request
    ↓
Merge → main

Conclusion

Day 5 provided practical experience with Git revision, branching, commits, GitHub Pull Requests, code reviews, merge conflicts, conflict resolution, and recovery commands. The Employee Management System simulation demonstrated how multiple developers can work independently and safely integrate their changes into a shared project.
