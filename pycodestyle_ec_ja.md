# pycodestyleエラーコード
pycodestyleのエラーの内容をある程度分かるように実際に出るエラーコードと共に意訳する。
コードは主に[Flake8 Rules](https://lintlyci.github.io/Flake8Rules/)から引用している。

## `E1` - インデントに関するエラー

  * `E101` : Indentation contains mixed spaces and tabs
    - インデントにタブとスペースが混在

    **anti pattern** :
    ```python:bad
    class Tab:
        def func():
        	pass

    ```

    **best practice** :
    ```python:good
    class Tab:
        def func():
            pass

    ```


  * `E111` : Indentation is not a multiple of four
    - インデントのスペースが4の倍数個でない

    **anti pattern** :
    ```python:bad
    def func():
      pass

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```


  * `E112` : Expected an indented block
    - インデントすべき箇所にインデントが存在しない

    **anti pattern** :
    ```python:bad
    def func():
    pass

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```

  * `E113` : Unexpected indentation
    - 予期せぬインデントが存在する

    **anti pattern** :
    ```python:bad
        def func():
            pass

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```

  * `E114` : Indentation is not a multiple of four (comment)
    - インデントのスペースが4の倍数個でない(コメント)

    **anti pattern** :
    ```python:bad
    def func():
      # `pass` does nothing
        pass

    ```

    **best practice** :
    ```python:good
    def func():
        # `pass` does nothing
        pass

    ```

  * `E115` : Expected an indented block (comment)
    - インデントすべき箇所にインデントが存在しない(コメント)

    **anti pattern** :
    ```python:bad
    def func():
    # `pass` does nothing
        pass

    ```

    **best practice** :
    ```python:good
    def func():
        # `pass` does nothing
        pass

    ```

  * `E116` : Expected an indented block (comment)
    - 予期せぬインデントが存在する(コメント)

    **anti pattern** :
    ```python:bad
        # This is function
    def func():
        pass

    ```

    **best practice** :
    ```python:good
    # This is function
    def func():
        pass

    ```

  * `E117` : over-indented
    - インデントが深すぎる

    **anti pattern** :
    ```python:bad
    def func():
            pass

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```

  * `E121` <sup><a href="#ignore">\*</a></sup>, <sup><a href="#noqa">^</a></sup>: Continuation line under-indented for hanging indent
    - <a href="#continuous_line">継続行</a>におけるぶら下げインデントが浅い

    **anti pattern** :
    ```python:bad
    {
       'key1': 'value',
       'key2': 'value',
    }

    ```

    **best practice** :
    ```python:good
    {
        'key1': 'value',
        'key2': 'value',
    }

    ```

    **anti pattern** :
    ```python:bad
    print("Python", (
      "Rules"))

    ```

    **best practice** :
    ```pyhon:good
    print("Python", (
        "Rules"))

    ```


  * `E122` <sup><a href="#noqa">^</a></sup> : Continuation line missing indentation or outdented
    - <a href="#continuous_line">継続行</a>のインデントが存在しないか、インデントレベルが上回っている

    **anti pattern** :
    ```python:bad
    {
    'key1': 'value',
    'key2': 'value',
    }

    ```

    **best practice** :
    ```python:good
    {
        'key1': 'value',
        'key2': 'value',
    }

    ```

  * `E123` <sup><a href="#ignore">\*</a></sup> : Closing bracket does not match indentation of opening bracket’s line
    - 閉じ括弧が開き括弧の行のインデントレベルと一致していない

    **anti pattern** :
    ```python:bad
    {
        'key1': 'value',
        'key2': 'value',
        }

    ```

    **best practice** :
    ```python:good
    {
        'key1': 'value',
        'key2': 'value',
    }

    ```

    **anti pattern** :
    ```python:bad
    result = function_that_takes_arguments(
        'a', 'b', 'c',
        'd', 'e', 'f',
        )

    ```

    **best practice** :
    ```python:good
    result = function_that_takes_arguments(
        'a', 'b', 'c',
        'd', 'e', 'f',
    )

    ```


  * `E124` <sup><a href="#noqa">^</a></sup> : Closing bracket does not match visual indentation
    - 閉じ括弧のインデントが視覚的に統一できていない

    **anti pattern** :
    ```python:bad
    result = function_that_takes_arguments('a', 'b', 'c',
                                           'd', 'e', 'f',
    )

    ```

    **best practice** :
    ```python:good
    result = function_that_takes_arguments('a', 'b', 'c',
                                           'd', 'e', 'f',
                                           )

    ```


  * `E125` <sup><a href="#noqa">^</a></sup> : Continuation line with same indent as next logical line
    - <a href="#continuous_line">継続行</a>のインデントレベルが次に続く論理行と同じインデントレベルになっている  
     (継続行が次に続く論理行と同じインデントになる場合は継続行のインデントレベルをさらに上げる)

    **anti pattern** :
    ```python:bad
    if user is not None and user.is_admin or \
        user.name == 'Grant':
        blah = 'yeahnah'

    ```

    **best practice** :
    ```python:good
    if user is not None and user.is_admin or \
            user.name == 'Grant':
        blah = 'yeahnah'

    ```

  * `E126` <sup><a href="#ignore">\*</a></sup>,<sup><a href="#noqa">^</a></sup> : Continuation line over-indented for hanging indent
    - <a href="#continuous_line">継続行</a>のインデントが深すぎる

    **anti pattern** :
    ```python:bad
    {
            'key1': 'value',
            'key2': 'value',
    }

    ```

    **best practice** :
    ```python:good
    {
        'key1': 'value',
        'key2': 'value',
    }

    ```

  * `E127` <sup><a href="#noqa">^</a></sup> : Continuation line over-indented for visual indent
    - <a href="#continuous_line">継続行</a>のインデントが、視覚的に統一するためのインデントよりも深い

    **anti pattern** :
    ```python:bad
    print("Python", ("Hello",
                       "World"))

    ```

    **best practice** :
    ```python:good
    print("Python", ("Hello",
                     "World"))

    ```

  * `E128` <sup><a href="#noqa">^</a></sup> : Continuation line under-indented for visual indent
    - <a href="#continuous_line">継続行</a>のインデントが、視覚的に統一するためのインデントよりも浅い

    **anti pattern** :
    ```python:bad
    print("Python", ("Hello",
                   "World"))

    ```

    **best practice** :
    ```python:good
    print("Python", ("Hello",
                     "World"))

    ```

  * `E129` <sup><a href="#noqa">^</a></sup> : Visually indented line with same indent as next logical line
    - 視覚的に統一するためのインデントが次に続く論理行と同じインデントレベルになっている

    **anti pattern** :
    ```python:bad
    if (row < 0 or module_count <= row or
        col < 0 or module_count <= col):
        raise Exception("%s,%s - %s" % (row, col, self.moduleCount))

    ```

    **best practice** :
    ```python:good
    if (row < 0 or module_count <= row or
            col < 0 or module_count <= col):
        raise Exception("%s,%s - %s" % (row, col, self.moduleCount))

    ```


  * `E131` <sup><a href="#noqa">^</a></sup> : Continuation line unaligned for hanging indent
    - <a href="#continuous_line">継続行</a>のぶら下げのインデントの位置が合っていない

    **anti pattern** :
    ```python:bad
    {
        "key1": "value",
        "key2": "value value value"
            "value",
    }

    ```

    **best practice** :
    ```python:good
    {
        "key1": "value",
        "key2": "value value value"
                "value",
    }

    ```


  * `E133` <sup><a href="#ignore">\*</a></sup> : Closing bracket is missing indentation
    - 閉じ括弧にインデントがない  
    (`--hang-closing` オプションが使用されている場合にのみ発生)

    **anti pattern** :
    ```python:bad
    my_list = [
        1, 2, 3,
        4, 5, 6,
    ]

    ```

    **best practice** :
    ```python:good
    my_list = [
        1, 2, 3,
        4, 5, 6,
        ]

    ```

  * `E131` <sup><a href="#noqa">^</a></sup> : Continuation line unaligned for hanging indent
    - <a href="#continuous_line">継続行</a>のぶら下げのインデントの位置が合っていない

    **anti pattern** :
    ```python:bad
    {
        "key1": "value",
        "key2": "value value value"
            "value",
    }

    ```

    **best practice** :
    ```python:good
    {
        "key1": "value",
        "key2": "value value value"
                "value",
    }

    ```


## `E2` - 空白に関するエラー

  * `E201` : Whitespace after '('
    - 開き括弧の後に空白が入っている

    **anti pattern** :
    ```python:bad
    with open( 'file.dat') as f:
        contents = f.read()

    ```

    **best practice** :
    ```python:good
    with open('file.dat') as f:
        contents = f.read()

    ```


  * `E202` : Whitespace before ')'
    - 閉じ括弧の前に空白が入っている

    **anti pattern** :
    ```python:bad
    with open('file.dat' ) as f:
        contents = f.read()

    ```

    **best practice** :
    ```python:good
    with open('file.dat') as f:
        contents = f.read()

    ```


  * `E203` : Whitespace before ':'
    - コロンの前に空白が入っている

    **anti pattern** :
    ```python:bad
    with open('file.dat') as f :
        contents = f.read()

    ```

    **best practice** :
    ```python:good
    with open('file.dat') as f:
        contents = f.read()

    ```


  * `E211` : Whitespace before '('
    - 開き括弧の前に空白が入っている

    **anti pattern** :
    ```python:bad
    with open ('file.dat') as f:
        contents = f.read()

    ```

    **best practice** :
    ```python:good
    with open('file.dat') as f:
        contents = f.read()

    ```

  * `E221` : Multiple spaces before operator
    - 演算子の前に複数の空白が存在する

    **anti pattern** :
    ```python:bad
    x = 10
    y = x  * 2

    ```

    **best practice** :
    ```python:good
    x = 10
    y = x * 2

    ```

  * `E222` : Multiple spaces before operator
    - 演算子の後に複数の空白が存在する

    **anti pattern** :
    ```python:bad
    x = 10
    y = x *  2

    ```

    **best practice** :
    ```python:good
    x = 10
    y = x * 2

    ```


  * `E223` : tab before operator
    - 演算子の前にタブ文字が存在する

    **anti pattern** :
    ```python:bad
    x = 10
    y = x	* 2

    ```

    **best practice** :
    ```python:good
    x = 10
    y = x * 2

    ```


  * `E224` : tab after operator
    - 演算子の後にタブ文字が存在する

    **anti pattern** :
    ```python:bad
    x = 10
    y = x *	2

    ```

    **best practice** :
    ```python:good
    x = 10
    y = x * 2

    ```


  * `E225` : Missing whitespace around operator
    - 演算子の前後に空白が存在しない

    **anti pattern** :
    ```python:bad
    if age>15:
    print('Can drive')

    ```

    **best practice** :
    ```python:good
    if age > 15:
    print('Can drive')

    ```

  * `E226` <sup><a href="#ignore">\*</a></sup> : Missing whitespace around arithmetic operator
    - 算術演算子(`+`, `-`, `/`, `*`)の前後に空白が存在しない

    **anti pattern** :
    ```python:bad
    age = 10+15

    ```

    **best practice** :
    ```python:good
    age = 10 + 15

    ```


  * `E227` : Missing whitespace around bitwise or shift operator
    - ビット演算子またはシフト演算子(`<<`, `>>`, `&`, `|`, `^`)の前後に空白が存在しない

    **anti pattern** :
    ```python:bad
    remainder = 10%2

    ```

    **best practice** :
    ```python:good
    remainder = 10 % 2

    ```


  * `E228` : Missing whitespace around modulo operator
    - 剰余演算子 (`%`) の前後に空白が存在しない

    **anti pattern** :
    ```python:bad
    age = 10+15

    ```

    **best practice** :
    ```python:good
    age = 10 + 15

    ```


  * `E231` : Missing whitespace after ',', ';', or ':'
    - `,`, `;`, `:`の前後に空白が存在しない

    **anti pattern** :
    ```python:bad
    my_tuple = 1,2,3

    ```

    **best practice** :
    ```python:good
    my_tuple = 1, 2, 3

    ```


  * `E241` <sup><a href="#ignore">\*</a></sup> : Multiple spaces after ‘,’
    - `,`の後に複数の空白が存在する

    **anti pattern** :
    ```python:bad
    my_tuple = 1,  2

    ```

    **best practice** :
    ```python:good
    my_tuple = 1, 2

    ```

  * `E242` <sup><a href="#ignore">\*</a></sup> : Tab after ','
    - `,`の後にタブ文字が存在する

    **anti pattern** :
    ```python:bad
    my_tuple = 1,	2,	3

    ```

    **best practice** :
    ```python:good
    my_tuple = 1, 2, 3

    ```


  * `E251` : Unexpected spaces around keyword / parameter equals
    - 関数定義時の `=` 前後に空白が存在する

    **anti pattern** :
    ```python:bad
    def func(key1 = 'val1',
         key2 = 'val2'):
         return key1, key2

    ```

    **best practice** :
    ```python:good
    def func(key1='val1',
         key2='val2'):
         return key1, key2

    ```


  * `E261` : At least two spaces before inline comment
    - インラインコメントの前には少なくとも2つのスペースが必要である

    **anti pattern** :
    ```python:bad
    def print_name(self):
        print(self.name) # This comment needs an extra space

    ```

    **best practice** :
    ```python:good
    def print_name(self):
        print(self.name)  # Comment is correct now

    ```


  * `E262` : Inline comment should start with '# '
    - インラインコメントは `# ` で始める必要がある

    **anti pattern** :
    ```python:bad
    def print_name(self):
        print(self.name)  #This comment needs a space

    ```

    **best practice** :
    ```python:good
    def print_name(self):
        print(self.name)  # Comment is correct now

    ```


  * `E265` : Block comment should start with '# '
    - ブロックコメントは `# ` で始める必要がある

    **anti pattern** :
    ```python:bad
    #This comment needs a space
    def print_name(self):
        print(self.name)

    ```

    **best practice** :
    ```python:good
    # Comment is correct now
    def print_name(self):
        print(self.name)

    ```


  * `E266` : Too many leading '#' for block comment
    - ブロックコメントを開始する `#` が多すぎる

    **anti pattern** :
    ```python:bad
    ## Prints hello
    print('hello')

    ```

    **best practice** :
    ```python:good
    # Prints hello
    print('hello')

    ```


  * `E271` : Multiple spaces after keyword
    - キーワードの後に複数の空白が存在する

    **anti pattern** :
    ```python:bad
    def  func():
        pass

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```


  * `E272` : Multiple spaces before keyword
    - キーワードの前に複数の空白が存在する

    **anti pattern** :
    ```python:bad
    def func():
        if 1  in [1, 2, 3]:
            print('yep!')

    ```

    **best practice** :
    ```python:good
    def func():
        if 1 in [1, 2, 3]:
            print('yep!')

    ```


  * `E273` : Tab after keyword
    - キーワードの後にタブ文字が存在する

    **anti pattern** :
    ```python:bad
    def	func():
        pass

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```


  * `E274` : Tab before keyword
    - キーワードの前にタブ文字が存在する

    **anti pattern** :
    ```python:bad
    def func():
        if 1	in [1, 2, 3]:
            print('yep!')

    ```

    **best practice** :
    ```python:good
    def func():
        if 1 in [1, 2, 3]:
            print('yep!')

    ```

  * `E275` : Missing whitespace after keyword
    - キーワードの後に空白が存在しない

    **anti pattern** :
    ```python:bad
    from collections import(namedtuple, defaultdict)

    ```

    **best practice** :
    ```python:good
    from collections import (namedtuple, defaultdict)

    ```


## `E3` - 空行に関するエラー

  * `E301` : Expected 1 blank line, found 0
    - クラスのメソッド間に1行の空白行が必要

    **anti pattern** :
    ```python:bad
    class MyClass(object):
    def func1():
        pass
    def func2():
        pass

    ```

    **best practice** :
    ```python:good
    class MyClass(object):
    def func1():
        pass

    def func2():
        pass

    ```


  * `E302` : Expected 2 blank lines, found 0
    - 関数とクラスの間に2行の空白行が必要

    **anti pattern** :
    ```python:bad
    def func1():
        pass
    def func2():
        pass

    ```

    **best practice** :
    ```python:good
    def func1():
        pass


    def func2():
        pass

    ```


  * `E303` : Too many blank lines (3)
    - 空白行が多すぎる

    **anti pattern** :
    ```python:bad
    def func1():
        pass



    def func2():
        pass

    ```

    **best practice** :
    ```python:good
    def func1():
        pass


    def func2():
        pass

    ```


  * `E304` : Blank lines found after function decorator
    - 関数デコレータの後に空白行が存在する

    **anti pattern** :
    ```python:bad
    class User(object):

        @property

        def name(self):
            pass

    ```

    **best practice** :
    ```python:good
    class User(object):

        @property
        def name(self):
            pass

    ```

    * `E305` : Expected 2 blank lines after end of function or class
      - 関数またはクラスの終了後は2行の空白行が必要

      **anti pattern** :
    ```python:bad
      class User(object):
          pass
      user = User()

    ```

      **best practice** :
    ```python:good
      class User(object):
          pass


      user = User()

    ```


## `E4` - Importに関するエラー

  * `E401` : Multiple imports on one line
    - 1行に複数回のインポートが行われている

    **anti pattern** :
    ```python:bad
    import collections, os, sys

    ```

    **best practice** :
    ```python:good
    import collections
    import os
    import sys

    ```


  * `E402` : Module level import not at top of file
    - モジュールレベルのインポートがファイルの先頭以外で行われている

    **anti pattern** :
    ```python:bad
    import locale

    locale.setlocale(locale.LC_ALL, 'en_US.UTF-8')

    import sys

    ```

    **best practice** :
    ```python:good
    import locale
    import sys

    locale.setlocale(locale.LC_ALL, 'en_US.UTF-8')

    ```


## `E5` - 行の長さに関するエラー

  * `E501` <sup><a href="#noqa">^</a></sup> : Line to long ((length) > 79 characters)
    - 一行の文字数が多すぎる
    - 推奨最大文字数は79文字
    - 100または120文字に変更することは一般的


  * `E502` : The backslash is redundant between brackets
    - 括弧の中に冗長なバックスラッシュが存在している

    **anti pattern** :
    ```python:bad
    print('Four score and seven years ago our fathers brought '\
          'forth, upon this continent, a new nation, conceived '\
          'in liberty, and dedicated to the proposition that '\
          '"all men are created equal."')

    ```

    **best practice** :
    ```python:good
    print('Four score and seven years ago our fathers brought '
          'forth, upon this continent, a new nation, conceived '
          'in liberty, and dedicated to the proposition that '
          '"all men are created equal."')

    ```


## `E7` ステートメントに関するエラー

  * `E701` : Multiple statements on one line (colon)
    - 一行に複数のステートメントが存在する( `:` )

    **anti pattern** :
    ```python:bad
    if x > 5: y = 10

    ```

    **best practice** :
    ```python:good
    if x > 5:
        y = 10

    ```

  * `E702` : Multiple statements on one line (semicolon)
    - 一行に複数のステートメントが存在する( `;` )

    **anti pattern** :
    ```python:bad
    from gevent import monkey; monkey.patch_all()

    ```

    **best practice** :
    ```python:good
    from gevent import monkey
    monkey.patch_all()

    ```


  * `E703` : Statement ends with a semicolon
    - ステートメントがセミコロンで終了している

    **anti pattern** :
    ```python:bad
    print('Hello world!');

    ```

    **best practice** :
    ```python:good
    print('Hello world!')

    ```


  * `E704` <sup><a href="#ignore">\*</a></sup> : Multiple statements on one line (def)
    - 関数定義の複数ステートメントが一行で行われている

    **anti pattern** :
    ```python:bad
    def f(): pass

    ```

    **best practice** :
    ```python:good
    def f():
        pass

    ```


  * `E711` <sup><a href="#noqa">^</a></sup> : Comparison to none should be 'if cond is none:'
    - True, False, Noneといったシングルトンオブジェクトを同一性ではなく等価性で比較している

    **anti pattern** :
    ```python:bad
    if var != True:
        print("var is not equal to True")
    if var == None:
        print("var is equal to None")

    ```

    **best practice** :
    ```python:good
    if var is not True
        print("var is not True")
    if var is None
        print("var is None")

    ```

  * `E712` <sup><a href="#noqa">^</a></sup> : Comparison to true should be 'if cond is true:' or 'if cond:'
    - `True` との比較を等価演算子を用いて行っている

    **anti pattern** :
    ```python:bad
    x = True
    if x == True:
        print('True!')

    ```

    **best practice** :
    ```python:good
    x = True
    if x is True:
        print('True!')

    # or simply:
    if x:
        print('True!')

    ```


  * `E713` : Test for membership should be 'not in'
    - 要素の検証に `in` の結果の否定が使われている

    **anti pattern** :
    ```python:bad
    my_list = [1, 2, 3]
    if not num in my_list:
        print(num)

    ```

    **best practice** :
    ```python:good
    my_list = [1, 2, 3]
    if num not in my_list:
        print(num)

    ```


  * `E714` : Test for object identity should be 'is not'
    - オブジェクトの同一性の検証に `is` の結果の否定が使われている

    **anti pattern** :
    ```python:bad
    if not user is None:
        print(user.name)

    ```

    **best practice** :
    ```python:good
    if user is not None:
        print(user.name)

    ```


  * `E721` <sup><a href="#noqa">^</a></sup> : Do not compare types, use 'isinstance()'
    - 型の比較に `isinstance()` を使用していない

    **anti pattern** :
    ```python:bad
    if type(user) == User:
        print(user.name)

    ```

    **best practice** :
    ```python:good
    if isinstance(user, User):
        print(user.name)

    ```

  * `E722` : Do not use bare except, specify exception instead
    - 例外捕捉時に例外クラスを指定していない

    **anti pattern** :
    ```python:bad
    try:
        func()
    except:
        print("error")

    ```

    **best practice** :
    ```python:good
    try:
        func()
    except Exception:
        print("error")

    ```


  * `E731` : Do not assign a lambda expression, use a def
    - ラムダ式を変数に代入している

    **anti pattern** :
    ```python:bad
    root = lambda folder_name: os.path.join(BASE_DIR, folder_name)

    ```

    **best practice** :
    ```python:good
    def root(folder_name):
        return os.path.join(BASE_DIR, folder_name)

    ```


  * `E741` : Do not use variables named 'l', 'O', or 'I'
    - `l`, `O`, `I` といった紛らわしい変数名を使用している

    **anti pattern** :
    ```python:bad
    l = []

    ```

    **best practice** :
    ```python:good
    list_name = []

    ```


  * `E742` : Do not define classes named 'l', 'O', or 'I'
    - `l`, `O`, `I` といった紛らわしいクラス名を使用している

    **anti pattern** :
    ```python:bad
    class I:

        def func():
            pass

    ```

    **best practice** :
    ```python:good
    class Icon:

        def func():
            pass

    ```


  * `E743` : Do not define functions named 'l', 'O', or 'I'
    - `l`, `O`, `I` といった紛らわしい関数名を使用している

    **anti pattern** :
    ```python:bad
    def O:
      pass

    ```

    **best practice** :
    ```python:good
    def oh:
      pass

    ```


## `E9` - ランタイムエラー

  * `E901` : SyntaxError or IndentationError
    - 構文エラーまたはインデントのエラー


  * `E902` : IOError
    - 入出力エラー


## `W1` - インデントに関する警告

  * `W191` : Indentation contains tabs
    - タブでインデントされている行が存在する

    **anti pattern** :
    ```python:bad
    def func():
    	pass

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```


## `W2` - 空白に関する警告

  * `W291` : Trailing whitespace
    - 行末に空白が存在する

    **anti pattern** :
    ```python:bad
    def func():
        pass  

    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```


  * `W292` : No newline at end of file
    - ファイルの末尾に改行が存在しない

    **anti pattern** :
    ```python:bad
    def func():
        pass
    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```


  * `W293` : Blank line contains whitespace
    - 空白行に空白またはタブが存在する

    **anti pattern** :
    ```python:bad
    def first_func():
        pass
        # This line contains four spaces

    def second_func():
        pass

    ```

    **best practice** :
    ```python:good
    def first_func():
        pass


    def second_func():
        pass

    ```

## `W3` - 空白行に関する警告

  * `W391` : Blank line at end of file
    - ファイルの末尾に複数の空白行が存在する

    **anti pattern** :
    ```python:bad
    def func():
        pass


    ```

    **best practice** :
    ```python:good
    def func():
        pass

    ```


## `W5` - 改行に関する警告

  * `W503` <sup><a href="#ignore">\*</a></sup> : Line break occurred before a binary operator
    - 二項演算子の前に改行が存在する  
      (現在非推奨, `W504` と排他的な関係)

    **anti pattern** :
    ```python:bad
    income = (gross_wages
              + taxable_interest)

    ```

    **best practice** :
    ```python:good
    income = (gross_wages +
              taxable_interest)

    ```


  * `W504` <sup><a href="#ignore">\*</a></sup> : Line break occurred after a binary operator
    - 二項演算子の後に改行が存在する  
      (`W503` と排他的な関係)

    **anti pattern** :
    ```python:bad
    income = (gross_wages +
              taxable_interest)

    ```

    **best practice** :
    ```python:good
    income = (gross_wages
              + taxable_interest)

    ```


  * `W505` <sup><a href="#ignore">\*</a></sup> <sup><a href="#noqa">^</a></sup> : Doc line too long ((length) > 79 characters)
    - コメントまたはdocstringの一行の文字数が多すぎる  
      (79文字が基準だが、flake8では `max-doc-length` の値を与えなければ警告されない)

    **anti pattern** :
    ```python:bad
    def func():
        """
        Nothing Nothing Nothing Nothing Nothing Nothing Nothing Nothing Nothing Nothing
        """

        pass

    ```

    **best practice** :
    ```python:good
    def func():
        """
        Nothing Nothing Nothing Nothing Nothing Nothing Nothing Nothing Nothing
        Nothing
        """

        pass


    ```


## `W6` - 廃止構文に関する警告

  * `W601` : .has_key() is deprecated, use ‘in’
    - `.has_key()` メソッドの使用

    **anti pattern** :
    ```python:bad
    {'key': 'value'}.has_key('key')

    ```

    **best practice** :
    ```python:good
    'key' in {'key': 'value'}

    ```

  * `W602` : Deprecated form of raising exception
    - 非推奨の形式( `raise Exception, message` )で例外を発生させている

    **anti pattern** :
    ```python:bad
    def can_drive(age):
        if age < 16:
            raise ValueError, 'Not old enough to drive'
        return True

    ```

    **best practice** :
    ```python:good
    def can_drive(age):
        if age < 16:
            raise ValueError('Not old enough to drive')
        return True

    ```


  * `W603` : '<>' is deprecated, use '!='
    - 非等価の比較に `<>` を用いている

    **anti pattern** :
    ```python:bad
    assert 'test' <> 'testing'

    ```

    **best practice** :
    ```python:good
    assert 'test' != 'testing'

    ```


  * `W604` : Backticks are deprecated, use 'repr()'
    - Python3で廃止されたバッククォートによるオブジェクトの文字列化を試みている

    **anti pattern** :
    ```python:bad
    obj = MyObj()
    print(`obj`)

    ```

    **best practice** :
    ```python:good
    obj = MyObj()
    print(repr(obj))

    ```


  * `W605` : invalid escape sequence 'x'
    - 無効なエスケープシーケンスを用いている  
      (バックスラッシュと値の組み合わせは全てエスケープシーケンスとみなされる)

    **anti pattern** :
    ```python:bad
    regex = '\.png$'

    ```

    **best practice** :
    ```python:good
    regex = r'\.png$'

    ```


  * `W606` : ‘async’ and ‘await’ are reserved keywords starting with Python 3.7
    - Python 3.7以降の予約語である `async` と `await` を用いている

    **anti pattern** :
    ```python:bad
    def async():
        pass

    ```

    **best practice** :
    ```python:good
    def my_async():
        pass

    ```


## 注釈

 * <span id="continuous_line" style="font-size:x-small">継続行: 一行で表現可能なコード(辞書型のリテラルやメソッドの引数など)を複数行にしたもの</span>

 * <span id="ignore" style="font-size:x-small">\*: 賛否あるルールのため、 `ignore` を使用していない場合はデフォルトで無視される</span>

 * <span id="noqa" style="font-size:x-small">^: `# noqa` コメントにより一時的にルールを無効化可能
