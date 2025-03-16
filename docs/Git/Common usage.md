### sign with ssh key

edit `~/.giconfig` or `{repo}/.git/config`, add:

```
[gpg]
    format = ssh
[push]
    autoSetupRemote = true
[commit]
    gpgsign = true
```

### set local git config
```
git config --local user.name ""
git config --local user.email ""
```
* (optional, when use sign key)
```
git config --local user.signingkey ""
```

### Delete Remote Branch
[ref @ stackoverflow](https://stackoverflow.com/a/2003515)

`git push <remote_name> --delete <branch_name>`

**Note:** In most cases, `<remote_name>` will be `origin`.

### Run git pull over all subdirectories [duplicate]
[ref @ stackoverflow](https://stackoverflow.com/a/12495234)

* status

  `find . -type d -depth 1 -exec git --git-dir={}/.git --work-tree=$PWD/{} status \;`

* pull

  `find . -type d -depth 1 -exec git --git-dir={}/.git --work-tree=$PWD/{} pull \;`

### Get github repo's size
`$1`: owner

`$2`: repos' name

`shell:`
```shell
$ curl https://api.github.com/repos/$1/$2 2> /dev/null | grep size | tr -dc '[:digit:]'
```

result returned in 'KB'


## 重新上传 commit

* 返回上一个 commit 前状态：
  `git reset --soft HEAD^`
* 更改
* `git commit`
* `git push -f`

----

# Git, sync local to upstream

## Add remote from original repository in your forked repository:

`git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git`
`git fetch upstream`

## Updating your fork from original repo to keep up with their changes:

`git pull upstream master`
`git push`

----

`$ git status`

`$ git diff`

`$ git commit`

`$ git commit -am`  “任意注释”

`$ vim ~/.gitconfig`

`$ git commit -am`  “任意注释”

`$ git pull —rebase origin master`

`$ git push origin master`

`$ git log`             出现各次改动，SHA1及注释

`$ git show 某SHA1`     看相应改动

`$ git reset —soft SHA1`    恢复到”SHA1“这个节点

`$ git reflow -v`           看改动

----

### 5 Git Tips

1. When working with multiple branches you can stash changes away that you are not yet ready to commit:

`git stash save "save message"`

You can then retrieve them later with:

`git stash list`
`git stash pop <stash_item_hash>`

2. When you want to add more changes to the last (local) commit, use:

`git add file(s)`
`git commit --amend`

This opens your editor and lets you modify the last commit.

3. On the other hand, if you want to spread out your changes over multiple commits (granular commits are good!), use:

`git add -p`

Here you can commit only parts ("hunks") of your changes in interactive mode.

4. Imagine you get excited coding, and accidentally commit your changes to the main branch. No worries: if you forget to branch off earlier, you can still do so at this point:

`git branch new_branch`

Now you have your changes on both the original and new branch so you can wipe them out on the former:

`git checkout original_branch`
`git reset HEAD~<number-of-commits-to-go-back>`

(Make sure this is all local though, **don't go modifying changes you already pushed!**)

5. If you want to use a commit from one branch on another, you can cherry pick it:

`git cherry-pick <commit_from_anywhere_in_your_repo>`
