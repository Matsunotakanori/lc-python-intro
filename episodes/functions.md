---
title: Built-in Functions and Help
タイトル: 4. 組み込み機能とヘルプ
teaching: 15
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explain the purpose of functions.
- Correctly call built-in Python functions.
- Correctly nest calls to built-in functions.
- Use help to display documentation for built-in functions.
- Correctly describe situations in which SyntaxError and NameError occur.
- 機能の目的を説明する。
- 組み込みのPython関数を正しく呼び出します。
- 組み込み関数への呼び出しを正しくネストします。
- ヘルプを使用して、組み込み機能のドキュメントを表示します。
- SyntaxErrorとNameErrorが発生する状況を正しく説明してください。
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I use built-in functions?
- How can I find out what they do?
- What kind of errors can occur in programs?
- 組み込み機能を使用するにはどうすればよいですか?
- どうすれば彼らが何をしているのかを知ることができますか?
- プログラムではどのようなエラーが発生する可能性がありますか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Use comments to add documentation to programs.
## コメントを使用して、プログラムにドキュメントを追加します。

It's helpful to add comments to our code so that our collaborators (and our future selves) will be able to understand what particular pieces of code are meant to accomplish or how they work

協力者（および将来の自分自身）が、特定のコードが何を達成するのか、どのように機能するのかを理解できるように、コードにコメントを追加すると便利です。

```python
# This sentence isn't executed by Python.
name = 'Library Carpentry'   # Neither is this comment
# Anything after '#' is ignored.
```

## A function may take zero or more arguments.
## 関数は0以上の引数を取ることができます。

We have seen some functions such as `print()` and `len()` already but let's take a closer look at their structure. 

`print()`や`len()`などの関数はすでに見てきましたが、その構造を詳しく見てみましょう。

An *argument* is a value passed into a function. Any arguments you want to pass into a function must go into the `()`.

*引数*は、関数に渡される値です。関数に渡す引数は、`()`に入る必要があります。

```python
print("I am an argument and must go here.")
print()
print("Sometimes you don't need to pass an argument.")
```

```output
I am an argument and must go here.

私は議論であり、ここに行かなければなりません。

Sometimes you don't need to pass an argument.

時々、あなたは議論を渡す必要はありません。

```
You always need to use parentheses at the end of a function, because this tells Python you are calling a function. Leave the parentheses empty if you don't want or need to pass any arguments.

関数の最後に括弧を使用する必要があります。これは、関数を呼び出していることをPythonに伝えるからです。引数を渡したくない、または渡す必要がない場合は、括弧を空のままにしてください。

## Commonly-used built-in functions include `max()` and `min()`.

## 一般的に使用される組み込み関数には、`max()`と`min()`が含まれます。

- Use `max()` to find the largest value of one or more values.
- Use `min()` to find the smallest.
- `max()`を使用して、1つ以上の値の最大値を見つけます。
- `min()` を使用して最小を見つけます。

Both `max()` and `min()` work on character strings as well as numbers, so can be used for numerical and alphabetical comparisons. Note that numerical and alphabetical comparisons follow some specific rules about what is larger or smaller: numbers are smaller than letters and upper case letters are smaller than lower case letters, so the order of operations in Python is 0-9, A-Z, a-z when comparing numbers and letters.

`max()` と `min()` はどちらも文字列と数字で動作するため、数値とアルファベットの比較に使用できます。数値とアルファベットの比較は、大きいか小さいかに関するいくつかの特定の規則に従うことに注意してください。数字は文字よりも小さく、大文字は小文字よりも小さいので、数字と文字を比較するときのPythonの操作順序は0-9、A-Z、a-zです。

```python
print(max(1, 2, 3)) # notice that functions are nestable
print(min('a', 'b', max('c', 'd'))) # nest with care since code gets less readable
print(min('a', 'A', '2')) # numbers and letters can be compared if they are the same data type
```

```output
3
a
2
```

## Functions may only work for certain (combinations of) arguments.

## 関数は、特定の（組み合わせの）引数に対してのみ機能します。


`max()` and `min()` must be given at least one argument and they must be given things that can meaningfully be compared.

`max()`と`min()`は、少なくとも1つの引数を与えられなければならず、有意義に比較できるものを与えられなければならない。

```python
max(1, 'a')
```

```error
TypeError                                 Traceback (most recent call last)
Cell In[6], line 1
----> 1 max(1, 'a')

TypeError: '>' not supported between instances of 'str' and 'int'
```

## Function argument default values, and `round()`.
## 関数引数のデフォルト値、および `round()`。

`round()` will round off a floating-point number. By default, it will round to zero decimal places, which is how it will operate if you don't pass a second argument.

`round()`は浮動小数点数を四捨五入します。デフォルトでは、小数点以下0桁に丸められます。これは、2番目の引数を渡さない場合の動作方法です。

```python
round(3.712)
```

```output
4
```

We can use a second argument (or parameter) to specify the number of decimal places we want though.

ただし、2番目の引数（またはパラメータ）を使用して、必要な小数点以下を指定できます。

```python
round(3.712, 1)
```

```output
3.7
```

## Use the built-in function `help` to get help for a function.
## 組み込み関数 `help` を使用して、関数のヘルプを取得します。

Every built-in function has online documentation. You can always access the documentation using the built-in `help()` function. In the jupyter environment, you can access help by either adding a `?` at the end of your function and running it or Hold down <kbd>Shift</kbd>, and press <kbd>Tab</kbd> when your insertion cursor is in or near the function name.

すべての組み込み機能にはオンラインドキュメントがあります。組み込みの`help()`関数を使用して、いつでもドキュメントにアクセスできます。Jupyter環境では、`を追加することでヘルプにアクセスできます。関数の最後に実行するか、<kbd>Shift</kbd>を押したまま、挿入カーソルが関数名またはその近くにあるときに<kbd>Tab</kbd>を押します。

```python
help(round)
```

```python
round?
```

```output
Help on built-in function round in module builtins:
モジュールビルトインの組み込み機能ラウンドに関するヘルプ:

round(...)
    round(number[, ndigits]) -> number

    Round a number to a given precision in decimal digits (default 0 digits).
    This returns an int when called with one argument, otherwise the
    same type as the number. ndigits may be negative.

数字を所定の精度に10進数で丸めます(デフォルトは0桁)。

これは、1つの引数で呼び出されたときにintを返します。そうでなければ、

数字と同じタイプです。ndigitsは負の場合があります。


```

## Every function returns something.
## すべての関数は何かを返します。

Every function call produces some result and if the function doesn't have a useful result to return, it usually returns the special value `None`. Each line of Python code is executed in order. In this case, the second line call to `{result}` returns 'None' since the `print` statement in the previous line didn't return a value to the `result` variable.

すべての関数呼び出しは何らかの結果を生成し、関数が返す有用な結果がない場合は、通常、特別な値「None」を返します。Pythonコードの各行は順番に実行されます。この場合、前の行の `print` ステートメントが `result` 変数に値を返さなかったため、`{result}` への 2 行目の呼び出しは 'None' を返します。

```python
result = print('example')
print(f'result of print is {result}')
```

```output
example
result of print is None
```


:::::::::::::::::::::::::::::::::::::::  challenge

## Spot the Difference
## 違いを見つける

1. Predict what each of the `print` statements in the program below will print.
2. Does `max(len(cataloger), assistant_librarian)` run or produce an error message?
  If it runs, does its result make any sense?

1. 以下のプログラムの「印刷」ステートメントのそれぞれが何を印刷するかを予測します。
2. `max(len(cataloger), assistant_librarian)`はエラーメッセージを実行または生成しますか?

それが実行された場合、その結果は理にかなっていますか?

```python
cataloger = "metadata_curation"
assistant_librarian = "archives"
print(max(cataloger, assistant_librarian))
print(max(len(cataloger), assistant_librarian))
```

:::::::::::::::  solution

## Solution
## 解決策

```output
metadata_curation
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
Cell In[2], line 4
      2 assistant_librarian = "archives"
      3 print(max(cataloger, assistant_librarian))
----> 4 print(max(len(cataloger), assistant_librarian))

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



:::::::::::::::::::::::::::::::::::::::: keypoints

- Use comments to add documentation to programs.
- A function may take zero or more arguments.
- Commonly-used built-in functions include `max`, `min`, and `round`.
- Functions may only work for certain (combinations of) arguments.
- Functions may have default values for some arguments.
- Use the built-in function `help` to get help for a function.
- Every function returns something.
- コメントを使用して、プログラムにドキュメントを追加します。

- 関数は0以上の引数を取ることができます。

- 一般的に使用される組み込み関数には、`max`、`min`、`round`が含まれます。

- 関数は、特定の（組み合わせの）引数に対してのみ機能します。

- 関数には、一部の引数にデフォルト値がある場合があります。

- 組み込みの関数「help」を使用して、関数のヘルプを取得します。

- すべての関数は何かを返します。

::::::::::::::::::::::::::::::::::::::::::::::::::


