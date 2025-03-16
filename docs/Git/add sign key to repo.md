```sh
cd {repo root}
```

```sh
echo [user]\n\t\
name = {github_user}\n\t\
email = {email}\n\t\
signingkey = key::{pub key} >> .git/config
```

Q: 上面，如果 `signingkey = {key path}`，
在签名时会报错：`error: Couldn't load public key /home/repo/xxx.key: No such file or directory?`
（至少在 Chimera）

A: 改成 `signingkey = key::{pub key}` 就没问题
