# GitHub
## git に紐づける
```
$ git init   # .git フォルダ作成
$ git add .com # そこにファイル加える
$ git status
$ git commit -m "first commit"
$ git remote add origin http://----- # remote リポジトリと紐づけ
$ git remote add foofoo http://----- # remote リポジトリ2と紐づけ
$ git remote -v
$ git push origin master # repo1にpush
$ git push foofoo master # repo2へpush
```

## Rename repository
```
$ cd .git
$ open config
→　名前変更
$ git remote -v
→　確認
```

## 複数PCから同じアカウントにgitする
[参考記事](https://tips-memo.com/git-same-account)

### ssh key作成 (passwordは空)
```
$ ls ~/.ssh
$ ssh-keygen
```

### 「rd_rsa.pub」の中身をコピー
```
$ cat ~/.ssh/id_rsa.pub
```
GitのsettingページのNew SSHに登録

### PCに登録
```
$ git config --global user.name -----
$ git config --global user.email ----@gmail.com
```

### fetch 取り消し
```
$ git reset --hard HEAD
```

### pushが上手くいかない
```
$ git push origin main
```
.mdでmaster pushができなかったので．．．

## Personal Access Tokenについて
```
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
```
というエラーが出たので，[参考にした記事](https://menta.sutaruhin.com/?p=3420)を見習い，
アクセストークンキーをgenerateし，copy. 
pwdの代わりにtokenkeyで認証させた．


