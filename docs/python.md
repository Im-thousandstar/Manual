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