# Git Exercise

## Bundle 1

### Exercise 1

```bash
mkdir the-gym-git-exercises
cd the-gym-git-exercises/
git init
code .
git branch -m master main
git status
git add .
git commit -m "create readme"
git remote add origin https://github.com/berniceu/gym-git-exercise-solutions.git
git push -u origin main
git checkout -b dev
git checkout -b test
git checkout dev
git branch -d test

```