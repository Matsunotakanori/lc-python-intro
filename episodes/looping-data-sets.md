---
title: Looping Over Data Sets
タイトル: 7. データセットのループ
teaching: 10
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Be able to read and write globbing expressions that match sets of files.
- Use glob to create lists of files.
- Write for loops to perform operations on files given their names in a list.
- ファイルのセットに一致するグロビング式を読み書きできる。

- globを使用してファイルのリストを作成します。

- リストに名前が指定されたファイルに対して操作を実行するためにループを書き込みます。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I process many data sets with a single command?
- 1つのコマンドで多くのデータセットを処理するにはどうすればよいですか?
::::::::::::::::::::::::::::::::::::::::::::::::::

## Use a `for` loop to process files given a list of their names.
## `for`ループを使用して、名前のリストが与えられたファイルを処理します。

If you recall from episode 06, the `pd.read_csv()` method takes a text string referencing a filename as an argument. If we have a list of strings that point to our filenames, we can loop through the list to read in each CSV file as a dataframe. Let's print out the maximum values from the 'ytd' (year to date) column for each dataframe.

エピソード06から思い出すと、`pd.read_csv()`メソッドは、ファイル名を引数として参照するテキスト文字列を取ります。ファイル名を指す文字列のリストがある場合は、リストをループして各CSVファイルをデータフレームとして読み取ることができます。各データフレームの「ytd」（年から現在まで）列から最大値を印刷しましょう。

```python
for filename in ['data/2011_circ.csv', 'data/2012_circ.csv']:
  data = pd.read_csv(filename)
  print(filename, data['ytd'].max())
```

```output
data/2011_circ.csv 9218
data/2012_circ.csv 10010
```

## Use `glob` to find sets of files whose names match a pattern.
## `glob`を使用して、名前がパターンに一致するファイルのセットを見つけます。


Fortunately, we don't have to manually type in a list of all of our filenames. We can use a Python library called `glob`, to work with paths and files in a convenient way. In Unix, the term "globbing" means "matching a set of files with a pattern". Glob gives us some nice pattern matching options:

幸いなことに、すべてのファイル名のリストを手動で入力する必要はありません。`glob`と呼ばれるPythonライブラリを使用して、パスやファイルを便利な方法で操作できます。Unixでは、「グロブ」という用語は「一連のファイルをパターンと一致させる」ことを意味します。Globは、私たちにいくつかの素敵なパターンマッチングオプションを提供します。

- `*` will "match zero or more characters"
- `?` will "match exactly one character"

The `glob` library contains a function also called `glob` to match file patterns. For example, `glob.glob('*.txt')` would match all files in the current directory with names that end with `.txt`.

`glob`ライブラリには、ファイルパターンを一致させる`glob`とも呼ばれる関数が含まれています。たとえば、`glob.glob('*.txt')`は、現在のディレクトリ内のすべてのファイルに「.txt`」で終わる名前を一致させます。

Let's create a list of the usage data CSV files. Because the `.glob()` argument includes a filepath in single quotes, we'll use double quotes around our f-string.

使用状況データCSVファイルのリストを作成しましょう。`.glob()` 引数には単一引用符でファイルパスが含まれているため、f文字列の周りに二重引用符を使用します。

```python
import glob
print(f"all csv files in data directory: {glob.glob('data/*.csv')}")
```

```output
all csv files in data directory: ['data/2011_circ.csv', 'data/2016_circ.csv', 'data/2017_circ.csv', 'data/2022_circ.csv', 'data/2018_circ.csv', 'data/2019_circ.csv', 'data/2012_circ.csv', 'data/2013_circ.csv', 'data/2021_circ.csv', 'data/2020_circ.csv', 'data/2015_circ.csv', 'data/2014_circ.csv']
```

## Use `glob` and `for` to process batches of files.
## `glob`と`for`を使用して、ファイルのバッチを処理します。

Now we can use glob in a `for` loop to create dataframes from all of the CSV files in the `data` directory. To use tools like `glob` it helps if files are named and stored consistently so that simple patterns will find the right data. You can learn more about how to name files to improve machine-readability from the [Open Science Foundation article on file naming](https://help.osf.io/article/146-file-naming).

これで、`for`ループでglobを使用して、`data`ディレクトリ内のすべてのCSVファイルからデータフレームを作成できます。「Glob」のようなツールを使用するには、ファイルに名前が付けられ、一貫して保存され、単純なパターンが適切なデータを見つけるのに役立ちます。[Open Science Foundation article on file naming](https://help.osf.io/article/146-file-naming)から、機械の読みやすさを向上させるためにファイルに名前を付ける方法について詳しく知ることができます。

```python
for csv in glob.glob('data/*.csv'):
  data = pd.read_csv(csv)
  print(csv, data['ytd'].max())
```

```output
data/2011_circ.csv 1678047
data/2016_circ.csv 3478369
data/2017_circ.csv 3623318
data/2022_circ.csv 6336579
data/2018_circ.csv 4006963
data/2019_circ.csv 4821180
data/2012_circ.csv 1707032
data/2013_circ.csv 2069537
data/2021_circ.csv 6629348
data/2020_circ.csv 8222810
data/2015_circ.csv 3195053
data/2014_circ.csv 2792631
```

The output of the files above may be different for you, depending on what operating system you use. The glob library doesn't have its own internal system for determining how filenames are sorted, but instead relies on the operating system's filesystem. Since operating systems can differ, it is helpful to use Python to manually sort the glob files so that everyone will see the same results, regardless of their operating system. You can do that by applying the Python method `sorted()` to the `glob.glob` list.

上記のファイルの出力は、使用するオペレーティングシステムによって異なる場合があります。Globライブラリには、ファイル名のソート方法を決定するための独自の内部システムはありませんが、代わりにオペレーティングシステムのファイルシステムに依存しています。オペレーティングシステムは異なる可能性があるため、オペレーティングシステムに関係なく、誰もが同じ結果を見ることができるように、Pythonを使用してglobファイルを手動でソートすると便利です。Pythonメソッド `sorted()` を `glob.glob` リストに適用することで、これを行うことができます。

```python
for csv in sorted(glob.glob('data/*.csv')):
    data = pd.read_csv(csv)
    print(csv, data['ytd'].max())
```

```output
data/2011_circ.csv 1678047
data/2012_circ.csv 1707032
data/2013_circ.csv 2069537
data/2014_circ.csv 2792631
data/2015_circ.csv 3195053
data/2016_circ.csv 3478369
data/2017_circ.csv 3623318
data/2018_circ.csv 4006963
data/2019_circ.csv 4821180
data/2020_circ.csv 8222810
data/2021_circ.csv 6629348
data/2022_circ.csv 6336579
```

## Appending dataframes to a list
## データフレームをリストに追加する

In the example above, we can print out results from each dataframe as we cycle through them, but it would be more convenient if we saved all of the yearly usage data in these CSV files into dataframes that we could work with later on. We can do that by using a list "accumulator" (as we covered in the last episode) and appending each dataframe to an empty list. You can create an empty list by assigning a variable to empty square brackets before the loop begins.

上記の例では、各データフレームの結果を循環しながら出力できますが、これらのCSVファイルの年間使用状況データをすべて、後で作業できるデータフレームに保存すると便利です。リスト「アキュムレータ」(前回のエピソードで説明したように)を使用し、各データフレームを空のリストに追加することで、それを行うことができます。ループが始まる前に空の角括弧に変数を割り当てることで、空のリストを作成できます。

```python
dfs = [] # an empty list to hold all of our dataframes
counter = 1

for csv in sorted(glob.glob('data/*.csv')):
  data = pd.read_csv(csv)
  print(f'{counter} Saving {len(data)} rows from {csv}')
  dfs.append(data)
  counter += 1

print(f'Number of saved dataframes: {len(dfs)}')
```

```output
1 Saving 83 rows from data/2011_circ.csv
2 Saving 82 rows from data/2012_circ.csv
3 Saving 83 rows from data/2013_circ.csv
4 Saving 83 rows from data/2014_circ.csv
5 Saving 83 rows from data/2015_circ.csv
6 Saving 83 rows from data/2016_circ.csv
7 Saving 83 rows from data/2017_circ.csv
8 Saving 83 rows from data/2018_circ.csv
9 Saving 84 rows from data/2019_circ.csv
10 Saving 85 rows from data/2020_circ.csv
11 Saving 85 rows from data/2021_circ.csv
12 Saving 86 rows from data/2022_circ.csv
Number of saved dataframes: 12
```

## Concatenating dataframes 
## データフレームのコンカテネーション

There are many different ways to merge, join, and concatenate pandas dataframes together. The [pandas documentation has good examples](https://pandas.pydata.org/docs/user_guide/merging.html) of how to use the `.merge()`, `.join()`, and `.concat()` methods to accomplish different goals. Because all of our CSVs have the exact same columns, if we want to concatenate them vertically (adding all of the rows from each dataframe together in order), we can do so using `concat()`, which takes a list of dataframes as its first argument. Since we aren't using a specific column as a pandas index, we'll set the argument of `ignore_index` to be True. 

パンダのデータフレームをマージ、結合、連結する方法はさまにあります。[Pandasドキュメントには、異なる目標を達成するために`.merge()`、`.join()`、および`.concat()`メソッドを使用する方法の良い例](https://pandas.pydata.org/docs/user_guide/merging.html)。すべてのCSVはまったく同じ列を持っているため、垂直に連結したい場合(各データフレームからすべての行を順番に追加する)、最初の引数としてデータフレームのリストを取る `concat()` を使用して行うことができます。特定の列をパンダインデックスとして使用していないため、`ignore_index`の引数をTrueに設定します。

```python
df = pd.concat(dfs, ignore_index=True)
f'Number of rows in df: {len(df)}'
```

```output
'Number of rows in df: 1003'
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Determining Matches
## 試合の決定

Which of these files would be matched by the expression `glob.glob('data/*circ.csv')`?

これらのファイルのうち、「glob.glob('data/*circ.csv')」という式と一致するのはどれですか？

1. `data/2011_circ.csv`
2. `data/2012_circ_stats.csv`
3. `circ/2013_circ.csv`
4. Both 1 and 3

:::::::::::::::  solution

## Solution
## 解決策

Only item 1 is matched by the wildcard expression `data/*circ.csv`. 
項目1のみがワイルドカード式`data/*circ.csv`と一致します。



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Minimum circulation per year
## 年間最小発行部数

Modify the following code to print out the lowest value in the `ytd` column from each year/file.

次のコードを変更して、各年/ファイルから「ytd」列の最低値を印刷します。

```python
import pandas as pd
for csv in sorted(glob.glob('data/*.csv')):
    data = pd.read_csv(____)
    print(csv, data['____'].____())
    
```

:::::::::::::::  solution

## Solution
## 解決策

```python
import pandas as pd
for csv in sorted(glob.glob('data/*.csv')):
    data = pd.read_csv(csv)
    print(csv, data['ytd'].min())
    
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Compile CSVs into one dataframe
## CSVを1つのデータフレームにコンパイルする

Imagine you had a folder named `outputs/` that included all kinds of different file types. Use `glob` and a `for` loop to iterate through all of the CSV files in the folder that have a file name that begins with `data`. Save them to a list called `dfs`, and then use `pd.concat()` to concatenate all of the dataframes from the `dfs` list together into a new dataframe called, `new_df`. You can assume that all of the data CSV files have the same columns so they will concatenate together cleanly using `pd.concat()`.

あらゆる種類の異なるファイルタイプを含む「outputs/」という名前のフォルダがあると想像してみてください。`glob`と`for`ループを使用して、`data`で始まるファイル名を持つフォルダ内のすべてのCSVファイルをイテートします。それらを`dfs`というリストに保存し、`pd.concat()`を使用して、`dfs`リストのすべてのデータフレームを`new_df`という新しいデータフレームに連結します。すべてのデータCSVファイルが同じ列を持っていると仮定できるので、`pd.concat()`を使用してきれいに連結されます。


:::::::::::::::  solution

## Solution
## 解決策

```python
import pandas as pd

dfs = []

for csv in sorted(glob.glob('outputs/data*.csv')):
    data = pd.read_csv(csv)
    dfs.append(data)
    
new_df = pd.concat(dfs, ignore_index=True)
    
```

:::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Use a `for` loop to process files given a list of their names.
- Use `glob.glob` to find sets of files whose names match a pattern.
- Use `glob` and `for` to process batches of files.
- Use a list “accumulator” to append a dataframe to an empty list `[]`.
- The `.merge()`, `.join()`, and `.concat()` methods can combine pandas dataframes.

- `for`ループを使用して、名前のリストが与えられたファイルを処理します。

- `glob.glob`を使用して、名前がパターンに一致するファイルのセットを検索します。

- `glob`と`for`を使用して、ファイルのバッチを処理します。

- リスト「アキュムレータ」を使用して、空のリスト`[]`にデータフレームを追加します。

- `.merge()`、`.join()`、および`.concat()`メソッドは、パンダのデータフレームを組み合わせることができます。
  
::::::::::::::::::::::::::::::::::::::::::::::::::


