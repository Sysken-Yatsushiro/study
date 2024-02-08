# wsl cheatsheet

## WSL を初期化

すでに WSL が入っているが、環境を一から作りたくなった人は、ここから始めてください

まだ WSL を入れていない人は下の「WSL をインストール」から始めてください

https://learn.microsoft.com/ja-jp/windows/wsl/install
https://learn.microsoft.com/ja-jp/windows/wsl/basic-commands

```
wsl --list --verbose
```

Ubuntu と表示された人は

```
wsl --unregister Ubuntu
```

Ubuntu 以外が表示された人は、上のコマンドの Ubuntu をその名前に入れ替えてください。

あと、docker-desktop や docker-desktop-beta は unregister しなくて大丈夫です。

## WSL（Ubuntu）をインストール

https://learn.microsoft.com/ja-jp/windows/wsl/install

```
wsl --install -d Ubuntu
```

## Ubuntu setup

Ubuntu を開いて、ユーザー設定を終えたら以下のコマンドを実行

```
sudo apt update && sudo apt upgrade
```

## github cli のインストール

https://github.com/cli/cli/blob/trunk/docs/install_linux.md

```
sudo apt install gh
```

```
gh auth login
```

```
git config --global user.email "Githubに登録したメールアドレス"
```

```
git config --global user.name "Githubに登録したユーザー名"
```

## node.js のインストール（web ページ作ってみたい人だけ）

https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

ターミナルを開きなおしてください。

```
nvm install --lts
```

## python のインストール

https://learn.microsoft.com/en-us/windows/python/web-frameworks

```
sudo apt install python3-pip
```

```
sudo apt install python3-venv
```

### pyenv のインストール（pyenv って何？って人はしなくて大丈夫）

https://github.com/pyenv/pyenv-installer

```
curl https://pyenv.run | bash
```

```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
```

```
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
```

```
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
```

ターミナルを開きなおしてください。

https://github.com/pyenv/pyenv/wiki#suggested-build-environment

```
sudo apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

### pipenv のインストール（Python やる人は入れましょう）

https://pipenv-ja.readthedocs.io/ja/translate-ja/install.html

```
pip install --user pipenv
```

```
echo 'export PIPENV_VENV_IN_PROJECT=1' >> ~/.bashrc
```

ターミナルを開きなおしてください。

### pip のグローバルインストールを防ぐ（pipenv 入れた人限定）

https://stackoverflow.com/questions/27410821/how-to-prevent-pip-install-without-virtualenv

```
python3 -m pip config set global.require-virtualenv True
```

## Pipenv で新しいプロジェクトを作る

プロジェクト名と言っても、要は自分のプログラムに名前を付けるだけです

```
mkdir プロジェクト名
```

```
cd プロジェクト名
```

VSCode で、今作ったディレクトリを開くには：

```
code .
```

Ctrl+J で VSCode 内蔵のターミナルを開いてください

```
pipenv install 入れたいPythonパッケージ名
```

入れたいパッケージを全部入れたら以下を実行：

```
pipenv requirements > requirements.txt
```

## Python で作ったプロジェクトを github にアップロード

```
git init
```

```
echo ".venv" > .gitignore
```

```
git add .
```

```
git commit -m "first commit"
```

```
git branch -m main
```

Github に登録したユーザー名にスペースが入っている場合、以下の URL ではスペースを抜いてください

```
git remote add origin https://github.com/Githubに登録したユーザー名/プロジェクト名.git
```

```
git push -u origin main
```

git 関連は難しいので、わからないことがあれば 4,5 年生を頼ってください。
