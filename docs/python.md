# Python 環境構築 using pyenv + pipenv (M1, zsh)

# Python
macのpythonのversino確認
(この二つは同じ意味)
'''
% python -V
% python --version
'''

# Homebrew
Homebrewも確認．
'''
% brew -v
'''

## pyenv
'''
% brew install pyenv 
'''
インストールできるpythonのバージョンを確認
'''
pyenv install --list
'''
最新に近いものをインストール
'''
% pyenv install 3.9.7
'''
インストールできたか確認．
'''
% pyenv versions 
 system
  3.10.0
* 3.9.7 (set by /Users/Blanton/.pyenv/version)
'''

pythonのversionが２系から切り替わらなかった．．．
'''
% pyenv init
% export PYENV_ROOT="$HOME/.pyenv"
% export PATH="$PYENV_ROOT/bin:$PATH"
% eval "$(pyenv init --path)"
% eval "$(pyenv init -)"
'''
これらを実行してから，グローバルに設定．
'''
% pyenv global 3.9.7 
% python --version
Python 3.9.7
'''

# pipenv
'''
% brew install pipenv 
% pipenv --version 
pipenv, version 2021.5.29
'''

任意のプロジェクトを作成し，開発フォルダ内に仮想環境を作成． 
'''
% mkdir testproject
% cd testproject
testproject % export PIPENV_VENV_IN_PROJECT=1
'''

仮想環境でのpythonのversionを指定．
'''
testproject % pipenv --python 3.9.7
'''

仮想環境に入るには，
'''
% pipenv shell
'''
そうしたら，pythonコマンド使える．
'''
% python -V
Python 3.9.7
'''