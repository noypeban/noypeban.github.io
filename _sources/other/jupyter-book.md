# jupyter-bookの覚え書き

## Install
```sh
pip install -U jupyter-book
```

```{note}
Windowsでinstall後にコマンドが見つからないとなった。
環境変数PathにpythonのScriptディレクトリを追加したらうまくいった
```

## 新規サイト作成時
新規のディレクトリmysiteを作るため、1階層上で実行する
```sh
jupyter-book create mysite
```

なお、`jupyter-book`は省略して`jb`でも通る

## html化
mysiteディレクトリの1階層上で実行
```sh
jupyter-book build mysite
```

もしくは作ったディレクトリの中で
```sh
jupyter-book build .
```

デフォルトでは更新されたファイルだけ再構築されるので、2回目以降はちょっと早くなるはず

## 定義リストを使えるようにする

`_config.yml`に以下の行を追加する
```yml
parse:
  myst_enable_extensions:
    # don't forget to list any other extensions you want enabled,
    # including those that are enabled by default!
    - dollarmath
    - linkify
    - substitution
    - colon_fence
    - deflist
```
一番下の`deflist`がdefinition listの機能フラグ。それより上はデフォルトで有効になっている機能。書いておかないと無効になっちゃう

## Tip
- コンテンツは任意の階層化が可能。TOCにでなくても検索したら出てきた
- 全ページ再作成したい時は`--all`フラグ
  ```shell
  jupyter-book build --all mybookname/
  ```
## .venvを置くとエラー

同じディレクトリに`.venv`ディレクトリを作ってjbを実行するとエラーでhtml生成ができなかった。  
`.venv`ディレクトリの中まで実行しようとしていたのが原因の様子。  
実行対象外ディレクトリに指定してあげるとエラーが出なくなった。

[Exclude pages from your build](https://jupyterbook.org/en/stable/structure/configure.html#exclude-pages-from-your-build)

```yaml
exclude_patterns:
  - .venv/*
```
