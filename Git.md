# Git

`$ sudo apt-get install git-all`

###### ##To fix upstart

`$ sudo apt-get purge runit git-daemon-run`

#### tag

```
git fetch --all --tags --prune
```

```
git checkout tags/<tag_name> -b <branch_name>
```

```
# list all tags
$ git tag

# list all tags with given pattern ex: v-
$ git tag --list 'v-*'
```

```
# creat annotated tag
$ git tag -a v1.0
```


#### config
`$ git config --list`

`$ git config --global user.name "myname"`

`$ git config --global user.email *`

#### store
`git config --global credential.helper store`

#### Avoid merge commits
`$ git config --global branch.autosetuprebase always`

#### Set remote ip 
`git remote set-url origin user@ip-address:/git/project`

#### Switch to SSH

`git remote set-url origin git@github.com:EinWTW/SummaryDayByDay.git`

#### Revert changes to modified files
git reset --hard
#### Remove all untracked files and directories.

 (`-f` is `force`, `-d` is `remove directories`)

`git clean -fd`
#### Overwrite local change
git fetch --all
git reset --hard origin/master

git reset HEAD ../tests/
git log

#### work in branch

git fetch

git checkout existing-branch

git branch

git switch devbranch

#### merge master into branch--------

git add
git commit
git pull --rebase
git merge origin/master
-------------------- fix conflict----------------------
git pull origin master
...
git commit
git push origin HEAD

-------------------------------------------------
git checkout feature-8

git pull origin master

//remember pass

$ git config credential.helper store

$ git checkout -b kafka-debug
$ git checkout kafka-debug
$ git add -A
$ git commit

$ git push --set-upstream origin kafka-debug

$ git checkout master
$ git pull
$ sudo git fetch origin master
$ sudo git rebase -i origin/master
#### Squash commits, fix up commit messages etc.
$ git add -A
$ git commit -m "log by vk"

$ git push origin master

git stash
git stash list

git stash pop

#### undo add .
git reset
#### undo last commit
git reset --soft HEAD~1

git tag 0427
git tag

git push --tags

git push
git pull

-------------------------------------------------
vim .gitignore 
#.idea/

git update-index --assume-unchanged .idea/

$ git init
$ git status
& git add . && git add -u .
$ git add -A
$ git commit -m "log by vk"
$ git remote add origin https://github.com/tianwenwvk/development
$ git push origin master
$ git pull https://github.com/tianwenwvk/vklog
$ git pull origin master
$ git revert versionhash/(versionhasha..versionhashb]

$ git clone https://github.com/tianwenwvk/vklog
$ git tag
$ git branch (newbranch)
$ git checkout master
$ git checkout . //undo all changes in 
current working directory
$ git merge newbranch
$ git branch -d newbranch
$ git clean
$ git branch -a --list *release-M*

$ git log
$ git show *
$ git diff 
$ git diff -w / git show -w //This makes the diff algorithm ignore whitespace changes



#### Ensure submodule loaded properly

```
git submodule update --init --recursive
```

```
git config pull.rebase false
```
