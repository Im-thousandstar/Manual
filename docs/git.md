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
