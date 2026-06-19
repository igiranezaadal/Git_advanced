### creating files
```bash
   touch test{1..4}.md
   git add test1.md && git commit -m "chore: Create initial file"
   git add test2.md && git commit -m "chore: Create another file"
   git add test3.md && git commit -m "chore: Create third and fourth files"
   ```
   # Part 1
   ### Exercise 1
   ``` bash
   git status
   git log
   git add test4.log
   ```
### Exercise 2
    ``` bash
    git git rebase -i HEAD~2
    git add test4.log
    ```
### Exercise 3  Keeping History Tidy - Squashing Commits:
``` bash
    git git rebase -i HEAD~2
    git add test4.log
     git add .
 git status

 git commit -m "Create initial file"
[detached HEAD 24b41a4] Create initial file
2 files changed, 1 insertion(+), 1 deletion(-)
 git push
fatal: You are not currently on a branch.
To push the history leading to the current (detached HEAD)
state now, use

    git push origin HEAD:<name-of-remote-branch>

 git push -u origin main
branch 'main' set up to track 'origin/main'.
Everything up-to-date
unknown option: -i
usage: git [-v | --version] [-h | --help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--no-lazy-fetch]
           [--no-optional-locks] [--no-advice] [--bare] [--git-dir=<path>]
           [--work-tree=<path>] [--namespace=<name>] [--config-env=<name>=<envvar>]
           <command> [<args>]
 git rebase -i HEAD~2 
fatal: It seems that there is already a rebase-merge directory, and
I wonder if you are in the middle of another rebase.  If that is the
case, please try
        git rebase (--continue | --abort | --skip)
If that is not the case, please
        rm -fr ".git/rebase-merge"
and run me again.  I am stopping in case you still have something
valuable there.
```
### Exercise 4 Squashing
``` bash
 git reset HEAD~1
Unstaged changes after reset:
M       Git-exercise
git reset HEAD~1
Unstaged changes after reset:
M       Git-exercise

git add test3.md
git commit -m "Create Third File"
[main d542e6f] Create Third File
 1 file changed, 1 insertion(+)
 create mode 100644 test3.md

git add test4.md
git commit -m "Create Fourth File"
[main e01e30e] Create Fourth File
 1 file changed, 1 insertion(+)
```


### Exercise 5 Advanced Squashing
``` bash
$ git rebase -i HEAD~2
[detached HEAD d5e5c48] Create third and fourth test files
 Date: Mon Jun 15 15:31:55 2026 +0200
 2 files changed, 2 insertions(+)
 create mode 100644 test3.md
Successfully rebased and updated refs/heads/main.
```
### Exercise 6 Droping a Commit:
``` bash
 git log --oneline --graph --decorate --all

* 379fc50 (HEAD -> main) unwanted file
* be8a0c2 Exercise 6
* f9eb1ce unwanted file
* bd5749a testing
* b82a335 chore: create third and forth files
* cafc8c9 chore: create another file
* b85fdde chore create initial file
* e4744a0 (origin/main, origin/HEAD) Update README.md
* 3083f66 Update README
* 826eba3 Update README
* 86ec50c refactor: update README
* be0f35c Update README.md
git reset --hard HEAD~1
*messages...
```

### Exercise 7 Droping a Commit:

``` bash
$ git log --oneline
f263ccc (HEAD -> feature-102) testing 2
6a009bf git-rebase-todo
f5d52a3 first commit

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (feature-102)
$ git rabase -i HEAD~3
git: 'rabase' is not a git command. See 'git --help'.

The most similar command is
        rebase

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (feature-102)
$ git rabase -i HEAD~2
git: 'rabase' is not a git command. See 'git --help'.

The most similar command is
        rebase

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (feature-102)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/feature-102.

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (feature-102)
$ git log -oneline
fatal: unrecognized argument: -oneline

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (feature-102)
$ git log --oneline
f53814e (HEAD -> feature-102) git-rebase-todo
27faef5 testing 2
f5d52a3 first commit
```

# Exercise 8 Cherry-Picking Commits:
``` bash
Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (ft/branch)
$ touch test5.txt

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (ft/branch)
$ ls
AnswerReadMe.md  Git-adv-exercises/  Git-exercise/  README.md  test1.md  test2.md  test3.md  test4.md  test5.txt
$ git commit -m "Implemented test 5"
```
# Exercise 9 Visualizing Commit History (Bonus):
``` bash
$ git log --graph
* commit 32d28df841e872d843cb69b989e66311ebe50fc5 (HEAD -> ft/branch)
| Author: prime Adal <igiranezaadal@gmail.com>
| Date:   Thu Jun 18 14:06:14 2026 +0200
| 
|     Revert "Implemented test 5"
|     
|     This reverts commit 8d064198bd3129ae6a4519a6466199c455220e79.
| 
* commit 8d064198bd3129ae6a4519a6466199c455220e79
| Author: prime Adal <igiranezaadal@gmail.com>
| Date:   Wed Jun 17 16:11:56 2026 +0200
| 
|     Implemented test 5
| 
* commit f53814e07895508426b6411f254be5b9c3839d8b (feature-102)
| Author: prime Adal <igiranezaadal@gmail.com>
| Date:   Wed Jun 10 15:54:20 2026 +0200
| 
|     git-rebase-todo
# Exercise 10 Cherry-Picking Commits:
```

# Exercise 10 Understanding Reflogs (Bonus):
```  bash
$ git reflog
32d28df (HEAD -> ft/branch) HEAD@{0}: revert: Revert "Implemented test 5"
8d06419 HEAD@{1}: commit: Implemented test 5
f53814e (feature-102) HEAD@{2}: checkout: moving from feature-102 to ft/branch
f53814e (feature-102) HEAD@{3}: rebase (finish): returning to refs/heads/feature-102
f53814e (feature-102) HEAD@{4}: rebase (pick): git-rebase-todo
27faef5 HEAD@{5}: rebase (pick): testing 2
f5d52a3 HEAD@{6}: rebase (start): checkout HEAD~2
f263ccc HEAD@{7}: commit: testing 2
6a009bf HEAD@{8}: checkout: moving from main to feature-102
d5e5c48 (main) HEAD@{9}: rebase (finish): returning to refs/heads/main
d5e5c48 (main) HEAD@{10}: rebase (squash): Create third and fourth test files
d542e6f HEAD@{11}: rebase (start): checkout HEAD~2
```




# PART 2

### Exercise 1 Feature Branch Creation:
```bash
$ git switch -c ft/new-feature
Switched to a new branch 'ft/new-feature'

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (ft/new-feature)
$ git branch
  feature-102
  ft/branch
* ft/new-feature
  main
```
### Exercise 2 Working on the Feature Branch:
``` bash
$ touch feature.txt
$ git add .
Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (ft/new-feature)
$ git commit -m "Implemented core functionality for new feature"
[ft/new-feature f59f8af] Implemented core functionality for new feature
 8 files changed, 452 insertions(+), 1 deletion(-)
 create mode 100644 AnswerReadMe.md
 create mode 100644 README.md
 create mode 100644 feature.txt
 create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test5.txt
```

### Exercise 3 Switching Back and Making More Changes:
``` bash
$ git branch --show-current
ft/new-feature
$ git switch main
error: Your local changes to the following files would be overwritten by checkout:
        AnswerReadMe.md
Please commit your changes or stash them before you switch branches.
Aborting
$ git add .

$ git commit -m "update answer"
[ft/new-feature 229466c] update answer
 1 file changed, 8 insertions(+)

$ git switch main
M       Git-exercise
Switched to branch 'main'
Your branch is behind 'origin/main' by 32 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

$ git push -u origin main --force
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/igiranezaadal/Git_advanced.git
 + 5ac81f6...d5e5c48 main -> main (forced update)
branch 'main' set up to track 'origin/main'.

Adal@DESKTOP-NV8O6DJ MINGW64 ~/Documents/coding/git_advanced (main)
$ git switch main
M       Git-exercise
Already on 'main'
Your branch is up to date with 'origin/main'.

$ touch readme.txt

$ git add readme.txt
git_advanced (main)
$ git commit -m "Updated project readme"
[main c75d38e] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt

$ git push
```
### Exercise 4 
``` bash
```
### Exercise 5 
``` bash
```
### Exercise 6 Creating a Branch from a Commit:
```bash
coding/git_advanced (main)
$ git log --oneline --graph
* d5e5c48 (HEAD -> main) Create third and fourth test files
* 6a009bf git-rebase-todo
* f5d52a3 first commit

coding/git_advanced (main)
$ git checkout -b feature-102 6a009bf
M       Git-exercise
Switched to a new branch 'feature-102'

coding/git_advanced (feature-102)
$ git log --oneline --graph
* 6a009bf (HEAD -> feature-102) git-rebase-todo
* f5d52a3 first commit

```
### Exercise 7 
``` bash
```