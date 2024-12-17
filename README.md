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

## Bundle 3
### Exercise 1

```bash

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git checkout -b ft/team-page
Switched to a new branch 'ft/team-page'

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ touch team.html

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git commit -M "create team file"
error: unknown switch `M'
usage: git commit [-a | --interactive | --patch] [-s] [-v] [-u<mode>] [--amend]
                  [--dry-run] [(-c | -C | --squash) <commit> | --fixup [(amend|reword):]<commit>)]
                  [-F <file> | -m <msg>] [--reset-author] [--allow-empty]
                  [--allow-empty-message] [--no-verify] [-e] [--author=<author>]
                  [--date=<date>] [--cleanup=<mode>] [--[no-]status]
                  [-i | -o] [--pathspec-from-file=<file> [--pathspec-file-nul]]
                  [(--trailer <token>[(=|:)<value>])...] [-S[<keyid>]]
                  [--] [<pathspec>...]

    -q, --[no-]quiet      suppress summary after successful commit
    -v, --[no-]verbose    show diff in commit message template

Commit message options
    -F, --[no-]file <file>
                          read message from file
    --[no-]author <author>
                          override author for commit        
    --[no-]date <date>    override date for commit
    -m, --[no-]message <message>
                          commit message
    -c, --[no-]reedit-message <commit>
                          reuse and edit message from specified commit
    -C, --[no-]reuse-message <commit>
                          reuse message from specified commit
    --[no-]fixup [(amend|reword):]commit
                          use autosquash formatted message to fixup or amend/reword specified commit
    --[no-]squash <commit>
                          use autosquash formatted message to squash specified commit
    --[no-]reset-author   the commit is authored by me now (used with -C/-c/--amend)
    --trailer <trailer>   add custom trailer(s)
    -s, --[no-]signoff    add a Signed-off-by trailer       
    -t, --[no-]template <file>
                          use specified template file       
    -e, --[no-]edit       force edit of commit
    --[no-]cleanup <mode> how to strip spaces and #comments from message
    --[no-]status         include status in commit message template
    -S, --[no-]gpg-sign[=<key-id>]
                          GPG sign commit

Commit contents options
    -a, --[no-]all        commit all changed files
    -i, --[no-]include    add specified files to index for commit
    --[no-]interactive    interactively add files
    -p, --[no-]patch      interactively add changes
    -o, --[no-]only       commit only specified files       
    -n, --no-verify       bypass pre-commit and commit-msg hooks
    --verify              opposite of --no-verify
    --[no-]dry-run        show what would be committed      
    --[no-]short          show status concisely
    --[no-]branch         show branch information
    --[no-]ahead-behind   compute full ahead/behind values  
    --[no-]porcelain      machine-readable output
    --[no-]long           show status in long format (default)
    -z, --[no-]null       terminate entries with NUL        
    --[no-]amend          amend previous commit
    --no-post-rewrite     bypass post-rewrite hook
    --post-rewrite        opposite of --no-post-rewrite     
    -u, --[no-]untracked-files[=<mode>]
                          show untracked files, optional modes: all, normal, no. (Default: all)
    --[no-]pathspec-from-file <file>
                          read pathspec from file
    --[no-]pathspec-file-nul
                          with --pathspec-from-file, pathspec elements are separated with NUL character


HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git commit -m "create team file"
[ft/team-page cc111f9] create team file
 1 file changed, 11 insertions(+)
 create mode 100644 team.html

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git push
fatal: The current branch ft/team-page has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin ft/team-page

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.  


HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git push --set-upstream origin ft/team-page
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 416 bytes | 416.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'ft/team-page' on GitHub by visiting:
remote:      https://github.com/berniceu/gym-git-exercise-solutions/pull/new/ft/team-page
remote:
To https://github.com/berniceu/gym-git-exercise-solutions.git
 * [new branch]      ft/team-page -> ft/team-page
branch 'ft/team-page' set up to track 'origin/ft/team-page'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git checkout -b ft/contact-page
Switched to a new branch 'ft/contact-page'

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git checkout ft/team-page
Switched to branch 'ft/team-page'
Your branch is up to date with 'origin/ft/team-page'.       

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git log
commit cc111f96dae459c9546ad051b528849229157113 (HEAD -> ft/team-page, origin/ft/team-page)
Author: uwituzeb <b.uwituze@alustudent.com>
Date:   Tue Dec 17 12:00:11 2024 +0200

    create team file

commit 52a60ca0d44419b153f4d384e71f7b2ee5c87c4a (origin/main, main, ft/contact-page)
Author: uwituzeb <b.uwituze@alustudent.com>
Date:   Tue Dec 17 11:53:40 2024 +0200

    add bundle 3 exercise 2 commands


HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/team-page)
$ git checkout ft/contact-page
Switched to branch 'ft/contact-page'

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git cherry-pick cc111f96dae459c9546ad051b528849229157113
[ft/contact-page 9118e6a] create team file
 Date: Tue Dec 17 12:00:11 2024 +0200
 1 file changed, 11 insertions(+)
 create mode 100644 team.html

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git commit -m "contact page"
[ft/contact-page fb8e7f1] contact page
 1 file changed, 11 insertions(+)
 create mode 100644 contact.html

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git push
fatal: The current branch ft/contact-page has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin ft/contact-page

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.  


HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git push --set-upstream origin ft/contact-page
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 4 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 655 bytes | 655.00 KiB/s, done.
Total 6 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (3/3), completed with 1 local object.
remote:
remote: Create a pull request for 'ft/contact-page' on GitHub by visiting:
remote:      https://github.com/berniceu/gym-git-exercise-solutions/pull/new/ft/contact-page
remote:
To https://github.com/berniceu/gym-git-exercise-solutions.git
 * [new branch]      ft/contact-page -> ft/contact-page     
branch 'ft/contact-page' set up to track 'origin/ft/contact-page'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git checkout ft/faq-page
error: pathspec 'ft/faq-page' did not match any file(s) known to git

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/contact-page)
$ git checkout -b ft/faq-page
Switched to a new branch 'ft/faq-page'

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git commit -m "faq page"
[ft/faq-page c88b5d4] faq page
 1 file changed, 11 insertions(+)
 create mode 100644 faq.html

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git push
fatal: The current branch ft/faq-page has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin ft/faq-page

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.  


HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git push --set-upstream origin ft/faq-page
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 407 bytes | 407.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
Revert "create team file"
remote:
remote: Create a pull request for 'ft/faq-page' on GitHub by visiting:
remote:      https://github.com/berniceu/gym-git-exercise-solutions/pull/new/ft/faq-page
remote:
To https://github.com/berniceu/gym-git-exercise-solutions.git
 * [new branch]      ft/faq-page -> ft/faq-page
branch 'ft/faq-page' set up to track 'origin/ft/faq-page'.  

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git revert cc111f96dae459c9546ad051b528849229157113       
[ft/faq-page 1565b45] Revert "create team file"
 1 file changed, 11 deletions(-)
 delete mode 100644 team.html

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git log
commit 1565b45cd2ce0180e60416f1a7ea47476fba813b (HEAD -> ft/faq-page)
Author: uwituzeb <b.uwituze@alustudent.com>
Date:   Tue Dec 17 12:08:45 2024 +0200

    Revert "create team file"

    This reverts commit cc111f96dae459c9546ad051b528849229157113.

commit c88b5d41d9624a80e1b9243c8736af9c40504dc2 (origin/ft/faq-page)
Author: uwituzeb <b.uwituze@alustudent.com>
Date:   Tue Dec 17 12:07:17 2024 +0200

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git commit -m "revert team page"
On branch ft/faq-page
Your branch is ahead of 'origin/ft/faq-page' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git push
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 272 bytes | 272.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/berniceu/gym-git-exercise-solutions.git
   c88b5d4..1565b45  ft/faq-page -> ft/faq-page

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
```

### Exercise 2

```bash
HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git checkout ft/faq-page
Switched to branch 'ft/faq-page'
Your branch is up to date with 'origin/ft/faq-page'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/faq-page)
$ git checkout -b ft/home-page-redesign
Switched to a new branch 'ft/home-page-redesign'

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git commit -m "add h1 in home file"
[main 752e18e] add h1 in home file
 1 file changed, 1 insertion(+)

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 322 bytes | 322.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/berniceu/gym-git-exercise-solutions.git
   3c402f9..752e18e  main -> main

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (main)
$ git checkout ft/home-page-redesign
Switched to branch 'ft/home-page-redesign'
Your branch is up to date with 'origin/ft/home-page-redesign'.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git rebase main
Successfully rebased and updated refs/heads/ft/home-page-redesign.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git add .

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git commit-m "new changes to home"
git: 'commit-m' is not a git command. See 'git --help'.

The most similar command is
        commit-tree

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git commit -m "new changes to home"
[ft/home-page-redesign abc01b5] new changes to home
 1 file changed, 1 insertion(+)

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git push
To https://github.com/berniceu/gym-git-exercise-solutions.git
 ! [rejected]        ft/home-page-redesign -> ft/home-page-r
Merge branch 'ft/home-page-redesign' of https://github.com/bedesign (non-fast-forward)
error: failed to push some refs to 'https://github.com/berniceu/gym-git-exercise-solutions.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git pull
Merge made by the 'ort' strategy.

HOSA.LTD@DESKTOP-JOJFIGL MINGW64 ~/gym-git-exercise-solutions (ft/home-page-redesign)
$ git push
Enumerating objects: 17, done.
Counting objects: 100% (17/17), done.
Delta compression using up to 4 threads
Compressing objects: 100% (13/13), done.
Writing objects: 100% (13/13), 1.50 KiB | 512.00 KiB/s, done.
Total 13 (delta 7), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (7/7), completed with 2 local objects.
To https://github.com/berniceu/gym-git-exercise-solutions.git
   1565b45..3927764  ft/home-page-redesign -> ft/home-page-redesign

```