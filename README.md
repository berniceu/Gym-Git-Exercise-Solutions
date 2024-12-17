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

## Bundle 2

### Exercise 1
```bash
$ git checkout -b ft/bundle-2
Switched to a new branch 'ft/bundle-2'
$ touch services.html
$ git add .
$ git commit -m "create new services file"
[ft/bundle-2 de5c8b0] create new services file
 1 file changed, 11 insertions(+)
 create mode 100644 services.html
$ git push
fatal: The current branch ft/bundle-2 has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin ft/bundle-2

To have this happen automatically for branches without a tracking
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 429 bytes | 429.00 KiB/s, done.Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'ft/bundle-2' on GitHub by visiting:
remote:      https://github.com/berniceu/gym-git-exercise-solutions/pull/new/ft/bundle-2
remote:
To https://github.com/berniceu/gym-git-exercise-solutions.git
 * [new branch]      ft/bundle-2 -> ft/bundle-2
branch 'ft/bundle-2' set up to track 'origin/ft/bundle-2'.
```

### Exercise 2

```bash
HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/bundle-2)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git checkout -b ft/service-redesign
Switched to a new branch 'ft/service-redesign'

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git pull
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (1/1), 909 bytes | 181.00 KiB/s, done.
From https://github.com/berniceu/gym-git-exercise-solutions
   91b4b7d..16d6520  main       -> origin/main
Updating 91b4b7d..16d6520
Fast-forward
 README.md     | 34 +++++++++++++++++++++++++++++++++-
 services.html | 11 +++++++++++
 2 files changed, 44 insertions(+), 1 deletion(-)
 create mode 100644 services.html

# here I repeated the process because I had not pulled before checking out on a new branch
HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git checkout ft/service-redesign
Switched to branch 'ft/service-redesign'

# merged to get the recent changes
HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git merge origin main
merge: origin - not something we can merge

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git merge origin/main
Updating 91b4b7d..16d6520
Fast-forward
 README.md     | 34 +++++++++++++++++++++++++++++++++-
 services.html | 11 +++++++++++
 2 files changed, 44 insertions(+), 1 deletion(-)
 create mode 100644 services.html

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git commit -m "new changes to service page"
[ft/service-redesign ff4d935] new changes to service page
 1 file changed, 1 insertion(+)

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git push
fatal: The current branch ft/service-redesign has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin ft/service-redesign      

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.  


HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git push --set-upstream origin ft/service-redesign 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 332 bytes | 332.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
remote: 
remote: Create a pull request for 'ft/service-redesign' on GitHub by visiting:
remote:      https://github.com/berniceu/gym-git-exercise-solutions/pull/new/ft/service-redesign
remote:
To https://github.com/berniceu/gym-git-exercise-solutions.git
 * [new branch]      ft/service-redesign -> ft/service-redesign
branch 'ft/service-redesign' set up to track 'origin/ft/service-redesign'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git commit -m "new changes"
[main 5093c94] new changes
 1 file changed, 1 insertion(+), 1 deletion(-)

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 314 bytes | 314.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/berniceu/gym-git-exercise-solutions.git
   16d6520..5093c94  main -> main

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git checkout ft/service-redesign
Switched to branch 'ft/service-redesign'
Your branch is up to date with 'origin/ft/service-redesign'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git diff main ft/service-redesign
diff --git a/services.html b/services.html
index eba4c38..02d19ff 100644
--- a/services.html
+++ b/services.html
@@ -6,6 +6,7 @@
     <title>Services</title>
 </head>
 <body>
-    <h2>New changes</h2>
+    <h1>Services Page</h1>
+    
 </body>
 </html>
\ No newline at end of file

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git merge main
Auto-merging services.html
CONFLICT (content): Merge conflict in services.html
Automatic merge failed; fix conflicts and then commit the result.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign|MERGING)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign|MERGING)
$ git commit -m "fix conflicts"
[ft/service-redesign 99f9f6e] fix conflicts

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git push
Enumerating objects: 1, done.
Counting objects: 100% (1/1), done.
Writing objects: 100% (1/1), 215 bytes | 215.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/berniceu/gym-git-exercise-solutions.git
   ff4d935..99f9f6e  ft/service-redesign -> ft/service-redesign


HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/service-redesign)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```