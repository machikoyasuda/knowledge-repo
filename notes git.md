GIT is a distributed, version control system.

- Distributed: Each team member has full local repo
- Master: name for local 
- Origin: name for remote repo
- password caching

Each team member has her own local repository on her computer. That is the master branch. The Origin is the center on GitHub.


// git help
// git help config (command)

0. git init (create local repo)
1. git status (what has changed, what is tracked)
2. (create file)
3. git add README.txt (add file to staging area)
4. git commit -m "comment" (commit changes)
5. (make more edits)
6. (add files to staging area)
7. (commit)

git add --all (all new/modified)
git add *.txt
git add docs/*.txt (all txt in dir)
git add docs/ (all in dir)
git add "*.txt" (all txt in repo)

git log (see timeline) commit history

git diff (show unstaged diffs since last commit)

git diff -- staged (staged diffs)

HEAD: last commit on current branch (timeline)

----------
git reset - unstage file

git checkout -- file.name blow away / undo changes since last commit & DELETE

git commit -a -m "Modify" - Add changes from all tracked files

git reset --soft HEAD^ - UNDO last commit, put changes back to staging

git reset --hard HEAD^ UNDO last commit AND all changes
git reset --hard HEAD^^ UNDO last 2 commits and all changes

git commit --amend - add a file to a commit you forgot to add
---------

git remote add origin http://.git

git remote -v see all remote repos


---------

git pull - pull changes

//////////

git remote add <name> <address>
git remote rm <name> (remove)
git push -u <name> <branch> (usually master)

-u : so you don't have to use it later

//////////

## Heroku

Install heroku gem

heroku create

git@heroku.com: dev-server0213.git

remote : origin

git push heroku master

Heroku only deploys master branch (no staging or other branches)

git push heroku-staging staging_master (will push and deploy stating on Heroku)


////////


DO NOT RUN RESET AFTER PUSHING. ONLY AFTER STAGING.

///////

# Clone the repository

git clone URL (create local repo in dir)

git clone URL 'name' (custom name)

// Cloning downloads the files and adds origin remote to clone URL. Checks out initial branch (master) and set the head.

# Branching out on your own

// Local branches

got branch cat (new branch from master)

git branch (check what branch)

git checkout cat (switching branch/timelines)

echo "Schrodinger" > cat.txt
git add cat.txt
git commit -m 'Create cat'

(on the branch)

git checkout master (move back to master)

// Remote branches

When you need other people to work on a a branch and will work on it for many days, back it up by pushing it. 

git checkout -b shopping (create and checkout to new branch)

git push origin shopping (link local to remote branch and start tracking)

git pull (new coworker pulls entire repo, can see list of shopping and -> origin/shopping)

git branch -r (list all remote branches)

git checkout shopping

git remote show origin (show all remote branches and tracked or not, which local branches they are config with)

git push origin :shopping (delete remote branch after you are done with feature)

git branch -d shopping (delete local branch)

git remote prune origin (delete stale origins)

# Merge

git merge cat 

Fast-forward: Changes only made on branch, not master. Add and merge branch changes to master.

git branch -d cat (delete cat branch)

Non-fast-forward: Changes made in both branch and master timelines. 

Recursive merging: git log - a commit was created to merge the 2 branches

git checkout -b admin (create and checkout branch)

## Every time you commit, the head moves with it.

VI: :wq, j (down) h (left) k (up) l (right) ESC (leave) i (insert) 


## Collaboration basics

# git pull: (git fetch & pull)
1. Fetch and sync our local with remote, pulls down changes
2. Merges Master with Origin/Master

CONFLICT: Merge conflict

Need to manually change diffs

git commit -a

** Merge commits are bad: Merge commits clog your log, feel useless. The alternative: Rebase

Jane's commit on GitHub is different from Greg's on local. Instead of git push (fetch & pull), do REBASE.

## Tagging

Tag: reference to a specific commit (used for released versioning)

git tag
v0.1
v0.2

git tag v0.1

git tag -a v.0.3 -m "version 3" (add tag)

git push --tag (push new tags)

git checkout v0.2

## Rebase: git rebase

Rebase:
1. Move all changes to master which are not in origin/master to a temporary area

2. Run all origin/master commits.

3. Run all commits in temporary area one at a time. 

----

git checkout admin
git rebase master (run master then admin)
git checkout master
git merge admin

git fetch (from github)
git rebase (move all changes from master to temp area) *(run all origin/master commits) *(run all temp area)

git rebase -- continue
git rebase -- skip
git rebase -- abort

If you're dealing with a branch that has a lot of edits, may want to merge instead of rebase. 

----

git config --global color.ui true
git log --pretty=oneline

git log --oneline --stat
git log --oneline --graph

git log --until=1.minute.ago
git log --since-1.day.ago
git log --since=1.hour.ago
git log --since=1.hour.ago --until=2.weeks.ago
git log --since=2000-0101 --until=2012-12-21

Git log -- graph -- decorate --all
----

# Git diff

git diff: see removed and added lines

git diff HEAD: diff between last commit and current state

git diff HEAD^, ^^, ~5 commits ago, HEAD^..HEAD

git diff SHA..SHA
git log --oneline
git log -p / patch / show diff
git diff abbrevSHA..abbrevSHA
git diff master bird (compare)

git diff --since (time range)

----

git blame index.html --date short
hash, author, when, line #, context

----

## Excluding files

.git/info/exclude
filename/
tutorial.mp4
*.mp4
logs/*.log

// Never put log file into repository. ,gitignore log file.

.gitignore
logs/*.log 

## Removing file from repository

git rm README.txt
git commit -m "remove readme"

## Remove from tracking

git rm --cached development.log

Deleted from git, but not filesystem.

git add .gitignore
git commit
git commit -m "Ignore all log files"

git config --global user.name "NN"
git config --global user.email ""

git config --global core.editor emacs
git config --global merge.tool opendiff

git config user.email "mail@gmail.com"

git config --list

// Aliases: nickname commands

git config alias.(name) (commands)

git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit


