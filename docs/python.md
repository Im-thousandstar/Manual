# Python 環境構築 using pyenv + pipenv (M1, zsh)

# Python
macのpythonのversino確認  
(この二つは同じ意味)
```
% python -V
% python --version
```
# Homebrew
Homebrewも確認．
```
% brew -v
```

# pyenv
まずはbrewでインストール．
```
% brew install pyenv 
```
インストールできるpythonのバージョンを確認
```
pyenv install --list
```
最新に近いものをインストール
```
% pyenv install 3.9.7
```
インストールできたか確認．
```
% pyenv versions 
 system
  3.10.0
* 3.9.7 (set by /Users/Blanton/.pyenv/version)
```

pythonのversionが２系から切り替わらなかった．．．
```
% pyenv init
```
これをしてから，
```
% export PYENV_ROOT="$HOME/.pyenv"
% export PATH="$PYENV_ROOT/bin:$PATH"
% eval "$(pyenv init --path)"
% eval "$(pyenv init -)"
```
この４つを実行してから，グローバルに設定．
```
% pyenv global 3.9.7 
% python --version
Python 3.9.7
```

# pipenv
まずはbrewでインストール．
```
% brew install pipenv 
% pipenv --version 
pipenv, version 2021.5.29
```

任意のプロジェクトを作成． 
```
% mkdir jupyter_notebooks
% cd jupyter_notebooks
```
versionを指定して（何も指定しなければStableな最新版が入る），仮想環境とPipfileを作成．
```
jupyter_notebooks % pipenv install --python 3.9.7
```
プロジェクト内には，
```
jupyter_notebooks % ls -a
Pipfile		Pipfile.lock
```
が作成される．  
パッケージをインストールすると，Pipfileに適宜情報が書き込まれる．  
一方で，仮想環境は，
```
User/.local/share/virtualenvs
```
に作成される． 
ちなみに上記のパスは
```
$ pipenv --venv
``` 
で確認できる． 
仮想環境の削除は，
```
% pipenv --rm
```
  
仮想環境に入るには，
```
jupyter_notebooks % pipenv shell
```
そうしたら，通常のpythonのコマンドが使える．
```
(jupyter_notebooks) User@MacBook-Air jupyter_notebooks % python -V
Python 3.9.7
```

仮想環境に入った状態で、pipenvでデータ分析用パッケージをインストールする．
```
(jupyter_notebooks) User@MacBook-Air jupyter_notebooks % pipenv install jupyter numpy scipy pandas scikit-learn keras tensorflow matplotlib seaborn
```
インストールされているパッケージのバージョンアップ/確認
```
$ pipenv update
```
```
$ cat pipfile
```

## 2025追記：windowsへインストール(winはpathがほんとやっかい。。。)
以下のパスを通して、設定→アプリの詳細設定→アプリの実行エイリアスをオフ
```
pythonのpath通す→C:\Users\thous\AppData\Local\Programs\Python\Python313\
pipのpath通す→C:\Users\thous\AppData\Local\Programs\Python\Python313\Scripts\
```
## Pyenv + Pipenv 
[参考記事1](https://zenn.dev/sql_geinin/articles/29f2b0a5c55db2)
[参考記事2](https://zenn.dev/tikita/articles/f7a5bc16c36101#3.-%E5%AE%9F%E9%9A%9B%E3%81%ABpyenv%E3%81%A8pipenv%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6%E3%81%BF%E3%82%8B)
[デジタル署名は出ていませんのエラー](https://qiita.com/sugimochi_1019/items/7be532081fc51992993f)

インストールできたら、指定のフォルダにバージョン指定して仮想環境を作成
```
C:\~>pipenv install --python 3.13.3
```
仮想環境にライブラリを入れる。
```
C:\~>pipenv install  scikit-learn
```
仮想環境に入って
```
C:\~>pipenv shell
```
実行
```
C:\~>python ~.py
```
