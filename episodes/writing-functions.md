---
title: Writing Functions
タイトル: 関数を書く
teaching: 10
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explain and identify the difference between function definition and function call.
- Write a function that takes a small, fixed number of arguments and produces a single result.
- Identify local and global variables.
- 関数定義と関数呼び出しの違いを説明し、特定する。

- 少数の固定数の引数を取り、単一の結果を生成する関数を書く。

- ローカル変数とグローバル変数を特定します。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I create my own functions?
- How do variables inside and outside of functions work?
- How can I make my functions easier to understand?
- 独自の関数を作成するにはどうすればよいですか?

- 関数の内外の変数はどのように機能しますか?

- 機能を理解しやすくするにはどうすればよいですか?
- 
::::::::::::::::::::::::::::::::::::::::::::::::::

## Use functions to make your code easier to understand.

Human beings can only keep a few items in working memory at a time. But we can work with larger and more complicated ideas by breaking content down into pieces. Functions serve a similar purpose in Python. We can create our own functions to *encapsulate* complexity and treat specific actions or ideas as a single "thing". Functions also enable us to *re-use* code so we can write code one time, but use it many times.

## 関数を使用して、コードを理解しやすくします。

人間は一度にワーキングメモリにいくつかのアイテムしか保持できません。しかし、コンテンツをバラバラに分解することで、より大きく、より複雑なアイデアに取り組むことができます。関数はPythonでも同様の目的を果たします。複雑さを*カプセル化*し、特定のアクションやアイデアを単一の「もの」として扱う独自の機能を作成できます。関数はまた、コードを*再利用*することを可能にするので、一度だけコードを書くことができますが、何度も使用できます。

## Define a function using `def` with a name, parameters, and a block of code.

Begin each definition of a new function with the keyword `def` (for "define"), followed by the name of the function. Function names follow the same rules as variable names. Next, add your *parameters* in parentheses. You should still use empty parentheses if the function doesn't take any inputs. Finally, like in conditionals and loops, you'll add a colon and an indented block of code that will contain the body of your function.

## 名前、パラメータ、およびコードブロックを含む `def` を使用して関数を定義します。

キーワード `def` (「define」) で新しい関数の各定義を開始し、その後に関数の名前が続きます。関数名は変数名と同じルールに従います。次に、括弧内に*パラメータ*を追加します。関数が入力を取らない場合は、空の括弧を使用する必要があります。最後に、条件やループのように、コロンと関数の本文を含むインデントされたコードブロックを追加します。

```python
def print_greeting():
    print('Hello!')
```


## Defining a function does not run it.

Note that we don't have any output when we run code to define a function. This is similar to assigning a value to a variable. The function definition is sort of like a recipe in a cookbook - the recipe doesn't create a meal until we use it. So we need to "call" a function to execute the code it contains. This means that Python won't show you errors in your function until you call it.  So when a definition of a function runs without error it doesn't mean that there won't be errors when it executes later.

## 関数を定義しても実行されません。

関数を定義するためにコードを実行すると、出力がないことに注意してください。これは、変数に値を割り当てるのと似ています。機能定義は、料理本のレシピのようなものです - レシピは私たちがそれを使用するまで食事を作成しません。そのため、含まれているコードを実行するために関数を「呼び出す」必要があります。これは、Pythonが呼び出すまで関数にエラーを表示しないことを意味します。したがって、関数の定義がエラーなしで実行される場合、後で実行されたときにエラーがないという意味ではありません。


```python
print_greeting()
```

```output
Hello!
```

## Arguments in call are matched to parameters in definition.

Functions are highly useful when they use parameters to pull in data. You can specify *parameters* when you define a function which become variables when the function is executed.

## 呼び出し中の引数は、定義のパラメータと一致します。

関数は、パラメータを使用してデータを取り込むときに非常に便利です。関数の実行時に変数になる関数を定義するときに、*パラメータ*を指定できます。

```python
def print_date(year, month, day):
    joined = f'{year}/{month}/{day}'
    print(joined)

print_date(1871, 3, 19)
```

```output
1871/3/19
```

To expand on the recipe metaphor above, the arguments you add to the `()` contain the ingredients for the function, while the body contains the recipe.

上記のレシピの比喩を拡張するために、`()`に追加する引数には関数の成分が含まれ、本文にはレシピが含まれています。

Functions with defined parameters will result in an error if they are called without passing an argument:
定義されたパラメータを持つ関数は、引数を渡さずに呼び出された場合、エラーになります。

```python
print_date()
```

```error
TypeError                                 Traceback (most recent call last)
Cell In[15], line 1
----> 1 print_date()

TypeError: print_date() missing 3 required positional arguments: 'year', 'month', and 'day'
```

## Use `return` to pass values back from a function.

In the date example above, we printed the results of the function code to output, but there are better way to handle data and objects created within a function. We can use the keyword `return ...` to send a value back to the "global" environment. (We'll learn about local and global variables below). A return command can occur anywhere in the function, but is often placed at the very end of a function with the final result. 

## `return`を使用して、関数から値を返します。

上記の日付の例では、関数コードの結果を出力しましたが、関数内で作成されたデータとオブジェクトを処理するより良い方法があります。キーワード「return ...」を使用して、値を「グローバル」環境に送り返すことができます。(以下でローカル変数とグローバル変数について学びます)。戻りコマンドは、関数のどこにでも発生する可能性がありますが、多くの場合、最終結果を持つ関数の最後に配置されます。

```python
def calc_fine(days_overdue):
    if days_overdue <= 10:
        fine =  days_overdue * 0.25
    else:
        fine = (days_overdue * 0.25) + (days_overdue * .50)
    return fine
    
fine = calc_fine(12)
f'Fine owed: ${fine}'
```

```output
'Fine owed: $9.0'
```

:::::::::::::::::::::::::::::::::::::::::  callout
### Specify the number of float decimals to display
In the example above, the fine value is displayed as `9.0`, though ideally it would print as `$9.00`. We can use the `f-string format specifier` of `.2f` to display two decimal points: `{fine:.2f}`. If you wanted to display a float with three decimal points you would change the format specifier to `{fine:.3f}`. Here's a [cheat sheet of other f-string number formats](https://fstring.help/cheat/).

### 表示する小数点以下の小数点の数を指定する

上記の例では、細かい値は「9.0」と表示されますが、理想的には「$9.00」として印刷されます。`.2f`の`f文字列フォーマット指定子`を使用して、2つの小数点を表示できます: `{fine:.2f}`。小数点以下3点の浮動小数点数を表示したい場合は、フォーマット指定子を`{fine:.3f}`に変更します。これは[他のf文字列番号形式のチートシート](https://fstring.help/cheat/)です。

```python
fine = calc_fine(12)
f'Fine owed: ${fine:.2f}'
```
```output
'Fine owed: $9.00'
```

::::::::::::::::::::::::::::::::::::::::::::::::::

A function that doesn't explicitly `return` a value will automatically return `None`.

値を明示的に「返」しない関数は、自動的に「None」を返します。

```python
result = print_date(1970, 6, 21)
print(f'result of call is: {result}')
```

```output
1970/6/21
result of call is: None
```

## Variable scope

When we define a variable inside of a function in Python, it's known as a `local` variable, which means that it's not visible to -- or known by -- the rest of the program. Variables that we define outside of functions are `global` and are therefore visible throughout the program, *including* from within other functions. The part of a program in which a variable is visible is called its *scope*.

## 可変スコープ

Pythonで関数内で変数を定義すると、それは「ローカル」変数として知られています。つまり、プログラムの残りの部分には表示されない、または知られています。関数の外部で定義する変数は「グローバル」であるため、他の関数内から*含む*プログラム全体に表示されます。変数が表示されているプログラムの部分は、その*スコープ*と呼ばれます。

This is helpful for people using or writing functions, because they don't need to worry about repeating variable names that have been created elsewhere in the program. 

これは、プログラムの他の場所で作成された変数名を繰り返すことを心配する必要がないため、関数を使用したり書いたりする人に役立ちます。

```python
initial_fine = 0.25
late_fine = 0.50

def calc_fine(days_overdue):
    if days_overdue <= 10:
        days_overdue =  days_overdue * initial_fine
    else:
        days_overdue = (days_overdue * initial_fine) + (days_overdue * late_fine)
    return days_overdue
    
```

- `initial_fine` and `late_fine` are *global variables*.
- `days_overdue` is a *local variable* in `calc_fine`. Note that a function parameter is a variable that is automatically assigned a value when the function is called and so acts as a local variable.
- `initial_fine` と `late_fine` は *グローバル変数* です。

- `days_overdue` は `calc_fine` の *ローカル変数* です。関数パラメータは、関数が呼び出されたときに自動的に値が割り当てられ、ローカル変数として機能する変数であることに注意してください。

```python
fine = calc_fine(12)
print(f'Fine owed: ${fine:.2f}')
print(f'Fine rates: ${initial_fine:.2f}, ${late_fine:.2f}')
print(f'Days overdue: {days_overdue}')
```

```output
Fine owed: $9.00
Fine rates: $0.25, $0.50
```

```error
NameError                                 Traceback (most recent call last)
Cell In[22], line 4
      2 print(f'Fine owed: ${fine:.2f}')
      3 print(f'Fine rates: ${initial_fine:.2f}, ${late_fine:.2f}')
----> 4 print(f'Days overdue: {days_overdue}')

NameError: name 'days_overdue' is not defined
```

## Use docstrings to provide online help.

If the first thing in a function is a string that isn’t assigned to a variable, that string is attached to the function as its documentation. This kind of documentation at the beginning of a function is called a `docstring`. 

## docstringsを使用してオンラインヘルプを提供します。

関数の最初のものが変数に割り当てられていない文字列である場合、その文字列はドキュメントとして関数にアタッチされます。関数の先頭にあるこの種のドキュメントは、「docstring」と呼ばれます。

```python
def fahr_to_celsius(temp):
    "Input a fahrenheit temperature and return the value in celsius"
    return ((temp - 32) * (5/9))
```

This is helpful because we can now ask Python’s built-in help system to show us the documentation for the function:

これは、Pythonの組み込みヘルプシステムに関数のドキュメントを示すように依頼できるため、便利です。

```python
help(fahr_to_celsius)
```

```output
Help on function fahr_to_celsius in module __main__:

fahr_to_celsius(temp)
    Input a fahrenheit temperature and return the value in celsius
```

We don’t need to use triple quotes when we write a docstring, but if we do, we can break the string across multiple lines:

ドキュメント文字列を書くときに三重引用符を使用する必要はありませんが、そうすると、複数の行にわたって文字列を分割できます。

```python
def fahr_to_celsius(temp):
    """Convert fahrenheit values to celsius
    Input a value in fahrenheit
    Output a value in celsius"""
    return ((temp - 32) * (5/9))
```


:::::::::::::::::::::::::::::::::::::::  challenge

## Create a function

Write a function called `addition` that takes two parameters and returns their sum. After defining the function, call it with several arguments and print out the results. 

## 関数を作成する

2つのパラメータを取り、その合計を返す「addition」という関数を書いてください。関数を定義した後、いくつかの引数で呼び出し、結果を出力します。

:::::::::::::::  solution

## Solution
## 解決策

```python
def addition(x, y):
    return x + y

addition(3, 6)
```

```output
9

```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Conditional statements within functions
## 関数内の条件文

Create a function called `grade_converter` that takes a numerical score (0 - 100) as its parameter and returns a letter grade based on the score:

数値スコア（0〜100）をパラメータとして、スコアに基づいて文字グレードを返す「grade_converter」という関数を作成します。

- 90 and above returns 'A'
- 80 to 89 returns 'B'
- 70 to 79 returns 'C'
- 60 to 69 returns 'D'
- Below 60 returns 'F'

After defining the function, test it with a variety of scores to test it out. 
機能を定義した後、さまざまなスコアでテストしてテストします。

:::::::::::::::  solution

## Solution
## 解決策

```python
def grade_converter(score):
    if score > 100 or score < 0:
        return 'Invalid score'
    elif score >= 90:
        return 'A'
    elif score >= 80:
        return 'B'
    elif score >= 70:
        return 'C'
    elif score >= 60:
        return 'D'
    elif score <= 59:
        return 'F'

grade_converter(88)
```

```output
'B'
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::  challenge

## Local and global variables
## ローカル変数とグローバル変数

List all of the global variables and all of the local variables in the following code. 

次のコードで、すべてのグローバル変数とすべてのローカル変数をリストします。

```python
fine_rate = 0.25

def fine(days_overdue):
    if days_overdue <= 10:
        fine =  days_overdue * fine_rate
    else:
        fine = (days_overdue * fine_rate) + (days_overdue * (fine_rate*2))
    return fine
    
total_fine = calc_fine(20)
f'Fine owed: ${total_fine:.2f}'

```

```output
'Fine owed: $15.00'
```
:::::::::::::::  solution

## Solution
## 解決策

Global variables:

グローバル変数:

- fine_rate
- total_fine

Local variables:

- days_overdue
- fine

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## CSVs to Pandas function
In the [Looping Data Sets episode](looping-data-sets.html#appending-dataframes-to-a-list), we learned to use glob to loop through a directory of CSV files and convert them to a Pandas DataFrame. 

## CSVからパンダへの機能

[Looping Data Sets episode](looping-data-sets.html#appending-dataframes-to-a-list)では、globを使用してCSVファイルのディレクトリをループし、Pandas DataFrameに変換することを学びました。

Write a function that converts a directory of CSV files into a single Pandas DataFrame. The function should accept one parameter: a string that includes the path and glob wildcard expression to point to a set of CSV files (e.g., `'data/*.csv'`). We can assume, for these purposes, that all of the DataFrames have the same column names so that you can use `pd.concat(dfs, ignore_index=True)` at the end of the function to concatenate a list of DataFrames into a single DataFrame.

CSVファイルのディレクトリを単一のPandas DataFrameに変換する関数を書いてください。関数は1つのパラメータを受け入れる必要があります: CSVファイルのセットを指すパスとグロブワイルドカード式を含む文字列(例えば、`'data/*.csv'`)。これらの目的のために、すべてのDataFrameが同じ列名を持っていると仮定できるため、関数の最後に `pd.concat(dfs, ignore_index=True)` を使用して、DataFrame のリストを単一の DataFrame に連結できます。


:::::::::::::::  solution

## Solution
## 解決策

```python
import glob
import pandas as pd

def concat_csvs(path):
    
    dfs = [] 

    for csv in sorted(glob.glob(path)):
        data = pd.read_csv(csv)
        dfs.append(data)
    
    df = pd.concat(dfs, ignore_index=True)
    return df

df = concat_csvs('data/*.csv')

```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Break programs down into functions to make them easier to understand.
- Define a function using `def` with a name, parameters, and a block of code.
- Defining a function does not run it.
- Arguments in call are matched to parameters in definition.
- Functions may return a result to their caller using `return`.

- プログラムを機能に分解して理解しやすくします。

- 名前、パラメータ、およびコードブロックを含む`def`を使用して関数を定義します。

- 関数を定義しても実行されません。

- 呼び出し中の引数は、定義のパラメータと一致します。

- 関数は、`return`を使用して呼び出し者に結果を返すことができます。

::::::::::::::::::::::::::::::::::::::::::::::::::


