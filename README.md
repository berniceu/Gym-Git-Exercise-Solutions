# Git Exercises

This project will be used for a series of git exercises

## Bundle 1

### Exercise 1

```bash
$ mkdir the-gym-git-exercises
$ cd the-gym-git-exercises/
$ git init
Initialized empty Git repository in C:/Users/HOSA.LTD/gym-git-exercise-solutions/.git/

$ code .
$ git branch -m master main
$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
$ git add .
$ git commit -m "create readme"
[main (root-commit) f2f1b3c] create readme
 1 file changed, 9 insertions(+)
 create mode 100644 README.md
$ git remote add origin https://github.com/berniceu/gym-git-exercise-solutions.git
$ git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 255 bytes | 85.00 KiB/s, done. 
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/berniceu/gym-git-exercise-solutions.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
$ git checkout -b dev
Switched to a new branch 'dev'
$ git checkout -b test
Switched to a new branch 'test'
$ git checkout dev
Switched to branch 'dev'
$ git branch -d test
Deleted branch test (was f2f1b3c).
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
$ git add .
$ git commit -m "bundle 1"
[dev 2fa6389] bundle 1
 1 file changed, 14 insertions(+)
 git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 444 bytes | 444.00 KiB/s, done.

Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/berniceu/gym-git-exercise-solutions.git
   f2f1b3c..d902310  main -> main


```

### Exercise 2

```bash

$ touch index.html
$ touch home.html
$ git stash
No local changes to save
$ git add .
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   home.html

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   home.html

$ git add .
$ git stash
Saved working directory and index state WIP on main: f3f0c81 update readme
$ git stash list
stash@{0}: WIP on main: f3f0c81 update readme
$ git stash
No local changes to save
$ git add .
$ git stash
Saved working directory and index state WIP on main: f3f0c81 update readme
$ git add .
$ git stash
Saved working directory and index state WIP on main: f3f0c81 update readme
$ git stash list
stash@{0}: WIP on main: f3f0c81 update readme
stash@{1}: WIP on main: f3f0c81 update readme
stash@{2}: WIP on main: f3f0c81 update readme
$ git stash stash@{1}
fatal: subcommand wasn't specified; 'push' can't be assumed due to unexpected token 'stash@{1}'
$ git stash pop stash@{1}
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   about.html

Dropped stash@{1} (35222f23554f4ee0f753da68d94fdeff40169b6e)
$ git stash list
stash@{0}: WIP on main: f3f0c81 update readme
stash@{1}: WIP on main: f3f0c81 update readme
$ git stash pop stash@{1}
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   about.html
        new file:   home.html

Dropped stash@{1} (ec0c81c58a22d70da831ad24f539ca912355b596)
$ git add .
$ git commit -m "unstash home and about"
[main 36d5211] unstash home and about
 2 files changed, 22 insertions(+)
 create mode 100644 about.html
 create mode 100644 home.html
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 508 bytes | 508.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/berniceu/gym-git-exercise-solutions.git
   f3f0c81..36d5211  main -> main
$ git stash list
stash@{0}: WIP on main: f3f0c81 update readme
$ git stash pop stash@{0}
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   team.html

Dropped stash@{0} (caf29018783d0a560833d0ce7541023afc027e1e)
$ git reset
$ git reset --hard
HEAD is now at 36d5211 unstash home and about
$ git add .
$ git commit -m "revert commit"
[main 6f4b94a] revert commit
 1 file changed, 11 insertions(+)
 create mode 100644 team.html
$ git reset --hard
HEAD is now at 6f4b94a revert commit
$ git reset --hard
HEAD is now at 6f4b94a revert commit
$ git log
commit 6f4b94ab97836f2d9a6947e8ef6a29ee6a167490 (HEAD -> main)
Author: uwituzeb <b.uwituze@alustudent.com>
Date:   Mon Dec 16 13:05:22 2024 +0200

    revert commit

commit 36d521172fad828917cdb9034e46cfb20d5ae59a (origin/main)
Author: uwituzeb <b.uwituze@alustudent.com>
Date:   Mon Dec 16 13:03:15 2024 +0200

    unstash home and about

commit f3f0c8129eaa2ebc433f6783393fc7dbedabdde9
Author: uwituzeb <b.uwituze@alustudent.com>
Date:   Mon Dec 16 12:45:35 2024 +0200
$ git reset --hard 36d521172fad828917cdb9034e46cfb20d5ae59a 
HEAD is now at 36d5211 unstash home and about

```