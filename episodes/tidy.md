---
title: Tidy Data with Pandas
タイトル: Tidy Data with Pandas
teaching: 90  
exercises: 10  
---

::::::::::::::::::::::::::::::::::::::: objectives
* Identify the characteristics of tidy data and explain its benefits, listing the three principles and discussing how it facilitates data analysis during a review session.
* Use pandas functions like concat(), melt(), and data filtering to manipulate and clean a complex dataset, successfully combining multiple files into a single DataFrame and reshaping it using melt()
* 整頓されたデータの特性を特定し、その利点を説明し、3つの原則をリストし、レビューセッション中にデータ分析をどのように促進するかを議論します。

* concat()、melt()、データフィルタリングなどのパンダ関数を使用して、複雑なデータセットを操作およびクリーニングし、複数のファイルを単一のDataFrameにうまく結合し、melt()を使用して再形成します。

::::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::: questions
- What are the benefits of transforming data into a tidy format for analysis?
- How does the melt() function in pandas facilitate data tidying?
- What are some practical challenges when working with real-world datasets in Python, and how can they be addressed?
- データを分析のための整頓された形式に変換する利点は何ですか?

- パンダのmelt()関数は、データの整頓をどのように促進しますか?

- Pythonで現実世界のデータセットを扱う際の実用的な課題は何ですか？それらにどのように対処できますか？
::::::::::::::::::::::::::::::::::::::::::::::::::


# Tidy Data in Pandas 
# パンダの整頓データ

To recap work in the past two episodes, we used the `glob` package to help us work with files on our machine and work on them in Python. We learned about `pandas`, Python's main data cleaning and analysis library.

過去2つのエピソードの作業を要約するために、「glob」パッケージを使用して、マシン上のファイルを操作し、Pythonで作業しました。Pythonのメインデータクリーニングおよび分析ライブラリである「pandas」について学びました。


```python
import glob
import pandas as pd
```

We used `glob` and `pandas` to combine our Chicago public library circulation data into one dataframe. If you have not done this already, the following code will loop through our files, read in the `csv`'s as dataframes, and then append those together in a list and using the pandas `concat` function to merge together. You can check out your Python environment to see if you have a dataframe named `df` by using `%whos`.

「Glob」と「pandas」を使用して、シカゴ公共図書館の循環データを1つのデータフレームにまとめました。これをまだ行っていない場合は、次のコードがファイルをループし、`csv`をデータフレームとして読み込み、それらをリストに追加し、pandas `concat`関数を使用してマージします。Python環境をチェックして、`%whos`を使用して`df`という名前のデータフレームがあるかどうかを確認できます。

```python
%whos
```

```output
    Variable   Type      Data/Info
    ------------------------------
    glob       module    <module 'glob' from '/Use<...>/lib/python3.11/glob.py'>
    pd         module    <module 'pandas' from '/U<...>ages/pandas/__init__.py'>

```

```python
dfs = [] 

for csv in glob.glob('data/*.csv'):
    data = pd.read_csv(csv)
    dfs.append(data)
```

:::::::::::::::::::::::::::::::::::::::  challenge
## Review
1. What does `*` in `glob.glob('data/*.csv')` do? 
2. What kind of a Python object is the first occurrence of `csv` in the statement `for csv in glob.glob('data/*.csv'):`?
3. What does `dfs.append(data)` accomplish?

## レビュー

1. `glob.glob('data/*.csv')`の`*`は何をしますか?

2. ステートメント `for csv in glob.glob('data/*.csv'):` の `csv` の最初の出現は、どのような Python オブジェクトですか?

3. `dfs.append(data)`は何を達成しますか?

:::::::::::::::  solution

## Solution

1. The asterisk is a wildcard that finds any number of characters in files in the `data/` directory with the filetype `.csv`.
2. `for csv` creates a new variable that corresponds with each item the loop encounters when iterating across all of the files in `glob.glob('data/*.csv')`.
3. It appends each DataFrame that was read in from the CSV file during the loop to a list called `dfs`. So `dfs` will be a list of DataFrames corresponding to each CSV file in the `data/` directory.

## 解決策

1.アスタリスクは、ファイルタイプ `.csv` の `data/` ディレクトリ内のファイル内の任意の数の文字を見つけるワイルドカードです。

2. `for csv`は、`glob.glob('data/*.csv')`内のすべてのファイルをイタレートするときにループが遭遇する各項目に対応する新しい変数を作成します。

3.ループ中にCSVファイルから読み込まれた各DataFrameを「dfs」というリストに追加します。したがって、`dfs`は、`data/`ディレクトリ内の各CSVファイルに対応するDataFrameのリストになります。

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

Next, let's concatenate all of the DataFrames in `dfs` together.

次に、「dfs」のすべてのDataFrameを一緒に連結しましょう。

```python
df = pd.concat(dfs, ignore_index=True)
```

We can look at the head of our combined dataset: 

```python
df.info()
```

```output
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1003 entries, 0 to 1002
    Data columns (total 18 columns):
     #   Column     Non-Null Count  Dtype  
    ---  ------     --------------  -----  
     0   branch     1003 non-null   object 
     1   address    643 non-null    object 
     2   city       643 non-null    object 
     3   zip code   643 non-null    float64
     4   january    1003 non-null   int64  
     5   february   1003 non-null   int64  
     6   march      1003 non-null   int64  
     7   april      1003 non-null   int64  
     8   may        1003 non-null   int64  
     9   june       1003 non-null   int64  
     10  july       1003 non-null   int64  
     11  august     1003 non-null   int64  
     12  september  1003 non-null   int64  
     13  october    1003 non-null   int64  
     14  november   1003 non-null   int64  
     15  december   1003 non-null   int64  
     16  ytd        1003 non-null   int64  
     17  year       1003 non-null   int64  
    dtypes: float64(1), int64(14), object(3)
    memory usage: 141.2+ KB

```

```python
df.tail()
```

Table: Tail of df

| | branch                    | address             | city    |   zip code |   january |   february |   march |   april |    may |   june |   july |   august |   september |   october |   november |   december |     ytd |   year|
|-----:|:--------------------------|:--------------------|:--------|-----------:|----------:|-----------:|--------:|--------:|-------:|-------:|-------:|---------:|------------:|----------:|-----------:|-----------:|--------:|-------:|
|  998 | Woodson Regional          | 9525 S. Halsted St. | Chicago |      60628 |      8074 |       7208 |    8580 |    9424 |   8548 |   9093 |   9747 |     9609 |        9412 |      9631 |       8851 |       7748 |  105925 |   2014 |
|999 | Wrightwood-Ashburn        | 8530 S. Kedzie Ave. | Chicago |      60652 |      2307 |       2496 |    2894 |    2945 |   2915 |   3516 |   3708 |     3303 |        3167 |      3246 |       2873 |       2959 |   36329 |   2014 |
| 1000 | Downloadable Media        | nan                 | nan     |        nan |     47023 |      41299 |   46942 |   54642 |  55598 |  57774 |  61783 |    63758 |       61432 |     62406 |      66028 |      71276 |  689961 |   2014 |
| 1001 | Renewals - Online         | nan                 | nan     |        nan |    209934 |     196047 |  219824 |  213200 | 214743 | 220111 | 245478 |   243202 |      246715 |    258325 |     259521 |     265531 | 2792631 |   2014 |
| 1002 | Talking Books and Braille | nan                 | nan     |        nan |      9883 |       9978 |    9796 |   12551 |  11076 |  11165 |  12538 |    12080 |       11878 |     12500 |       9959 |      10277 |  133681 |   2014 |

Let's take a moment to discuss the setup of our DataFrame. It is structured in what is known as a wide format. This format displays an extensive amount of data directly on the screen, with each month's circulation counts spread across the columns in a pivoted manner. This layout makes it easier to read and manually manipulate the data in a spreadsheet and because of this, is often the default output for periodic reporting systems like integrated library systems.

少し時間を取って、DataFrameのセットアップについて話し合いましょう。それはワイドフォーマットとして知られているもので構成されています。この形式は、大量のデータを画面に直接表示し、毎月の発行部数がピボットされた方法で列に分散します。このレイアウトにより、スプレッドシート内のデータの読み取りと手動操作が容易になります。このため、統合ライブラリシステムなどの定期的なレポートシステムのデフォルトの出力になることがよくあります。

However, this wide format can pose challenges when working with data analysis tools like Pandas. For instance, if we need to identify all the library branches where circulation exceeded 10,000 in any given month, we would have to individually check each column dedicated to a month, which can be quite cumbersome.

しかし、このワイドフォーマットは、パンダのようなデータ分析ツールを扱う際に課題をもたらす可能性があります。たとえば、特定の月に発行部数が10,000を超えるすべての図書館支店を特定する必要がある場合は、1か月専用の各列を個別にチェックする必要がありますが、これはかなり面倒です。

To address this we can reshape our data in a long format. This is sometimes called un-pivoting the data, and in our case the month columns will become a single variable in the dataset.

これに対処するために、データを長い形式に再構築することができます。これはデータのピボット解除と呼ばれることがあり、私たちの場合、月の列はデータセット内の単一の変数になります。

## Tidy Data 

Tidy data is a standard way of organizing data values within a dataset, making it easier to work with. Here are the key principles of tidy data:
1. Every column holds a single variable, like "month" or "temperature."
2. Every row represents a single observation, like circulation counts by branch and month.
3. Every cell contains a single value.

## 整頓されたデータ

整頓されたデータは、データセット内のデータ値を整理する標準的な方法であり、作業を容易にします。整頓されたデータの主な原則は次のとおりです。

1.すべての列には、「月」や「温度」などの単一の変数があります。

2.すべての行は、枝や月ごとの循環カウントのように、単一の観察を表します。

3.すべてのセルには単一の値が含まれています。

The image below might help orient us to the concept of tidy data. 

下の画像は、整頓されたデータの概念に私たちを向けるのに役立つかもしれません。

![Tidy Data](fig/tidy-1.png){alt='image showing variables in columns, observations in rows, and values in cellssan'}

R for Data Science [12.1](https://r4ds.had.co.nz/tidy-data.html#fig:tidy-structure)

データサイエンスのためのR [12.1](https://r4ds.had.co.nz/tidy-data.html#fig:tidy-structure)

### Benefits of Tidy Data

Transforming our data into a tidy data format provides several advantages:
- Python operations, such as visualization, filtering, and statistical analysis libraries, work better with data in a tidy format.
- Tidy data makes transforming, summarizing, and visualizing information easier. For instance, comparing monthly trends or calculating annual averages becomes more straightforward.
- As datasets grow, tidy data ensures that they remain manageable and analyses remain accurate.

### 整頓されたデータの利点

データを整頓されたデータ形式に変換すると、いくつかの利点があります。

- 視覚化、フィルタリング、統計分析ライブラリなどのPython操作は、整頓された形式のデータでよりよく機能します。

- 整頓されたデータは、情報の変換、要約、視覚化を容易にします。たとえば、毎月の傾向を比較したり、年間平均を計算したりすると、より簡単になります。

- データセットが成長するにつれて、整頓されたデータは管理可能であり、分析が正確であることを保証します。

## Making Our Data Tidy
## データを整頓する

A good step towards tidying our data would be to consolidate the separate month columns into a column called `month,` and the circulation counts into another column called `circulation_counts.` This simplifies our data and aligns with the principles of tidy data.

データを整頓するための良いステップは、別々の月の列を「月」と呼ばれる列に統合し、循環を「circulation_counts」と呼ばれる別の列にカウントすることです。これは私たちのデータを簡素化し、整頓されたデータの原則と一致します。

To achieve this transformation, we can use a Pandas function called `melt()`. This function reshapes the data from wide to long format, where each row will represent one month's circulation data for a branch. Let's look at the help for `melt` first.

この変換を達成するために、`melt()`というパンダ関数を使用できます。この関数は、データをワイドフォーマットからロングフォーマットに再構築し、各行はブランチの1か月の循環データを表します。最初に「メルト」のヘルプを見てみましょう。


```python
help(pd.melt)
```

Now, let's tidy our data. We'll create a new dataframe called `df_long` and use `melt` to reshape. `melt` essentially melts down our columns into rows. 

では、データを片付けましょう。`df_long` と呼ばれる新しいデータフレームを作成し、`melt` を使用して形状を変更します。`melt` は本質的に列を行に溶かします。

```python
df_long = df.melt(id_vars=['branch', 'address', 'city', 'zip code', 'ytd', 'year'],
                    value_vars=['january', 'february', 'march', 'april', 'may', 'june', 
                                'july', 'august', 'september', 'october', 'november', 'december'],
                    var_name='month', value_name='circulation')
```

In the above code we use `id_vars` to list the columns we do not want to melt. We then identify the columns we do want to melt into rows in the `value_vars` parameter. `var_name` is the variable name for the columns that will be transformed into rows. `value_names` is the measured variable, `circulation` in our case. Let's now look at the new structure of our data.

上記のコードでは、`id_vars`を使用して、溶かしたくない列を一覧表示します。次に、`value_vars`パラメータの行に溶け込む列を特定します。`var_name`は、行に変換される列の変数名です。`value_names`は測定変数、私たちの場合は`circulation`です。では、データの新しい構造を見てみましょう。

```python
df_long
```
Table: View of the df_long table

|    | branch         | address                 | city    |   zip code |    ytd |   year | month   |   circulation |
|---:|:---------------|:------------------------|:--------|-----------:|-------:|-------:|:--------|--------------:|
|  0 | Albany Park    | 5150 N. Kimball Ave.    | Chicago |      60625 | 120059 |   2011 | january |          8427 |
|  1 | Altgeld        | 13281 S. Corliss Ave.   | Chicago |      60827 |   9611 |   2011 | january |          1258 |
|  2 | Archer Heights | 5055 S. Archer Ave.     | Chicago |      60632 | 101951 |   2011 | january |          8104 |
|  3 | Austin         | 5615 W. Race Ave.       | Chicago |      60644 |  25527 |   2011 | january |          1755 |
|  4 | Austin-Irving  | 6100 W. Irving Park Rd. | Chicago |      60634 | 165634 |   2011 | january |         12593 |
|  ... | ...  | ... | ... | ... | ... |   ... | ... | ... |
| 12031 | Woodson Regional          | 9525 S. Halsted St. | Chicago |      60628 |  105925 |   2014 | december |          7748 |
| 12032 | Wrightwood-Ashburn        | 8530 S. Kedzie Ave. | Chicago |      60652 |   36329 |   2014 | december |          2959 |
| 12033 | Downloadable Media        | nan                 | nan     |        nan |  689961 |   2014 | december |         71276 |
| 12034 | Renewals - Online         | nan                 | nan     |        nan | 2792631 |   2014 | december |        265531 |
| 12035 | Talking Books and Braille | nan                 | nan     |        nan |  133681 |   2014 | december |         10277 |

For this episode, let's focus on branches and not `Renewals - Online`, `Renewals - Auto`, `Downloadable Media`. We can remove an individual one like so: 

このエピソードでは、「Renewals - Online」、「Renewals - Auto」、「Downloadable Media」ではなく、ブランチに焦点を当てましょう。私たちは、このように個々のものを削除することができます:

```python
df_long = df_long[df_long['branch'] != 'Downloadable Media']
```

Ok let's look at the branches now: 

さて、今から枝を見てみましょう。

```python
df_long['branch'].unique()
```

```output
    array(['Albany Park', 'Altgeld', 'Archer Heights', 'Austin',
           'Austin-Irving', 'Avalon', 'Back of the Yards', 'Beverly',
           'Bezazian', 'Blackstone', 'Brainerd', 'Brighton Park',
           'Bucktown-Wicker Park', 'Budlong Woods', 'Canaryville',
           'Chicago Bee', 'Chicago Lawn', 'Chinatown', 'Clearing', 'Coleman',
           'Daley, Richard J. - Bridgeport', 'Daley, Richard M. - W Humboldt',
           'Douglass', 'Dunning', 'Edgebrook', 'Edgewater', 'Gage Park',
           'Galewood-Mont Clare', 'Garfield Ridge', 'Greater Grand Crossing',
           'Hall', 'Harold Washington Library Center', 'Hegewisch',
           'Humboldt Park', 'Independence', 'Jefferson Park', 'Jeffery Manor',
           'Kelly', 'King', 'Legler Regional', 'Lincoln Belmont',
           'Lincoln Park', 'Little Village', 'Logan Square', 'Lozano',
           'Manning', 'Mayfair', 'McKinley Park', 'Merlo', 'Mount Greenwood',
           'Near North', 'North Austin', 'North Pulaski', 'Northtown',
           'Oriole Park', 'Portage-Cragin', 'Pullman', 'Roden', 'Rogers Park',
           'Roosevelt', 'Scottsdale', 'Sherman Park', 'South Chicago',
           'South Shore', 'Sulzer Regional', 'Thurgood Marshall', 'Toman',
           'Uptown', 'Vodak-East Side', 'Walker', 'Water Works',
           'West Belmont', 'West Chicago Avenue', 'West Englewood',
           'West Lawn', 'West Pullman', 'West Town', 'Whitney M. Young, Jr.',
           'Woodson Regional', 'Wrightwood-Ashburn', 'Renewals - Online',
           'Talking Books and Braille', 'Renewals - Itivia',
           'Renewals - Auto', 'Renewals - Phone', 'Little Italy', 'West Loop'],
          dtype=object)

```

What if we want to remove multiple ones at once? To do this we can introduce a handy function called `isin`. It tests if elements in a list are present in the dataframe. In the below code, this will return `True` when the list element is present in our branch column. We combine this with the `~` operator to negate the expression and remove those rows.

一度に複数のものを削除したい場合はどうなりますか?これを行うには、`isin`と呼ばれる便利な関数を導入することができます。リスト内の要素がデータフレームに存在するかどうかをテストします。以下のコードでは、リスト要素がブランチ列に存在する場合、これは「True」を返します。これを「~」演算子と組み合わせて、式を無効にし、それらの行を削除します。


```python
df_long = df_long[~df_long['branch'].isin(["Renewals - Online", "Renewals - Auto", 'Renewals - Itivia',
       'Renewals - Phone', 'Talking Books and Braille'])]
df_long
```

Table: df_long after removing rows

|    | branch         | address                 | city    |   zip code |    ytd |   year | month   |   circulation |
|---:|:---------------|:------------------------|:--------|-----------:|-------:|-------:|:--------|--------------:|
|  0 | Albany Park    | 5150 N. Kimball Ave.    | Chicago |      60625 | 120059 |   2011 | january |          8427 |
|  1 | Altgeld        | 13281 S. Corliss Ave.   | Chicago |      60827 |   9611 |   2011 | january |          1258 |
|  2 | Archer Heights | 5055 S. Archer Ave.     | Chicago |      60632 | 101951 |   2011 | january |          8104 |
|  3 | Austin         | 5615 W. Race Ave.       | Chicago |      60644 |  25527 |   2011 | january |          1755 |
|  4 | Austin-Irving  | 6100 W. Irving Park Rd. | Chicago |      60634 | 165634 |   2011 | january |         12593 |
|  ... | ...  | ... | ... | ... | ... |   ... | ... | ... |
| 12031 | Woodson Regional          | 9525 S. Halsted St. | Chicago |      60628 |  105925 |   2014 | december |          7748 |
| 12032 | Wrightwood-Ashburn        | 8530 S. Kedzie Ave. | Chicago |      60652 |   36329 |   2014 | december |          2959 |
| 12033 | Downloadable Media        | nan                 | nan     |        nan |  689961 |   2014 | december |         71276 |
| 12034 | Renewals - Online         | nan                 | nan     |        nan | 2792631 |   2014 | december |        265531 |
| 12035 | Talking Books and Braille | nan                 | nan     |        nan |  133681 |   2014 | december |         10277 |
 | 12028 | West Pullman          | 830 W. 119th St.     | Chicago |      60643 |  30407 |   2014 | december |          2391 || 12029 | West Town             | 1625 W. Chicago Ave. | Chicago |      60622 |  92772 |   2014 | december |          6879 || 12030 | Whitney M. Young, Jr. | 7901 S. King Dr.     | Chicago |      60619 |  31993 |   2014 | december |          2334 || 12031 | Woodson Regional      | 9525 S. Halsted St.  | Chicago |      60628 | 105925 |   2014 | december |          7748 || 12032 | Wrightwood-Ashburn    | 8530 S. Kedzie Ave.  | Chicago |      60652 |  36329 |   2014 | december |          2959 |

```python
df_long['branch'].unique()
```

```output
    array(['Albany Park', 'Altgeld', 'Archer Heights', 'Austin',
           'Austin-Irving', 'Avalon', 'Back of the Yards', 'Beverly',
           'Bezazian', 'Blackstone', 'Brainerd', 'Brighton Park',
           'Bucktown-Wicker Park', 'Budlong Woods', 'Canaryville',
           'Chicago Bee', 'Chicago Lawn', 'Chinatown', 'Clearing', 'Coleman',
           'Daley, Richard J. - Bridgeport', 'Daley, Richard M. - W Humboldt',
           'Douglass', 'Dunning', 'Edgebrook', 'Edgewater', 'Gage Park',
           'Galewood-Mont Clare', 'Garfield Ridge', 'Greater Grand Crossing',
           'Hall', 'Harold Washington Library Center', 'Hegewisch',
           'Humboldt Park', 'Independence', 'Jefferson Park', 'Jeffery Manor',
           'Kelly', 'King', 'Legler Regional', 'Lincoln Belmont',
           'Lincoln Park', 'Little Village', 'Logan Square', 'Lozano',
           'Manning', 'Mayfair', 'McKinley Park', 'Merlo', 'Mount Greenwood',
           'Near North', 'North Austin', 'North Pulaski', 'Northtown',
           'Oriole Park', 'Portage-Cragin', 'Pullman', 'Roden', 'Rogers Park',
           'Roosevelt', 'Scottsdale', 'Sherman Park', 'South Chicago',
           'South Shore', 'Sulzer Regional', 'Thurgood Marshall', 'Toman',
           'Uptown', 'Vodak-East Side', 'Walker', 'Water Works',
           'West Belmont', 'West Chicago Avenue', 'West Englewood',
           'West Lawn', 'West Pullman', 'West Town', 'Whitney M. Young, Jr.',
           'Woodson Regional', 'Wrightwood-Ashburn', 'Little Italy',
           'West Loop'], dtype=object)

```

Alright! Now that we have the data tidied what can we do with it? Let's look at which branches circulated over 10,000 items in any given month. We can filter the `df_long` DataFrame to only show rows that have a number greater than 10,000 in the `circulation` column.

よし！データを整頓したので、それで何ができますか？どの支店が特定の月に10,000以上のアイテムを流通させたかを見てみましょう。`df_long` DataFrameをフィルタリングして、`circulation`列に10,000を超える数値を持つ行のみを表示できます。

```python
df_long[df_long['circulation'] > 10000]
```
Table: df_long rows with circulation greater than 10,000

|    | branch               | address                 | city    |   zip code |    ytd |   year | month   |   circulation |
|---:|:---------------------|:------------------------|:--------|-----------:|-------:|-------:|:--------|--------------:|
|  4 | Austin-Irving        | 6100 W. Irving Park Rd. | Chicago |      60634 | 165634 |   2011 | january |         12593 |
| 12 | Bucktown-Wicker Park | 1701 N. Milwaukee Ave.  | Chicago |      60647 | 173396 |   2011 | january |         13113 |
| 13 | Budlong Woods        | 5630 N. Lincoln Ave.    | Chicago |      60659 | 160271 |   2011 | january |         12841 |
| 17 | Chinatown            | 2353 S. Wentworth Ave.  | Chicago |      60616 | 158449 |   2011 | january |         14027 |
| 24 | Edgebrook            | 5331 W. Devon Ave.      | Chicago |      60646 | 129288 |   2011 | january |         10231 |
| ... | ...  | ...      | ... |      ... | ... |   ... | ... |         ... |
| 11978 | Edgewater                        | 1210 W. Elmdale Ave. | Chicago |      60660 | 194415 |   2014 | december |         15132 |
| 11984 | Harold Washington Library Center | 400 S. State St.     | Chicago |      60605 | 755189 |   2014 | december |         55067 |
| 11993 | Lincoln Belmont                  | 1659 W. Melrose St.  | Chicago |      60657 | 164597 |   2014 | december |         11857 |
| 12011 | Rogers Park                      | 6907 N. Clark St.    | Chicago |      60626 | 136193 |   2014 | december |         10293 |
| 12017 | Sulzer Regional                  | 4455 N. Lincoln Ave. | Chicago |      60625 | 490667 |   2014 | december |         34266 |

We can look at specific columns: 

特定の列を見ることができます。

```python
df_long[['branch', 'circulation']]
```

Table: Two columns from df_long

|    | branch         |   circulation |
|---:|:---------------|--------------:|
|  0 | Albany Park    |          8427 |
|  1 | Altgeld        |          1258 |
|  2 | Archer Heights |          8104 |
|  3 | Austin         |          1755 |
|  4 | Austin-Irving  |         12593 |
|  ... | ...  |        ... |
| 12028 | West Pullman          |          2391 |
| 12029 | West Town             |          6879 |
| 12030 | Whitney M. Young, Jr. |          2334 |
| 12031 | Woodson Regional      |          7748 |
| 12032 | Wrightwood-Ashburn    |          2959 |

We can sort our table using `.sort_values()`: 

`.sort_values()`を使用してテーブルを並べ替えることができます。

```python
df_long.sort_values('circulation', ascending=False)
```

Table: Sorting df_long by highest circulation

|      | branch                           | address          | city    |   zip code |    ytd |   year | month   |   circulation |
|-----:|:---------------------------------|:-----------------|:--------|-----------:|-------:|-------:|:--------|--------------:|
| 2037 | Harold Washington Library Center | 400 S. State St. | Chicago |      60605 | 966720 |   2011 | march   |         89122 |
| 3040 | Harold Washington Library Center | 400 S. State St. | Chicago |      60605 | 966720 |   2011 | april   |         88527 |
| 3541 | Harold Washington Library Center | 400 S. State St. | Chicago |      60605 | 937649 |   2012 | april   |         87689 |
| 7052 | Harold Washington Library Center | 400 S. State St. | Chicago |      60605 | 966720 |   2011 | august  |         85193 |
| 2538 | Harold Washington Library Center | 400 S. State St. | Chicago |      60605 | 937649 |   2012 | march   |         84255 |
| ... | ... | ... |... |      ... |... |   ... |...   |         ... |
| 10511 | South Shore           | 2505 E. 73rd St.     | Chicago |      60649 |  2571 |   2019 | november  |             0 |
|  8436 | Whitney M. Young, Jr. | nan                  | nan     |        nan |     4 |   2018 | september |             0 |
|  5549 | Humboldt Park         | 1605 N. Troy St.     | Chicago |      60647 | 15947 |   2012 | june      |             0 |
|  5599 | Albany Park           | 5150 N. Kimball Ave. | Chicago |      60625 |   572 |   2013 | june      |             0 |
|  2332 | Galewood-Mont Clare   | 6871 W. Belden Ave.  | Chicago |      60707 |     0 |   2022 | march     |             0 |

What if we want to tally up the total circulation for each branch over all years and also see the mean circulation? 

長年にわたる各支店の総循環量を集計し、平均循環量も見たい場合はどうなりますか？


```python
df_long.groupby('branch')['circulation'].agg(total_circulation='sum', mean_circulation='mean')
```
     
Table: df_long aggregated by circulation sums and means
     
| branch         |   total_circulation |   mean_circulation |
|:---------------|--------------------:|-------------------:|
| Albany Park    |         1024714 |           7116.07  |
| Altgeld        |     68358           |            474.708 |
| Archer Heights |    803014           |           5576.49  |
| Austin         |    200107           |           1389.63  |
| Austin-Irving  |         1359700  |           9442.36  |
| ...  |         ...  |           ...  |
| West Pullman          |              295327 |            2050.88 |
| West Town             |              922876 |            6408.86 |
| Whitney M. Young, Jr. |              259680 |            1803.33 |
| Woodson Regional      |              823793 |            5720.78 |
| Wrightwood-Ashburn    |              302285 |            2099.2  |

1. `df.groupby('branch')`: This groups the data by the 'branch' column so that all entries in the DataFrame with the same library branch are grouped together. (This is similar to the SQL `GROUP BY` statement or the `group_by` function in `dplyr` in R.)
2. `['circulation']`: After grouping the data by branch, this specifies that subsequent operations should be performed on the 'circulation' column.
3. `.agg(...)`: The `agg` function is used to apply one or more aggregation operations to the grouped data. Inside the `agg` function:

1. `df.groupby('branch')`: これは、同じライブラリブランチを持つDataFrame内のすべてのエントリがグループ化されるように、「ブランチ」列でデータをグループ化します。(これは、SQL `GROUP BY` ステートメントまたは R の `dplyr` の `group_by` 関数に似ています。)

2. `['circulation']`: データをブランチごとにグループ化した後、これは後続の操作を「circulation」列で実行する必要があることを指定します。

3.`.agg(...)`: `agg`関数は、グループ化されたデータに1つ以上の集計操作を適用するために使用されます。`agg`関数の内部:
     
     
     - `total_circulation='sum'`: This creates a new column named 'total_circulation' where each entry is the sum of 'circulation' for that branch. It totals up all circulation figures within each branch.

- `total_circulation='sum'`: これにより、「total_circulation」という名前の新しい列が作成され、各エントリはそのブランチの「circulation」の合計です。各支店内のすべての流通数値を合計します。
     
     - `mean_circulation='mean'`: This creates a new column named 'mean_circulation' where each entry is the average 'circulation' for that branch. It calculates the mean circulation figures for each branch.

- `mean_circulation='mean'`: これにより、各エントリがそのブランチの平均「循環」である「mean_circulation」という名前の新しい列が作成されます。各支店の平均循環数を計算します。
     
If we want to group by more than one variable, we can list those column names in the `.groupby()` function.  

複数の変数でグループ化したい場合は、それらの列名を `.groupby()` 関数に一覧表示できます。

```python
df_long.groupby(['branch', 'month'])['circulation'].agg(['sum', 'mean'])
```

Table: df_long sums and means grouped by multiple columns

|   branch      |    month                |   sum |    mean |
|:----------------------------|------:|--------:|
| Albany Park | april    | 79599 | 6633.25 |
| | august   | 91416 | 7618    |
| |december | 77849 | 6487.42 |
| |february | 76747 | 6395.58 |
| |january  | 85952 | 7162.67 |
| ...| ...  | ... | ... |
| Wrightwood-Ashburn| march     | 25817 | 2151.42 |
| | may      | 22049 | 1837.42 |
| |november  | 24124 | 2010.33 |
| |october   | 27345 | 2278.75 |
| |september | 25692 | 2141    |


:::::::::::::::::::::::::::::::::::::::: keypoints

- In tidy data each variable forms a column, each observation forms a row, and each type of observational unit forms a table.
-  Using pandas for data manipulation to reshape data is fundamental for preparing data for analysis.
- 整頓されたデータでは、各変数は列を形成し、各観測は行を形成し、各タイプの観測単位はテーブルを形成します。

- データ操作にパンダを使用してデータを再構築することは、分析のためのデータを準備するための基本です。
::::::::::::::::::::::::::::::::::::::::::::::::::
