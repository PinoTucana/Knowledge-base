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
