---
title: Variables and Types
teaching: 15
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Write Python to assign values to variables.
- 変数に値を割り当てるためにPythonを書いてください。
- Print outputs to a Jupyter notebook.
- Jupyterノートブックに出力を印刷します。
- Use indexing to manipulate string elements.
- インデックスを使用して文字列要素を操作します。
- View and convert the data types of Python objects.
- Pythonオブジェクトのデータ型を表示および変換します。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I store data in Python?
- Pythonでデータを保存するにはどうすればよいですか?
- What are some types of data that I can work with in Python?
- Pythonで作業できるデータの種類は何ですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Use variables to store values.
## 変数を使用して値を格納します。

Variables are names given to certain values. In Python the `=` symbol assigns a value to a variable. Here, Python assigns the number `42` to the variable `age` and the name `Ahmed` in single quote to a variable `name`.

変数は、特定の値に与えられる名前です。Pythonでは、`=`記号は変数に値を割り当てます。ここで、Pythonは変数`age`に番号`42`を割り当て、変数`name`にシングルクォートで名前`Ahmed`を割り当てます。

```python
age = 42
name = 'Ahmed'
```

:::::::::::::::::::::::::::::::::::::::::  callout
## Naming variables
## 変数の命名

Variable names:

変数名:

  - cannot start with a digit
  - 数字で始めることはできません
  - cannot contain spaces, quotation marks, or other punctuation
  - スペース、引用符、またはその他の句読点を含めることはできません
  - *may* contain an underscore (typically used to separate words in long variable names)
  - *May*にはアンダースコアが含まれています（通常、長い変数名で単語を区切るために使用されます）
  - are case sensitive. `name` and `Name` would be different variables.
  - 大文字と小文字が区別されます。`name`と`Name`は異なる変数になります
  - 
::::::::::::::::::::::::::::::::::::::::::::::::::

## Use `print()` to display values.
## `print()` を使用して値を表示します。

You can print Python objects to the Jupyter notebook output using the built-in function, `print()`. Inside of the parentheses we can add the objects that we want print, which are known as the `print()` function's arguments.  

組み込み関数`print()`を使用して、PythonオブジェクトをJupyterノートブック出力に印刷できます。括弧の内側には、印刷したいオブジェクトを追加できます。これは `print()` 関数の引数と呼ばれます。

```python
print(name, age)
```

```output
Ahmed 42 
```

In Jupyter notebooks, you can leave out the `print()` function for objects -- such as variables -- that are on the last line of a cell. If the final line of Jupyter cell includes the name of a variable, its value will display in the notebook when you run the cell.

Jupyterノートブックでは、セルの最後の行にある変数などのオブジェクトの`print()`関数を省くことができます。Jupyterセルの最後の行に変数の名前が含まれている場合、セルを実行すると、その値がノートブックに表示されます。

```python
name
age
```

```output
42
```

## Format output with f-strings
## f文字列で出力をフォーマットする

F-strings provide a concise and readable way to format strings by embedding Python expressions within them. You can format variables as text strings in your output using an f-string. To do so, start a string with `f` before the open single (or double) quote. Then add any replacement fields, such as variable names, between curly braces `{}`. (Note the f string syntax can only be used with Python 3.6 or higher.)

F文字列は、Python式を埋め込むことで、文字列をフォーマットする簡潔で読みやすい方法を提供します。F文字列を使用して、出力内の変数をテキスト文字列としてフォーマットできます。これを行うには、オープンシングル（またはダブル）クォートの前に「f」で文字列を開始します。次に、中括弧 `{}` の間に変数名などの置換フィールドを追加します。(f文字列構文はPython 3.6以降でのみ使用できることに注意してください。)

```python
f'{name} is {age} years old'
```

```output
'Ahmed is 42 years old'
```

## Variables must be created before they are used.
## 変数は使用する前に作成する必要があります。

If a variable doesn't exist yet, or if the name has been misspelled, Python reports an error called a `NameError`.

変数がまだ存在しない場合、または名前のスペルが間違っている場合、Pythonは「NameError」というエラーを報告します。

```python
print(eye_color)
```

```error
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-1-c1fbb4e96102> in <module>()
----> 1 print(eye_color)

NameError: name 'eye_color' is not defined
```

The last line of an error message is usually the most informative. In this case it tells us that the `eye_color` variable is not defined. NameErrors often refer to variables that haven't been created or assigned yet.

エラーメッセージの最後の行は、通常、最も有益です。この場合、`eye_color`変数が定義されていないことを示しています。NameErrorsは、多くの場合、まだ作成または割り当てられていない変数を指します。

## Variables can be used in calculations.
## 変数は計算に使用できます。

We can use variables in calculations as if they were values. We assigned 42 to `age` a few lines ago, so we can reference that value within a new variable assignment.

変数を値であるかのように計算に使用できます。数行前に42を「age」に割り当てたので、新しい変数の割り当て内でその値を参照できます。

```python
age = age + 3
f'Age equals: {age}'
```

```output
Age equals: 45
```

## Every Python object has a type.
## すべてのPythonオブジェクトには型があります。

Everything in Python is some type of object and every Python object will be of a specific type. Understanding an object's type will help you know what you can and can't do with that object. 

Pythonのすべては何らかのタイプのオブジェクトであり、すべてのPythonオブジェクトは特定のタイプになります。オブジェクトのタイプを理解することは、そのオブジェクトで何ができるか、何ができないかを知るのに役立ちます。

You can use the built-in Python function `type()` to find out an object's type. 

組み込みのPython関数`type()`を使用して、オブジェクトの型を調べることができます。

```python
print(type(140.2), 
      type(age), 
      type(name), 
      type(print))
```

```output
<class 'float'> <class 'int'> <class 'str'> <class 'builtin_function_or_method'>
```

1. 140.2 is an example of a floating point number or `float`. These are fractional numbers. 
1. 140.2は、浮動小数点数または「浮動小数点数」の例です。これらは小数です。
2. The value of the `age` variable is 45, which is a whole number, or integer (`int`).
2.`age`変数の値は45で、これは整数または整数(`int`)です。
3. The `name` variable refers to the string (`str`) of 'Ahmed'.
3. `name`変数は、'Ahmed'の文字列(`str`)を参照します。
4. The built-in Python function `print()` is also an object with a type, in this case it's a `builtin_function_or_method`. Built-in functions refer to those that are included in the core Python library.
4. 組み込みのPython関数`print()`も型を持つオブジェクトであり、この場合は`builtin_function_or_method`です。組み込み関数は、コアPythonライブラリに含まれているものを指します。

## Types control what operations (or methods) can be performed on objects.
## タイプは、オブジェクトに対して実行できる操作（またはメソッド）を制御します。

An object's type determines what the program can do with it.

オブジェクトのタイプは、プログラムがそれで何ができるかを決定します。

```python
5 - 3
```

```output
2
```

We get an error if we try to subtract a letter from a string:

文字列から文字を減算しようとするとエラーが発生します。

```python
'hello' - 'h'
```

```error
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-2-67f5626a1e07> in <module>()
----> 1 'hello' - 'h'

TypeError: unsupported operand type(s) for -: 'str' and 'str'
```

## Use an index to get a single character from a string.
## インデックスを使用して、文字列から1文字を取得します。

We can reference the specific location of a character (individual letters, numbers, and so on) in a string by using its index position. In Python, each character in a string (first, second, etc.) is given a number, which is called an index. Indexes begin from 0 rather than 1. We can use an index in square brackets to refer to the character at that position.

インデックス位置を使用して、文字列内の文字の特定の位置(個々の文字、数字など)を参照できます。Pythonでは、文字列(最初、2番目など)の各文字には、インデックスと呼ばれる数字が与えられます。インデックスは1ではなく0から始まります。角括弧内のインデックスを使用して、その位置の文字を参照できます。

```python
library = 'Alexandria'
library[0]
```

```output
A
```

## Use a slice to get multiple characters from a string.
## スライスを使用して、文字列から複数の文字を取得します。

A slice is a part of a string that we can reference using `[start:stop]`, where `start` is the index of the first character we want and `stop` is the last character. Referencing a string slice does not change the contents of the original string. Instead, the slice returns a copy of the part of the original string we want. 

スライスは、`[start:stop]`を使用して参照できる文字列の一部であり、`start`は最初の文字のインデックスで、`stop`は最後の文字です。文字列スライスを参照しても、元の文字列の内容は変更されません。代わりに、スライスは必要な元の文字列の一部のコピーを返します。

```python
library[0:3]
```

```output
Ale
```

Note that in the example above, `library[0:3]` begins with zero, which refers to the first element in the string, and ends with a 3. When working with slices the end point is interpreted as going up to, *but not including* the index number provided. In other words, the character in the index position of 3 in the string `Alexandria` is `x`, so the slice `[0:3]` will go up to but not include that character, and therefore give us `Ale`.

上記の例では、`library[0:3]`は、文字列の最初の要素を参照するゼロで始まり、3で終わることに注意してください。スライスを操作する場合、エンドポイントは、提供されたインデックス番号まで*ただし、含まれない*と解釈されます。言い換えれば、文字列`Alexandria`の3のインデックス位置の文字は`x`なので、スライス`[0:3]`はその文字まで上がりますが、その文字は含まれません。したがって、`Ale`を与えます。

## Use the built-in function `len` to find the length of a string.
## 組み込み関数 `len` を使用して、文字列の長さを見つけます。

The `len()`function will tell us the length of an item. In the case of a string, it will tell us how many characters are in the string. 

`len()`関数は、アイテムの長さを教えてくれます。文字列の場合、文字列内の文字数がわかります。

```python
len('Babel')
```

```output
5
```

## Variables only change value when something is assigned to them.
## 変数は、何かが割り当てられたときにのみ値を変更します。

Once a Python variable is assigned it will not change value unless the code is run again. The value of `older_age` below does not get updated when we change the value of `age` to `50`, for example:

Python変数が割り当てられると、コードが再度実行されない限り、値は変更されません。たとえば、以下の「older_age」の値は、「age」の値を「50」に変更しても更新されません。

```python
age = 42
older_age = age + 3
age = 50
f'Older age is {older_age} and age is {age}'
```

```output
Older age is 45 and age is 50
```

A variable in Python is analogous to a sticky note with a name written on it: assigning a value to a variable is like putting a sticky note on a particular value. When we assigned the variable `older_age`, it was like we put a sticky note with the name `older_age` on the value of `45`. Remember, `45` was the result of `age + 3` because `age` at that point in the code was equal to `42`. The `older_age` sticky note (variable) was never attached to (assigned to) another value, so it doesn't change when the `age` variable is updated to be `50`.

Pythonの変数は、名前が書かれた付箋に似ています。変数に値を割り当てることは、特定の値に付箋を置くようなものです。変数「older_age」を割り当てたとき、「45」の値に「older_age」という名前の付箋を貼ったようなものでした。コードのその時点での「年齢」が「42」に等しかったので、「45」は「年齢+ 3」の結果だったことを覚えておいてください。`older_age`付箋(変数)は別の値に添付(割り当て)されなかったため、`age`変数が`50`に更新されても変更されません。

:::::::::::::::::::::::::::::::::::::::  challenge

## F-string Syntax
## F文字列構文

Use an f-string to construct output in Python by filling in the blanks with variables and f-string syntax to tell Christina how old she will be in 10 years.

f文字列を使用して、変数とf文字列構文で空白を埋めてPythonで出力を構築し、クリスティーナに10年後に何歳になるかを伝えます。

Tip: You can combine variables and mathematical expressions in an f-string in the same way you can in variable assignment. We'll see more examples of dynamic f-string output as we go through the lesson.

ヒント: 変数の割り当てと同じように、変数と数学式をf文字列に組み合わせることができます。レッスンを進むにつれて、動的f文字列出力のより多くの例が表示されます。

```python
name = 'Christina'
age = 23

f'{____}, you will be ______ in 10 years.'
```

:::::::::::::::  solution

## Solution
## 解決策

```python
f'{name}, you will be {age + 10} in 10 years.'

```

```output
'Christina, you will be 33 in 10 years.'

```



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Swapping Values
## スワップ値

Draw a table showing the values of the variables in this program
after each statement is executed.
In simple terms, what do the last three lines of this program do?

このプログラムの変数の値を示す表を描画する

各ステートメントが実行された後。

簡単に言えば、このプログラムの最後の3行は何をしますか?


```python
x = 1.0
y = 3.0
swap = x
x = y
y = swap
```

:::::::::::::::  solution

## Solution
## 解決策

```
swap = x  #  x = 1.0 y = 3.0 swap = 1.0
x = y     #  x = 3.0 y = 3.0 swap = 1.0
y = swap  #  x = 3.0 y = 1.0 swap = 1.0
```

These three lines exchange the values in `x` and `y` using the `swap`
variable for temporary storage. This is a fairly common programming idiom.

これらの3行は、`swap`を使用して`x`と`y`の値を交換します

一時保管用の変数。これはかなり一般的なプログラミングの慣用句です。


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Predicting Values
## 値の予測

What is the final value of `position` in the program below?
(Try to predict the value without running the program,
then check your prediction.)

以下のプログラムの「位置」の最終値は何ですか？

(プログラムを実行せずに値を予測してみてください。

その後、あなたの予測を確認してください。)


```python
initial = "left"
position = initial
initial = "right"
```

:::::::::::::::  solution

## Solution
## 解決策

```python
initial = "left"  # Initial is assigned the string "left"
position = initial  # Position is assigned the variable initial, currently "left"
initial = "right"  # Initial is assigned the string "right"
print(position)
```

```output
left
```

The last assignment to position was "left"

ポジションへの最後の割り当ては「左」でした



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Can you slice integers?
## 整数をスライスできますか?

If you assign `a = 123`,
what happens if you try to get the second digit of `a`?

`a = 123`を割り当てると、

「A」の2桁目を取得しようとするとどうなりますか?

:::::::::::::::  solution

## Solution
## 解決策

Numbers are not stored in the written representation,
so they can't be treated like strings.

数字は書かれた表現に格納されません。

だから、彼らは文字列のように扱うことはできません。

```python
a = 123
print(a[1])
```

```error
TypeError: 'int' object is not subscriptable
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::  challenge

## Slicing
## スライス

We know how to slice using an explicit start and end point:

私たちは、明示的な開始点と終了点を使用してスライスする方法を知っています。

```python
library_name = 'Library of Babel'
f'library_name[1:3] is: {library_name[1:3]}'
```
```output
'library_name[1:3] is: ib'
```

But we can also use implicit and negative index values when we define a slice. Try the following (replacing `low` and `high` with index positions of your choosing) to figure out how these different forms of slicing work:

しかし、スライスを定義するときに、暗黙のインデックス値と負のインデックス値を使用することもできます。これらのさまざまな形式のスライスがどのように機能するかを把握するために、以下（「低」と「高」を選択したインデックス位置に置き換える）を試してみてください。

1. What does `library_name[low:]` (without a value after the colon) do?
1. `library_name[low:]`(コロンの後に値なし)は何をしますか?
2. What does `library_name[:high]` (without a value before the colon) do?
2.` library_name[:high]`(コロンの前に値なし)は何をしますか?
3. What does `library_name[:]` (just a colon) do?
3. `library_name[:]`(ただのコロン)は何をしますか?
4. What does `library_name[number:negative-number]` do?
4. `library_name[number:negative-number]`は何をしますか?

:::::::::::::::  solution

## Solution
## 解決策

1. It will slice the string, starting at the `low` index and stopping at the end of the string.
1. 文字列をスライスし、`low`インデックスから始まり、文字列の末尾で停止します。
2. It will slice the string, starting at the beginning on the string, and ending an element before the `high` index.
2. 文字列をスライスし、文字列の先頭から始まり、「high」インデックスの前に要素を終了します。
3. It will print the entire string.
3. 文字列全体が印刷されます。
4. It will slice the string, starting the `number` index, and ending a distance of the absolute value of `negative-number` elements from the end of the string.
4. 字列をスライスし、「number」インデックスを開始し、文字列の末尾から「negative-number」要素の絶対値の距離を終了します。  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Fractions
## 分数

What type of value is 3.4?
How can you find out?

3.4はどのような種類の値ですか?

どうやって知ることができますか?

:::::::::::::::  solution

## Solution
## 解決策

It is a floating-point number (often abbreviated "float").

それは浮動小数点数(しばしば「float」と略される)です。

```python
print(type(3.4))
```

```output
<class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Automatic Type Conversion
## 自動型変換

What type of value is 3.25 + 4?

3.25 + 4はどのような値ですか?

:::::::::::::::  solution

## Solution
## 解決策

It is a float: integers are automatically converted to floats as necessary.

それは浮動小数点数です: 整数は必要に応じて自動的に浮動小数点数に変換されます。

```python
result = 3.25 + 4
print(result, 'is', type(result))
```

```output
7.25 is <class 'float'>
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: keypoints

- Use variables to store values.
- 変数を使用して値を格納します。
- Use `print` to display values.
- 「印刷」を使用して値を表示します。
- Format output with f-strings.
- f文字列で出力をフォーマットします。
- Variables persist between cells.
- 変数は細胞間で持続する。
- Variables must be created before they are used.
- 変数は使用する前に作成する必要があります。
- Variables can be used in calculations.
- 変数は計算に使用できます。
- Use an index to get a single character from a string.
- インデックスを使用して、文字列から1文字を取得します。
- Use a slice to get a portion of a string.
- スライスを使用して、文字列の一部を取得します。
- Use the built-in function `len` to find the length of a string.
- 組み込み関数`len`を使用して、文字列の長さを見つけます。
- Python is case-sensitive.
- Pythonは大文字と小文字を区別します。
- Every object has a type.
- すべてのオブジェクトには型があります。
- Use the built-in function `type` to find the type of an object.
- 組み込み関数「type」を使用して、オブジェクトのタイプを検索します。
- Types control what operations can be done on objects.
- タイプは、オブジェクトに対して実行できる操作を制御します。
- Variables only change value when something is assigned to them.
- 変数は、何かが割り当てられている場合にのみ値を変更します。

::::::::::::::::::::::::::::::::::::::::::::::::::


