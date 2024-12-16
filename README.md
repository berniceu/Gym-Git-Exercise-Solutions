# Git Exercise

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
