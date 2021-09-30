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

どうやらデフォがmainになったみたい．

## Personal Access Tokenについて
```
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
```
というエラーが出たので，以下を参照した．
[参考記事:personal access token & key chain](https://zenn.dev/hayata_yamamoto/articles/github-access-key)

[参考記事:github docs](https://docs.github.com/ja/github/getting-started-with-github/getting-started-with-git/updating-credentials-from-the-macos-keychain)

[参考にした記事:access token](https://menta.sutaruhin.com/?p=3420)

githubのページでアクセストークンキーをgenerateし，copy.

pwdの代わりにtokenkeyで認証させた．


