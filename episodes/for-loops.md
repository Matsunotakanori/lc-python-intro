---
title: For Loops
タイトル: 6. For Loops
teaching: 25
exercises: 15
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explain what `for` loops are normally used for.
- Trace the execution of an un-nested loop and correctly state the values of variables in each iteration.
- Write `for` loops that use the accumulator pattern to aggregate values.
- 「for」ループが通常何に使われるのかを説明してください。
- ネストされていないループの実行をトレースし、各反復で変数の値を正しく述べます。
- アキュムレータパターンを使用して値を集約する「for」ループを記述します。
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I execute Python code iteratively across a collection of values?
- 値のコレクション全体でPythonコードを反復的に実行するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## For loops
## ループ用

Let's create a short list of numbers in Python, and then attempt to print out each value in the list. 

Pythonで数字の短いリストを作成し、リスト内の各値を印刷してみましょう。

```python
odds = [1, 3, 5, 7]
```

One way to print each number is to use a `print` statement with the index value for each item in the list:

各番号を印刷する1つの方法は、リスト内の各項目のインデックス値を持つ「print」ステートメントを使用することです。

```python
print(odds[0], odds[1], odds[2], odds[3])
```

```output
1 3 5 7
```

This is a bad approach for three reasons:

これは3つの理由で悪いアプローチです。

1. **Not scalable**. Imagine you need to print a list that has hundreds
  of elements.  

2. **Difficult to maintain**. If we want to add another change -- multiplying each number by 5, for example -- we would have to change the code for every item in the list, which isn't sustainable

3. **Fragile**. Hand-numbering index values for each item in a list is likely to cause errors if we make any mistakes.

1. **スケーラブルではありません**。何百ものリストを印刷する必要があると想像してみてください

要素の。

2. **維持が難しい**。たとえば、各数字に5を掛けるなど、別の変更を追加したい場合は、リスト内のすべての項目のコードを変更する必要がありますが、これは持続可能ではありません

3. **壊れやすい**。リスト内の各項目のインデックス値のハンドナンバリングは、間違いを犯すとエラーを引き起こす可能性があります。

```python
odds = [1, 3, 5]
print(odds[0], odds[1], odds[2], odds[3])
```

We get an IndexError when we try to refer to an item in a list that does not exist.

存在しないリスト内の項目を参照しようとすると、IndexErrorが発生します。

```error
---------------------------------------------------------------------------
IndexError                                Traceback (most recent call last)
<ipython-input-3-7974b6cdaf14> in <module>()
      3 print(odds[1])
      4 print(odds[2])
----> 5 print(odds[3])

IndexError: list index out of range
```

A `for` loop is a better solution:

`for`ループはより良い解決策です。

```python
odds = [1, 3, 5, 7]
for num in odds:
    print(num)
```

```output
1
3
5
7
```

A `for` loop repeats an operation -- in this case, printing -- once for each element it encounters in a collection. The general structure of a loop is:

「For」ループは、コレクションで遭遇する要素ごとに操作（この場合は印刷）を1回繰り返します。ループの一般的な構造は次のとおりです。

```python
for variable in collection:
    # do things using variable, such as print
```

We can call the loop variable anything we like, there must be a colon at the end of the line starting the loop, and we must indent anything we want to run inside the loop. Unlike many other programming languages, there is no command to signify the end of the loop body; everything indented after the `for` statement belongs to the loop.

ループ変数を好きなように呼び出すことができ、ループを開始する行の最後にコロンがなければならず、ループ内で実行したいものをインデントする必要があります。他の多くのプログラミング言語とは異なり、ループ本体の終わりを示すコマンドはありません。「for」ステートメントの後にインデントされたものはすべてループに属します。


Loops are more robust ways to deal with containers like lists. Even if the values of the `odds` list changes, the loop will still work.

ループは、リストのようなコンテナに対処するためのより堅牢な方法です。「オッズ」リストの値が変更されても、ループは引き続き機能します。

```python
odds = [1, 3, 5, 7, 9, 11]
for num in odds:
    print(num)
```

```output
1
3
5
7
9
11
```

Using a shorter version of the odds example above, the loop might look like this:

![](fig/for_loop.png){alt="Loop variable 'num' being assigned the value of each element in the list odds in turn and then being printed"}

Each number (`num`) variable in the `odds` list is looped through and printed one number after another. 

上記のオッズの例の短いバージョンを使用すると、ループは次のようになります。

![](Fig/for_loop.png){alt="ループ変数 'num' が順番にリストのオッズの各要素の値が割り当てられ、印刷されます"}

「オッズ」リストの各数字(`num`)変数はループされ、次々と印刷されます。

## Loop variables 
## ループ変数

Loop variables are created on demand when you define the loop and they will persist after the loop finishes. Like all variable names, it's helpful to give `for` loop variables meaningful names that you'll understand as the code in your loop grows. `for num in odds` is easier to understand than `for kitten in odds`, for example.

ループ変数は、ループを定義するときにオンデマンドで作成され、ループが終了した後も保持されます。すべての変数名と同様に、ループ内のコードが大きくなるにつれて理解できる「for」ループ変数に意味のある名前を与えると便利です。たとえば、「for num in odds」は、「for kitten in odds」よりも理解しやすいです。


## You can loop through other Python objects
## 他のPythonオブジェクトをループできます

You can use a `for` loop to iterate through each element in a string. `for` loops are not limited to operating on lists. 

`for` ループを使用して、文字列内の各要素をイテレートできます。`for` ループは、リストの操作に限定されません。

```python
for letter in 'library of babel':
  print(letter)
```

```output
L
i
b
r
a
r
y
 
o
f
 
B
a
b
e
l
```


## Use `range` to iterate over a sequence of numbers.
## 「範囲」を使用して、一連の数字を反復します。

The built-in function `range()` produces a sequence of numbers. You can pass a single parameter to identify how many items in the sequence to range over (e.g. `range(5)`) or if you pass two arguments, the first corresponds to the starting point and the second to the end point. The end point works in the same way as Python index values ("up to, but not including").

組み込み関数 `range()` は、一連の数値を生成します。単一のパラメータを渡して、シーケンス内の範囲の項目の数を識別できます（例：`range(5)`）、または2つの引数を渡すと、最初の引数は始点に対応し、2番目は終点に対応します。エンドポイントは、Pythonのインデックス値と同じように機能します(「最大、ただし含まない」)。

```python
for number in range(0,3):
    print(number)
```

```output
0
1
2
```

## Accumulators
##アキュムレータ

A common loop pattern is to initialize an *accumulator* variable to zero, an empty string, or an empty list before the loop begins. Then the loop updates the accumulator variable with values from a collection.

一般的なループパターンは、ループが始まる前に*アキュムレータ*変数をゼロ、空の文字列、または空のリストに初期化することです。その後、ループはコレクションの値でアキュムレータ変数を更新します。

We can use the `+=` operator to add a value to `total` in the loop below, so that each time we iterate through the loop we'll add the index value of the `range()` to `total`.

`+=` 演算子を使用して、以下のループで `total` に値を追加できるため、ループをイテレートするたびに `range()` のインデックス値を `total` に追加します。

```python
# Sum the first 10 integers.
total = 0

# range(1,11) will give us the numbers 1 through 10
for num in range(1, 11):
    print(f'num is: {num} total is: {total}')
    total += num

print(f'Loop finished. num is: {num} total is: {total}')
```

```output
num is: 1 total is: 0
num is: 2 total is: 1
num is: 3 total is: 3
num is: 4 total is: 6
num is: 5 total is: 10
num is: 6 total is: 15
num is: 7 total is: 21
num is: 8 total is: 28
num is: 9 total is: 36
num is: 10 total is: 45
Loop finished. Num is: 10 total is: 55
```

- The first time through the loop, `total` is equal to 0, and `num` is 1 (the range starts at 1). After those values print out we add 1 to the value of `total` (0), to get 1. 
- The second time through the loop, `total` is equal to 1, and `num` is 2. After those print out we add 2 to the value of `total` (1), to get 3.
- The third time through the loop, `total` is equal to 3, and `num` is 3. After those print out we add 3 to the value of `total` (3), to bring us to 6.
- And so on.
- After the loop is finished the values of `total` and `num` retain the values that were assigned the last time through the loop. So `num` is equal to 10 (the last index value of `range()`) and `total` is equal to 55 (45 + 10). 

- ループを初めて通過すると、`total`は0に等しく、`num`は1です(範囲は1から始まります)。これらの値を印刷した後、`total` (0)の値に1を加算して1を取得します。

- ループを通る2回目、`total`は1に等しく、`num`は2です。それらの印刷後、「合計」（1）の値に2を追加し、3を取得します。

- ループを通る3回目、`total`は3に等しく、`num`は3です。それらを印刷した後、「合計」（3）の値に3を追加し、6になります。

- などなど。

- ループが終了した後、`total`と`num`の値は、ループを介して最後に割り当てられた値を保持します。したがって、`num`は10（`range()`)の最後のインデックス値）に等しく、`total`は55（45 + 10）に等しいです。

:::::::::::::::::::::::::::::::::::::::  challenge

## Loop through a list
## リストをループする

Create a list of three vegetables, and then build a `for` loop to print out each vegetable from the list.

3つの野菜のリストを作成し、「for」ループを作成して、リストから各野菜を印刷します。

Bonus: Create an accumulator variable to print out the index value of each item in the list along with the vegetable name.

ボーナス: アキュムレータ変数を作成して、リスト内の各項目のインデックス値を野菜名と一緒に印刷します。

:::::::::::::::  solution

## Solution

```python
vegetables = ['lettuce', 'carrots', 'celery']
for veg in vegetables:
    print(veg)
    
```

```output
lettuce
carrots
celery
```
Bonus:

```python
idx = 0
vegetables = ['lettuce', 'carrots', 'celery']
for veg in vegetables:
    print(idx, veg)
    idx += 1
    
```

```output
0 lettuce
1 carrots
2 celery
```


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::
:::::::::::::::::::::::::::::::::::::::  challenge

## Use range() in a loop
## ループで range() を使用する

Print out the numbers 10, 11, 12, 13, 14, 15, using range() in a `for` loop.

`for` ループで range() を使用して、数字 10、11、12、13、14、15 を印刷します。

:::::::::::::::  solution

## Solution

```python

for num in range(10, 16):
    print(num)
    
```

```output
10
11
12
13
14
15
```


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Use a string index in a loop
## ループで文字列インデックスを使用する

How would you loop through a list with the values 'red', 'green', and 'blue' to create the acronym `rgb`, pulling from the first letters in each string? Print the acronym when the loop is finished.

各文字列の最初の文字から引き出して、頭字語「rgb」を作成するために、「赤」、「緑」、「青」の値を持つリストをどのようにループしますか?ループが終了したら頭字語を印刷します。

Hint: Use the `+` operator to concatenate strings together. For example, `lib = 'lib' + 'rary'` will assign the value of 'library' to `lib`.

ヒント: `+`演算子を使用して、文字列を連結します。たとえば、`lib = 'lib' + 'rary'`は'library'の値を`lib`に割り当てます。

:::::::::::::::  solution

## Solution
## 解決策

```python
acronym = ''
for color in ['red', 'green', 'blue']:
    acronym = acronym + color[0]
print(acronym)
```

```output
rgb
```

You could also concatenate inside of the loop with `acronym += color[0]`.

ループ内を `acronym += color[0]` で連結することもできます。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Subtract a list of values in a loop
## ループ内の値のリストを減算する

1. Create an accumulator variable called `total` that starts at 100.
2. Create a list called `numbers` with the values of 10, 15, 20, 25, 30.
3. Create a `for` loop to iterate through each item in the list.
4. Each time through the list update the value of `total` to subtract the value of the current list item from `total`. Tip: `-=` works for subtraction in the same way that `+=` works for addition.
5. Print the value of `total` inside of the loop to keep track of its value throughout.

1. 100で始まる「total」というアキュムレータ変数を作成します。

2. 10、15、20、25、30の値で「数字」というリストを作成します。

3. 「For」ループを作成して、リスト内の各項目をイテレートします。

4. 毎回、リストを通して「合計」の値を更新して、「合計」から現在のリスト項目の値を減算します。ヒント: `-=` は、`+=` が加算で機能するのと同じように、減算で機能します。

5. ループ内に「合計」の値を印刷して、全体を通してその値を追跡します。

:::::::::::::::  solution

## Solution
## 解決策

```python
total = 100
numbers = [10, 15, 20, 25, 30]
for num in numbers:
    total -= num
    print(total)
```

```output
90
75
55
30
0
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: keypoints

- A *for loop* executes commands once for each value in a collection.
- The first line of the `for` loop must end with a colon, and the body must be indented.
- Indentation is always meaningful in Python.
- A `for` loop is made up of a collection, a loop variable, and a body.
- Loop variables can be called anything (but it is strongly advised to have a meaningful name to the looping variable).
- The body of a loop can contain many statements.
- Use `range` to iterate over a sequence of numbers.
- The Accumulator pattern turns many values into one.

- *for loop*は、コレクション内の各値に対してコマンドを1回実行します。

- 「for」ループの最初の行はコロンで終わらなければならず、本文はインデントする必要があります。

- インデントはPythonでは常に意味があります。

- 「for」ループは、コレクション、ループ変数、および本体で構成されています。

- ループ変数は何でも呼び出すことができます(ただし、ループ変数に意味のある名前を持つことを強くお勧めします)。

- ループの本体には、多くのステートメントを含めることができます。

- 「範囲」を使用して、一連の数字を反復します。

- アキュムレータパターンは、多くの値を1つに変えます。

::::::::::::::::::::::::::::::::::::::::::::::::::


