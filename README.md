Pythonのコードスタイル周りを考える会
====
Pythonのコードスタイル及び、lintツールや整形ツールなどの選定をする

## とりあえず選んだもの
  * lintツール - [flake8](http://flake8.pycqa.org/en/latest/)
    - pycodestyle(コーディングスタイル) + pyflakes(論理エラー) + 循環的複雑度のチェックをまとめてできる


  * 整形ツール - [yapf](https://github.com/google/yapf)
    - google製, メジャーな整形ツールだとstar数が一番多い, 柔軟にカスタマイズできる


## ファイル説明
  ```
  ├── .gitignore
  ├── layer_1
  │   └── dirty_code.py
  ├── dirty_code.py
  ├── .flake8
  ├── .style.yapf
  ├── .yapfignore
  ├── README.md
  ├── init_venv.sh
  ├── .pre-commit-config.yaml
  └── requirement.txt
  ```

  * `layer_1/dirty_code.py`
    - 整形対象コード, 汚い


  * `dirty_code.py`
    - 整形対象コード, 汚い


  * `.flake8`
    - flake8の設定ファイル, 無視するルールや除外ディレクトリなどを記述。


  * `.style.yapf`
    - yapfのスタイル設定ファイル, 詳細は[公式のGitHub](https://github.com/google/yapf)参照


  * `.yapfignore`
    - yapfでの整形を行わないファイル・ディレクトリを指定


  * `README.md`
    - 本ファイル


  * `init_venv.sh`
    - venvの作成や必要パッケージのインストールなどを行うスクリプト


  * `.pre-commit-config.yaml`
    - コミット時に走らせるスクリプトを管理するファイル


  * `requirement.txt`
    - pipでインストールするパッケージを記述したファイル


## とりあえず動かす
  動作環境にPython3.7以上がインストールされており、Python3のPATHが通っていることが前提です。

  1. `init_venv.sh` を実行


  2. (プロジェクトルートで) `source .venv/bin/activate` を実行


  4. `flake8 ファイル名(.py)` コマンドを実行する
    … 該当ファイルの構文チェックが実行される


  5. `flake8` コマンドを実行する
    … プロジェクト内の該当ファイル全ての構文チェックが実行される


  6. `yapf ファイル名(.py)` を実行する
    … 該当ファイルのyapf実行後の差分が表示される


  7. `yapf ./ -r` を実行する
    … プロジェクト内の該当ファイル全ての構文チェックが実行される


  8. `yapf ファイル名(.py) -i` を実行する
    … 該当ファイルの整形が実行される

  > **NOTICE :**
    yapfはpep8に完全に準拠するわけではないので、yapfを実行してもflake8のチェックでエラーが出る場合があります

## pre-commitを使ってみる
  commit時に、自動で整形→チェックの処理を行ってくれる。整形後にチェックが通らなければコミットされない。  
  Docker環境を使うことを考えるとプロジェクトメンバーで統一するのはあまり現実的ではないので、やりたい場合は個人で環境を整える。

  1. venvが作成済みで、venvに入っている前提、 `dirty_code.py` は汚い状態に戻す


  2. `pre-commit install` を実行


  3. `dirty_code.py` のファイル名を変更する(何かしらmodifyすればOK)


  4. コンソールから該当ファイルを `add` して `commit` する


  5. yapf + flake8 が実行される
    … 該当ファイルに整形が実行される, flake8 のエラーが表示される


  6. 残ったエラーを手動で修正する


  7. `commit`する
