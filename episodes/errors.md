---
title: Errors (and other sandbox items)
タイトル: エラー (およびその他のサンドボックス項目)
teaching: 15
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives


- Correctly describe situations in which SyntaxError and NameError occur.
- SyntaxErrorとNameErrorが発生する状況を正しく説明してください。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions


- What kind of errors can occur in programs?
- プログラムではどのようなエラーが発生する可能性がありますか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Python reports a syntax error when Python's grammar rules have been violated.
## Pythonは、Pythonの文法規則に違反した場合、構文エラーを報告します。

You've already seen errors when you try to use a function incorrectly, but you can also have errors when you use punctuation incorrectly. Python will run a program up until a point where it encounters an error, and when the grammar of a line of code has produced an error, the program will shut down and output the error.

関数を誤って使用しようとすると、すでにエラーが見られますが、句読点を誤って使用するとエラーが発生する可能性があります。Pythonは、エラーに遭遇するまでプログラムを実行し、コード行の文法がエラーを生成した場合、プログラムはシャットダウンしてエラーを出力します。

```python
# Forgot to close the quotation marks around the string.
name = 'Feng
```

```error
SyntaxError: EOL while scanning string literal
```

```python
# An extra '=' in the assignment.
age = = 52
```

```error
SyntaxError: invalid syntax
```

Let's breakdown each line of this error message:

このエラーメッセージの各行を分解しましょう。

```python
print("hello world"
```

```error
  File "<ipython-input-6-d1cc229bf815>", line 1
    print ("hello world"
                        ^
SyntaxError: unexpected EOF while parsing
```

- At the end of the first line of this error message it notes there is a problem on first line of the input ("line 1").
- The "ipython-input" section of the file name tells us that we are working with input into IPython and the `-6-` part of the filename indicates that the error occurred in cell 6 of our Notebook.
- Next is the problematic line of code - `print ("hello world"` -  indicating where the problem is found with a `^` pointer.
- Finally we get the SyntaxError message, which tells us that Python expected an 'EOF' or end of file. It's often helpful to look at the end of the Error message first. Our SyntaxError, in this case, indicates that Python ran through all of the code but expected to find more information. In this case it expected to encounter a closing parenthesis in the `print("hello world")` function. 

- このエラーメッセージの最初の行の最後に、入力の最初の行（「1行目」）に問題があることに注意してください。

- ファイル名の「ipython-input」セクションは、IPythonへの入力で作業していることを示し、ファイル名の「-6-」部分は、ノートブックのセル6でエラーが発生したことを示しています。

- 次は問題のあるコード行です - `print ("hello world"` - `^`ポインタで問題が見つかった場所を示します。

- 最後に、Pythonが「EOF」またはファイルの終了を期待していたことを知らせるSyntaxErrorメッセージが表示されます。多くの場合、最初にエラーメッセージの最後を見ると便利です。この場合、私たちのSyntaxErrorは、Pythonがすべてのコードを実行したが、より多くの情報を見つけることを期待していたことを示しています。この場合、`print("hello world")`関数に閉じ括弧が発生すると予想されます。

## Python reports a runtime error when something goes wrong while a program is executing.

## Pythonは、プログラムの実行中に何か問題が発生した場合、ランタイムエラーを報告します。

```python
age = 53
remaining = 100 - aege # mis-spelled 'age'
```

```error
NameError: name 'aege' is not defined
```

You can fix syntax errors by reading the source and runtime errors by tracing execution.

実行をトレースすることで、ソースエラーとランタイムエラーを読み取ることで、構文エラーを修正できます。



:::::::::::::::::::::::::::::::::::::::  challenge

## What Happens When
## 何が起こるか

1. Explain in simple terms the order of operations in the following program:
  when does the addition happen, when does the subtraction happen,
  when is each function called, etc.
2. What is the final value of `word`?

1. 次のプログラムの操作の順序を簡単な言葉で説明してください。

足し算はいつ起こるのか、引き算はいつ起こるのか、

各関数がいつ呼び出されるかなど。

2. 「単語」の最終的な値は何ですか?

```python
word = 'blah '
word = max(min(word * 2 + 'blur ', 'aaah '), 'ping')
print(word)
```

:::::::::::::::  solution

## Solution
## 解決策

```
ping
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Spot the Difference
## 違いを見つける

1. Predict what each of the `print` statements in the program below will print.
2. Does `max(len(rich), poor)` run or produce an error message?
  If it runs, does its result make any sense?
1. 以下のプログラムの「印刷」ステートメントのそれぞれが何を印刷するかを予測します。

2. `max(len(rich), poor)`はエラーメッセージを実行または生成しますか?

それが実行された場合、その結果は理にかなっていますか?

```python
rich = "gold"
poor = "tin"
print(max(rich, poor))
print(max(len(rich), len(poor)))
```

:::::::::::::::  solution

## Solution
## 解決策

```
tin
4
TypeError: '>' not supported between instances of 'str' and 'int'
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Why Not?
## なぜですか?

Why don't `max` and `min` return `None` when they are given no arguments?

引数が与えられていないのに、なぜ「max」と「min」は「None」を返さないのですか?

:::::::::::::::  solution

## Solution
## 解決策

Both functions require an argument to execute

どちらの関数も実行するために引数が必要です

```python
print(max())
```

```error
TypeError: max expected 1 arguments, got 0
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Last Character of a String
## 文字列の最後の文字

If Python starts counting from zero,
and `len` returns the number of characters in a string,
what index expression will get the last character in the string `name`?
(Note: we will see a simpler way to do this in a later episode.)

Pythonがゼロから数え始めると、

そして、`len`は文字列内の文字数を返します。

文字列「name」の最後の文字を取得するインデックス式は何ですか?

（注：後のエピソードでこれを行うためのより簡単な方法が表示されます。）

:::::::::::::::  solution

## Solution
## 解決策

`name[len(name) - 1]`



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Python reports a syntax error when it can't understand the source of a program.
- Python reports a runtime error when something goes wrong while a program is executing.
- Fix syntax errors by reading the source code, and runtime errors by tracing the program's execution.
- Pythonは、プログラムのソースを理解できないときに構文エラーを報告します。

- Pythonは、プログラムの実行中に何か問題が発生すると、ランタイムエラーを報告します。

- ソースコードを読んで構文エラーを修正し、プログラムの実行をトレースしてランタイムエラーを修正します。

::::::::::::::::::::::::::::::::::::::::::::::::::


