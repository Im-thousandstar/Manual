 # TeXliveのインストール
 ## 　今回インストールしたTeXlive
 `/usr/local/texlive/2021`
 ## 参考記事
 [TeX wiki](https://texwiki.texjp.org/?TeX%20Live%2FMac#k03895bf)  
 [Qiita](https://qiita.com/rainbartown/items/d7718f12d71e688f3573)  
 [TeXフォーラム](https://oku.edu.mie-u.ac.jp/tex/mod/forum/discuss.php?d=2833&parent=16629)  
 [TeX Live 2020をMacBookにインストールする](https://snap.hyuki.net/20210212142647/)
 <br>

 ### TeXLive DL
 ```
 $ curl -OL http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
  ```
### Expand
```
$ tar xvf install-tl-unx.tar.gz
```
### cd expanded dir.
### then, Install
```
$ sudo ./install-tl -no-gui -repository http://mirror.ctan.org/systems/texlive/tlnet/
```
```
Enter command: I
```
### Finish
```
$ sudo /usr/local/texlive/????/bin/*/tlmgr path add
```


