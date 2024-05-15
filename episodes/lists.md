---
title: Lists
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Create collections to work with in Python using lists.
- リストを使用してPythonで作業するコレクションを作成します。
- Write Python code to index, slice, and modify lists through assignment and method calls.
- 割り当てとメソッド呼び出しを通じて、リストをインデックス、スライス、変更するためのPythonコードを作成します。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I store multiple items in a Python variable?
- Python変数に複数のアイテムを保存するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## A list stores many values in a single structure.
## リストは、多くの値を単一の構造に格納します。

The most popular kind of data collection in Python is the list. Lists have two primary important characteristics:
Pythonで最も人気のある種類のデータ収集はリストです。リストには2つの主要な重要な特徴があります。

1. They are mutable, i.e., they can be changed after they are created.
1. それらは変更可能です。つまり、作成後に変更できます。
2. They are heterogeneous, i.e., they can store values of many different types.
2. それらは異種です。つまり、さまざまなタイプの値を格納できます。

In the dataset we will be working with soon, we'll look at the circulation numbers from a variety of branch libraries in Chicago, Illinois (USA). Each branch library has some metadata associated with it, including its zip (postal) code. We could use a Python list to organize some of those zip codes.

まもなく作業するデータセットでは、米国イリノイ州シカゴのさまざまな支部図書館の発行部数を見ていきます。各ブランチライブラリには、郵便番号を含むいくつかのメタデータが関連付けられています。Pythonリストを使用して、それらの郵便番号の一部を整理することができます。

To create a new list, you can just put some values in square brackets with commas in between.

新しいリストを作成するには、間にカンマで囲まれた角括弧内にいくつかの値を入れるだけです。

```python
zip_codes = [60625, 60827, 60632, 60644, 60634]
f'Zip codes: {zip_codes}'
```

```output
'Zip codes: [60625, 60827, 60632, 60644, 60634]'
```

We can use `len()` to find out how many values are in a list.

`len()` を使用して、リスト内の値の数を調べることができます。

```python
f'Number of zip codes: {len(zip_codes)}'
```

```output
'Number of zip codes: 5'
```

## Use an item's index to fetch it from a list.
## アイテムのインデックスを使用して、リストから取得します。

In the same way we used index numbers for strings, we can reference elements and slices in a list.

文字列にインデックス番号を使用したのと同じように、リスト内の要素とスライスを参照できます。

```python
print(f'1st item of zip_codes: {zip_codes[0]}')
print(f'The first three zip codes: {zip_codes[0:3]}')
```

```output
1st item of zip_codes: 60625
The first three zip codes: [60625, 60827, 60632]
```

## Reassign list values with their index.
## インデックスでリスト値を再割り当てします。

Use an index value along with your list variable to replace a value from the list.

リスト変数と一緒にインデックス値を使用して、リストの値を置き換えます。

```python
print(f'zip_codes was: {zip_codes}')
zip_codes[0] = 60640
print(f'zip_codes is now: {zip_codes}')
```

```output
zip_codes was: [60625, 60827, 60632, 60644, 60634]
zip_codes is now: [60640, 60827, 60632, 60644, 60634]
```


### Character strings are immutable.
### 文字列は不変です。

Unlike lists, we cannot change the characters in a string using its index value. In other words strings are *immutable* (cannot be changed in-place after creation), while lists are *mutable*: they can be modified in place. Python considers the string to be a single value with parts, not a collection of values.

リストとは異なり、インデックス値を使用して文字列内の文字を変更することはできません。言い換えれば、文字列は*不変*(作成後にその場で変更することはできません)、リストは*変更可能*です:その場で変更できます。Pythonは、文字列を値のコレクションではなく、部分を含む単一の値と見なします。

```python
branch_library = 'Ulbany Park' # misspelled Albany
branch_library[0] = 'A'
```

```error
TypeError: 'str' object does not support item assignment
```

## Lists may contain values of different types.

## リストには、さまざまなタイプの値が含まれている場合があります。

A single list may contain numbers, strings, and anything else (including other lists!). If you're dealing with a list within a list you can continue to use the square bracket notation to reference specific items.

単一のリストには、数字、文字列、その他のもの（他のリストを含む！）を含めることができます。リスト内のリストを扱っている場合は、引き続き角括弧表記を使用して特定の項目を参照できます。

```python
mixed_list = ['word', 3, 10.2, ['list', 'of', 'items']]
print(f'1st word in sublist: {mixed_list[3][0]}')
```

```output
1st word in sublist: list
```

## Appending items to a list lengthens it.
## リストにアイテムを追加すると、それが長くなります。

Use `list_name.append` to add items to the end of a list. In Python, we would call `.append()` a *method* of the list object. You can use the syntax of `object.method()` to call methods.

`list_name.append`を使用して、リストの最後にアイテムを追加します。Pythonでは、リストオブジェクトの*メソッド*を`.append()`と呼びます。`object.method()`の構文を使用してメソッドを呼び出すことができます。

```python
print(f'zip_codes was:{zip_codes}')
zip_codes.append(60647)
print(f'zip_codes is now: {zip_codes}')
```

```output
zip_codes was: [60640, 60827, 60632, 60644, 60634]
zip_codes is now: [60640, 60827, 60632, 60644, 60634, 60647]
```

## Use `del` to remove items from a list entirely.
## `del`を使用して、リストからアイテムを完全に削除します。

`del list_name[index]` removes an item from a list and shortens the list. Unlike `.append()`, `del` is not a method, but a statement in Python. In the example below, `del` performs an "in-place" operation on a list of prime numbers. This means that the `primes` variable will be reassigned when you use the `del` statement, without needing to use an assignment operator (e.g., `primes = ...`) .

`del list_name[index]`は、リストからアイテムを削除し、リストを短縮します。`.append()`とは異なり、`del`はメソッドではなく、Pythonのステートメントです。以下の例では、`del`は素数のリストで「インプレース」操作を実行します。これは、割り当て演算子を使用することなく、`del`ステートメントを使用すると、`primes`変数が再割り当てされることを意味します（例：`primes = ...`) 。

```python
primes = [2, 3, 5, 7, 11]
print(f'primes before removing last item: {primes}')
del primes[4]
print(f'primes after removing last item: {primes}')
```

```output
primes before removing last item: [2, 3, 5, 7, 11]
primes after removing last item: [2, 3, 5, 7]
```


:::::::::::::::::::::::::::::::::::::::  challenge

## Fill in the Blanks
## 空白を埋める

Fill in the blanks so that the program below produces the output shown. (Hint: Use [] on its own to represent a list that doesn’t contain any values.)
以下のプログラムが示されている出力を生成するように、空白を埋めてください。（ヒント：値を含まないリストを表すには、単独で[]を使用します。）

```python
values = ____
values.____(1)
values.____(3)
values.____(5)
print('first time:', values)
values = values[____]
print('second time:', values)
```

```output
first time: [1, 3, 5]
second time: [3, 5]
```

:::::::::::::::  solution

## Solution
## 解決策

```python
values = []
values.append(1)
values.append(3)
values.append(5)
print('first time:', values)
values = values[1:3]
print('second time:', values)
```

```output
first time [1, 3, 5]
second time [3, 5]
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## How Large is a Slice?
## スライスはどれくらいの大きさですか?

If 'low' and 'high' are both non-negative integers,
how long is the list returned by this slicing operation `values[low:high]`?

「低」と「高」の両方が非負の整数である場合、

このスライス操作`values[low:high]`によって返されるリストはどのくらいの期間ですか?

:::::::::::::::  solution

## Solution
## 解決策

The list's length would be equal to `high - low`.  

リストの長さは「高-低」に等しくなります。



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## From Strings to Lists and Back
## 文字列からリストへ、そして戻る

Given this:

これを考えると:

```python
print('string to list:', list('book'))
print('list to string:', ''.join(['a', 'r', 't', 'i', 'c', 'l', 'e']))
```

```output
['b', 'o', 'o', 'k']
'article'
```

1. Explain in simple terms what `list('some string')` does.
1. `list('some string')`が何をするかを簡単な言葉で説明する
2. What does `'-'.join(['x', 'y'])` generate? Note that the first set of single quotes is not empty.
2.`'-'.join(['x', 'y'])`は何を生成しますか?単一引用符の最初のセットは空ではないことに注意してください。

:::::::::::::::  solution

## Solution
## 解決策

1. It creates a list of the `some string`s characters as elements.
1. 要素として「いくつかの文字列」文字のリストを作成します。
2. It creates a string composed of `x` and `y`, separated by a hyphen character(`-`).  
2. ハイフン文字(`-`)で区切られた`x`と`y`で構成される文字列を作成します。  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Working With the End
## 終わりと共に働く

What does the following program print?

次のプログラムは何を印刷しますか?

```python
resources = ['books','periodicals','DVDs','maps',
'databases','abstracts']
print(resource[-1])
```

1. How does Python interpret a negative index?
1.Pythonは負のインデックスをどのように解釈しますか?
2. If a list or string has N elements,
  what is the most negative index that can safely be used with it,
  and what location does that index represent?
2. リストまたは文字列にN個の要素がある場合、
安全に使用できる最も負のインデックスは何ですか?
そして、そのインデックスはどの場所を表していますか?
3. If `resources` is a list, what does `del resources[-1]` do?
3. `resources`がリストの場合、`del resources[-1]`は何をしますか?
4. How can you display all elements but the last one without changing `resources`?
  (Hint: you will need to combine slicing and negative indexing.)
4. 「リソース」を変更せずに、最後の要素以外のすべての要素を表示するにはどうすればよいですか?

（ヒント：スライスとネガティブインデックスを組み合わせる必要があります。）
:::::::::::::::  solution

## Solution
## 解決策

```output
abstracts
```

1. A negative index begins at the final element.
1. 負のインデックスは最後の要素から始まります。
2. `-(N)` corresponds to the first index, which is the [0] index.
2. `-(N)`は、[0]インデックスである最初のインデックスに対応します。
3. It removes the final element of the list.
3. リストの最後の要素を削除します。
4. You could do the following: `print(resources[0:-1])`
4. 次のことができます: `print(resources[0:-1])`  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Stepping Through a List
## リストをステップスルーする

What does the following program print?

次のプログラムは何を印刷しますか?

```python
resources = ['books','periodicals','DVDs','maps',
'databases','abstracts'] 
print(resources[::2])
print(resources[::-1])
```

1. If we write a slice as `low:high:stride`, what does `stride` do?
1. スライスを「low:high:stride」と書くと、「stride」は何をしますか?
2. What expression would select all of the even-numbered items from a collection?
2. コレクションから偶数番号のアイテムをすべて選択する式は何ですか?
:::::::::::::::  solution

## Solution
## 解決策

```output
['books', 'DVDs', 'databases']
['abstracts', 'databases', 'maps', 'DVDs', 'periodicals', 'books']
```

1. `stride` indicates both the number of steps, and from which end: positive starts from first element, negative from the last element.
2. `resources[1::2]`
  
  

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Slice Bounds
## スライスバウンド

What does the following program print?

次のプログラムは何を印刷しますか?

```python
resources = ['books','periodicals','DVDs','maps',
'databases','abstracts'] 
print(resources[0:20])
print(resources[-1:3])
```

:::::::::::::::  solution

## Solution
## 解決策

```output
['books', 'periodicals', 'DVDs', 'maps', 'databases', 'abstracts']
[]
```

There is no 20th index, so the entire list is captured.  

20番目のインデックスがないので、リスト全体がキャプチャされます。

There is no element after the -1 index, so an empty list is returned as empty square brackets.  

-1インデックスの後に要素がないため、空のリストは空の角括弧として返されます。


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Sort and Sorted
## 並べ替えと並べ替え

What do these two programs print?

この2つのプログラムは何を印刷しますか?

In simple terms, explain the difference between `sorted(resources)` and `resources.sort()`.

簡単に言えば、`sorted(resources)`と`resources.sort()`の違いを説明してください。

```python
# Program A
resources =  ['books','periodicals','DVDs','maps',
'databases','abstracts'] 
result = sorted(resources)
print('resources is', resources, 'and result is', result)
```

```python
# Program B
resources = ['books','periodicals','DVDs','maps',
'databases','abstracts'] 
result = resources.sort()
print('resources is', resources, 'and result is', result)
```

:::::::::::::::  solution

## Solution
## 解決策

Program A:

```output
resources is ['books', 'periodicals', 'DVDs', 'maps', 'databases', 'abstracts'] and result is ['DVDs', 'abstracts', 'books', 'databases', 'maps', 'periodicals']
```
Notice that the capital letters in acronym DVD sort before lowercase letters.

Program B:

```output
resources is ['DVDs', 'abstracts', 'books', 'databases', 'maps', 'periodicals'] and result is None
```

`sorted(resources)` returns a sorted copy of the list, while `resources.sort()` function call sorts the list *in place* and returns `None`.  



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: keypoints

- A list stores many values in a single structure.
- リストは、多くの値を単一の構造に格納します。
- Use an item's index to fetch it from a list.
- アイテムのインデックスを使用して、リストから取得します。
- Lists' values can be replaced by assigning to them.
- リストの値は、それらを割り当てることで置き換えることができます。
- Appending items to a list lengthens it.
- リストにアイテムを追加すると、それが長くなります。
- Use `del` to remove items from a list entirely.
- `del`を使用して、リストからアイテムを完全に削除します。
- Lists may contain values of different types.
- リストには、さまざまなタイプの値が含まれている場合があります。
- Character strings can be indexed like lists.
- 文字列はリストのようにインデックスを作成できます。
- Character strings are immutable.
- 文字列は不変です。
- Indexing beyond the end of the collection is an error.
- コレクションの終わりを超えたインデックス作成はエラーです。

::::::::::::::::::::::::::::::::::::::::::::::::::


