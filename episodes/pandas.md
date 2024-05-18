---
title: Using Pandas
タイトル: 8. パンダの使用
teaching: 20
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Select specific columns and rows from pandas DataFrames.
- Use pandas methods to calculate sums and means, and to display unique items.
- Sort DataFrame columns (pandas series).
- Save a DataFrame as a CSV or pickle file.

- pandas DataFramesから特定の列と行を選択します。

- パンダメソッドを使用して、合計と手段を計算し、ユニークなアイテムを表示します。

- DataFrame列(パンダシリーズ)を並べ替えます。

- DataFrameをCSVまたはピクルスファイルとして保存します。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I work with subsets of data in a pandas DataFrame?
- How can I run summary statistics and sort columns of a DataFrame? 
- How can I save DataFrames to other file formats?
- pandas DataFrameでデータのサブセットを操作するにはどうすればよいですか?

- 要約統計を実行し、DataFrameの列を並べ替えるにはどうすればよいですか?

- DataFramesを他のファイル形式に保存するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Pinpoint specific rows and columns in a DataFrame
## DataFrameで特定の行と列をピンポイントする

If you don't already have all of the CSV files loaded into a DataFrame, let's do that now: 

すべてのCSVファイルがまだDataFrameにロードされていない場合は、今すぐ実行しましょう。

```python
import glob
import pandas as pd

dfs = [] 

for csv in glob.glob('data/*.csv'):
    data = pd.read_csv(csv)
    dfs.append(data)

df = pd.concat(dfs, ignore_index=True)
df.head()
```

### Use `tail()` to look at the end of the DataFrame
### `tail()`を使用してDataFrameの末尾を見る

We've seen how to look at the first rows in your DataFrame using `.head()`. You can use `.tail()` to look at the final rows. You can also pass the number of rows you'd like to view as an argument for `.head()` and `.tail()` in case the the default of five rows doesn't work for you.

`.head()`を使用してDataFrameの最初の行を見る方法を見てきました。`.tail()`を使用して、最後の行を見ることができます。デフォルトの 5 行が機能しない場合に備えて、`.head()` と `.tail()` の引数として表示する行数を渡すこともできます。

```python
df.tail(10)
```

### Slicing a DataFrame
### データフレームのスライス

We can use the same slicing syntax that we used for strings and lists to look at a specific range of rows in a DataFrame. 

文字列やリストに使用したのと同じスライス構文を使用して、DataFrame内の特定の範囲の行を見ることができます。

```python
df[50:60] #look at rows 50 to 59
```

### Look at specific columns
### 特定の列を見る

To work specifically with one column of a DataFrame we can use a similar syntax, but refer to the name the column of interest. 

DataFrameの1つの列で具体的に作業するには、同様の構文を使用できますが、関心のある列の名前を参照してください。

```python
df['year'] #look at the year column
```
```output
0       2011
1       2011
2       2011
3       2011
4       2011
        ... 
998     2014
999     2014
1000    2014
1001    2014
1002    2014
Name: year, Length: 1003, dtype: int64
```

We can add a second square bracket after a column name to refer to specific row indices, either on their own, or using slices to look at ranges.

列名の後に2番目の角括弧を追加して、特定の行インデックスを参照するか、スライスを使用して範囲を見ることができます。

```python
print(f"first row: {df['year'][0]}") #use double quotes around your fstring if it contains single quotes
print('rows 100 to 102:') #adding a new print statement to create a new line
print(df['year'][100:103])
```
```output
first row: 2011
rows 100 to 102:
100    2016
101    2016
102    2016
Name: year, dtype: int64
```

Columns display differently in our notebook since a column is a different type of object than a full DataFrame. 

列は完全なDataFrameとは異なるタイプのオブジェクトであるため、ノートブックでは列の表示が異なります。

```python
type(df['year'])
```
```output
pandas.core.series.Series
```

## Summary statistics on columns
## 列の要約統計

A pandas Series is a one-dimensional array, like a column in a spreadsheet, while a pandas DataFrame is a two-dimensional tabular data structure with labeled axes, similar to a spreadsheet. One of the advantages of pandas is that we can use built-in functions like `max()`, `min()`, `mean()`, and `sum()` to provide summary statistics across Series such as columns. Since it can be difficult to get a sense of the range of data in a large DataFrame by looking over the whole thing manually, these functions can help us understand our dataset quickly and ask specific questions. 

パンダシリーズはスプレッドシートの列のような1次元配列であり、パンダデータフレームはスプレッドシートに似た、ラベル付きの軸を持つ2次元の表形式のデータ構造です。パンダの利点の1つは、`max()`、`min()`、`mean()`、`sum()`などの組み込み関数を使用して、列などのシリーズ全体の要約統計を提供できることです。全体を手動で調べることで、大規模なDataFrameのデータ範囲を理解するのは難しい可能性があるため、これらの機能は、データセットをすばやく理解し、特定の質問をするのに役立ちます。

If we wanted to know the range of years covered in this data, for example, we can look at the maximum and minimum values in the `year` column. 

たとえば、このデータでカバーされている年の範囲を知りたい場合は、「年」列の最大値と最小値を見ることができます。

```python
print(f"max year: {df['year'].max()}")
print(f"min year: {df['year'].min()}")
```
```output
max year: 2022
min year: 2011
```

### Summarize columns that hold string objects
### 文字列オブジェクトを保持する列を要約する

We might also want to quickly understand the range of values in columns that contain strings, the `branch` column, for example. We can look at a range of values, but it's hard to tell how many different branches are present in the dataset this way.

また、文字列を含む列、たとえば「ブランチ」列の値の範囲をすばやく理解することもできます。値の範囲を見ることができますが、このようにデータセットにいくつの異なるブランチが存在するかを見分けるのは難しいです。


```python
df['branch']
```

```output
0                     Albany Park
1                         Altgeld
2                  Archer Heights
3                          Austin
4                   Austin-Irving
                  ...            
998              Woodson Regional
999            Wrightwood-Ashburn
1000           Downloadable Media
1001            Renewals - Online
1002    Talking Books and Braille
Name: branch, Length: 1003, dtype: object
```

We can use the `.unique()` function to output an array (like a list) of all of the unique values in the `branch` column, and the `.nunique()` function to tell us how many unique values are present.

`.unique()`関数を使用して、`branch`列内のすべての一意の値の配列(リストなど)を出力し、`.nunique()`関数を使用して、存在する一意の値の数を伝えることができます。


```python
print(f"Number of unique branches: {df['branch'].nunique()}")
print(df['branch'].unique())
```
```output
Number of unique branches: 88
['Albany Park', 'Altgeld', 'Archer Heights', 'Austin',
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
       'Talking Books and Braille', 'Downloadable Media',
       'Renewals - Itivia', 'Renewals - Auto', 'Renewals - Phone',
       'Little Italy', 'West Loop']
```

## Use .groupby() to analyze subsets of data
## .groupby() を使用してデータのサブセットを分析する

A reasonable question to ask of the library usage data might be to see which branch library has seen the most checkouts over this ten + year period. We can use `.groupby()` to create subsets of data based on the values in specific columns. For example, let's group our data by branch name, and then look at the `ytd` column to see which branch has the highest usage. `.groupby()` takes a column name as its argument and then for each group we can sum the `ytd` columns using `.sum()`.

図書館の使用状況データを尋ねる合理的な質問は、この10年以上の間にどのブランチライブラリが最も多くのチェックアウトを見たかを確認することかもしれません。`.groupby()`を使用して、特定の列の値に基づいてデータのサブセットを作成できます。たとえば、ブランチ名でデータをグループ化し、「ytd」列を見て、どのブランチの使用率が最も高いかを確認します。`.groupby()` は列名を引数として取り、グループごとに `.sum()` を使用して `ytd` 列を合計できます。


```python
df.groupby('branch')['ytd'].sum()
```

```output
branch
Albany Park              1024714
Altgeld                    68358
Archer Heights            803014
Austin                    200107
Austin-Irving            1359700
                          ...   
West Pullman              295327
West Town                 922876
Whitney M. Young, Jr.     259680
Woodson Regional          823793
Wrightwood-Ashburn        302285
Name: ytd, Length: 88, dtype: int64
```

### Sort pandas series using .sort_values()
### .sort_values() を使用してパンダシリーズをソートする

The output for code above is another pandas series object. Let's save the output to a new variable so we can then apply the `.sort_values()` method which allows us to view the branches with the *most* usage. The `ascending` parameter for `.sort_values()` takes `True` or `False`. We want to pass `False` so that we sort from the highest values down...

上記のコードの出力は、別のパンダシリーズオブジェクトです。出力を新しい変数に保存して、`.sort_values()`メソッドを適用して、*最も*使用法でブランチを表示できるようにします。`.sort_values()` の `ascending` パラメータは `True` または `False` を取ります。「False」を渡して、最高値からソートしたい...

```python
circ_by_branch = df.groupby('branch')['ytd'].sum()
circ_by_branch.sort_values(ascending=False).head(10)
```
```output
branch
Renewals - Online                   28441560
Renewals - Auto                     21188737
Downloadable Media                  15709651
Harold Washington Library Center     7498041
Sulzer Regional                      5089225
Lincoln Belmont                      1850964
Edgewater                            1668693
Logan Square                         1539816
Rogers Park                          1515964
Bucktown-Wicker Park                 1456669
Name: ytd, dtype: int64
```
Now we have a list of the branches (including some checkout types) with the highest number of uses across the whole dataset. 
これで、データセット全体で使用回数が最も多いブランチ(一部のチェックアウトタイプを含む)のリストがあります。

We can pass multiple columns to `groupby()` to subset the data even further and breakdown the highest usage per year and branch. To do that, we need to pass the column names as a list. We can also chain together many methods into a single line of code. 

複数の列を `groupby()` に渡して、データをさらにサブセットし、年間とブランチあたりの最高使用量を分解することができます。そのためには、列名をリストとして渡す必要があります。また、多くのメソッドを1行のコードにまとめることもできます。

```python
circ_by_year_branch = df.groupby(['year', 'branch'])['ytd'].sum().sort_values(ascending=False)
circ_by_year_branch.head(5)
```
```output
year  branch           
2020  Renewals - Auto      8222810
2021  Renewals - Auto      6629348
2022  Renewals - Auto      6336579
2019  Renewals - Online    4821180
2018  Renewals - Online    4006963
Name: ytd, dtype: int64
```

## Use .iloc[] and .loc[] to select DataFrame locations.
## .iloc[] と .loc[] を使用して、DataFrame の場所を選択します。

You can point to specific locations in a DataFrame using two-dimensional numerical indexes with `.iloc[]`.
`.iloc[]`の2次元数値インデックスを使用して、DataFrame内の特定の場所を指すことができます。


```python
# print values in the 1st and 2nd to last columns in the first row
# '\n' prints a linebreak
print(f"Branch: {df.iloc[0,0]} \nYTD circ: {df.iloc[0,-2]}")

```

```output
Branch: Albany Park 
YTD circ: 120059
```

`.loc[]` uses the same structure but takes row (index) and column names instead of numerical indexes. Since our `df` rows don't have index names we would still use the default numerical index.

`.loc[]`は同じ構造を使用しますが、数値インデックスの代わりに行(インデックス)と列名を取ります。「Df」行にはインデックス名がないため、デフォルトの数値インデックスを使用します。


```python
# print the same values as above, using the column names
print(f"Branch: {df.loc[0,'branch']} \nYTD circ: {df.loc[0, 'ytd']}")

```

```output
Branch: Albany Park 
YTD circ: 120059
```

## Save DataFrames
## データフレームの保存

You might want to export the series of usage by year and branch that we just created so that you can share it with colleagues. Pandas includes a variety of methods that begin with `.to_...` that allow us to convert and export data in different ways. First, let's save our series as a DataFrame so we can view the output in a better format in our Jupyter notebook. 

同僚と共有できるように、作成したばかりの一連の使用状況を年とブランチごとにエクスポートすることをお勧めします。パンダには、さまざまな方法でデータを変換およびエクスポートできる「.to_...」で始まるさまざまな方法が含まれています。まず、Jupyterノートブックでより良い形式で出力を表示できるように、シリーズをDataFrameとして保存しましょう。


```python
circ_df = circ_by_year_branch.to_frame()
circ_df.head(5)
```

### Save to CSV
### CSVに保存

Next, let's export the new DataFrame to a CSV file so we can share it with colleagues who love spreadsheets. The `.to_csv()` method expects a string that will be the name of the file as a parameter. Make sure to add the .csv filetype to your file name. 

次に、新しいDataFrameをCSVファイルにエクスポートして、スプレッドシートを愛する同僚と共有しましょう。`.to_csv()`メソッドは、パラメータとしてファイルの名前となる文字列を期待しています。必ずファイル名に.csvファイルタイプを追加してください。

```python
circ_df.to_csv('high_usage.csv')
```
You should now see, in the JupyterLab file explorer to the left, the new CSV file. If you don't see it, you can hit the refresh icon (it looks like a spinning arrow) above the files pane. You can double-click on the CSV to preview the full spreadsheet in a new Jupyter tab.

左側のJupyterLabファイルエクスプローラに、新しいCSVファイルが表示されるはずです。表示されない場合は、ファイルペインの上にあるリフレッシュアイコン(回転する矢印のように見えます)を押すことができます。CSVをダブルクリックして、新しいJupyterタブで完全なスプレッドシートをプレビューできます。

::::::::::::::::::::::::::::::::::::::: callout
### Save pickle files
### ピクルスファイルを保存する

Working with your data in CSVs (especially via tools like Microsoft Excel) can introduce reproducibility issues. For example, you'll sometimes encounter character encoding problems, where certain characters in your dataset will no longer display properly after editing them in a spreadsheet software like Excel, and re-importing them to a pandas DataFrame. 

CSV（特にMicrosoft Excelなどのツールを介して）でデータを操作すると、再現性の問題が発生する可能性があります。たとえば、Excelなどのスプレッドシートソフトウェアで編集し、パンダDataFrameに再インポートした後、データセット内の特定の文字が正しく表示されなくなる文字エンコーディングの問題が発生することがあります。

One way to avoid issues like this is to save Python objects as [pickles](https://docs.python.org/3/library/pickle.html). Technically speaking, the Python pickle module serializes and de-serializes a Python object's structure. In practical terms, pickling allows you to store Python objects (like DataFrames, lists, etc.) efficiently and without losing or corrupting your data. 

このような問題を回避する1つの方法は、Pythonオブジェクトを[pickles](https://docs.python.org/3/library/pickle.html)として保存することです。技術的に言えば、Pythonピクルスモジュールは、Pythonオブジェクトの構造をシリアライズおよびデシリアライズします。実際には、ピクルスを使用すると、データを紛失したり破損したりすることなく、Pythonオブジェクト(DataFrame、リストなど)を効率的に保存できます。

You can save a DataFrame to pickle by using the `to_pickle()` method and using the filetype of `pkl`.

`to_pickle()`メソッドを使用し、`pkl`のファイルタイプを使用して、DataFrameをピクルスに保存できます。

```python
circ_df.to_pickle('high_usage.pkl')
```

You can only "see" the data in a pickle file by reloading it into Python. This is a great way to save a DataFrame that you created in one JupyterLab session so that you can reload it later on, or share it with a colleague who's familiar with Python. 

ピクルスファイル内のデータをPythonにリロードすることによってのみ「見る」ことができます。これは、1つのJupyterLabセッションで作成したDataFrameを保存して、後でリロードしたり、Pythonに精通している同僚と共有したりするのに最適な方法です。

```python
new_df = pd.read_pickle('high_usage.pkl')
new_df.head()
```
:::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Displaying rows and columns
## 行と列の表示

How would you use slicing and column names to select the following subsets of rows and columns from the circulation DataFrame?

スライスと列名を使用して、循環DataFrameから行と列の次のサブセットをどのように選択しますか?

1. The city column.
2. Rows 10 to 20.
3. Rows 20 to 30 from the zip code column.

1. 市のコラム。

2. 10行から20行。

3. 郵便番号の列から20行から30行。
:::::::::::::::  solution

## Solution
## 解決策

```python
#1
df['city']

#2
df[10:21]

#3 
df['zip code'][20:31]

```


:::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::  challenge

## Using loc()
## loc() を使用する

How would you use `loc()` to select rows 20 to 30 from the zip code column (the same rows as the last example in the challenge above)?

どのように`loc（）`を使用して、郵便番号の列から20〜30行を選択しますか（上記のチャレンジの最後の例と同じ行）

Tip: slices use "non-inclusive" indexing -- so require you to ask for `df[10:21]` to see row 20, but `loc()` uses inclusive indexing.

ヒント: スライスは「非包括的」インデックスを使用するため、20行目を見るには`df[10:21]`を依頼する必要がありますが、`loc()`は包括的なインデックスを使用します。

:::::::::::::::  solution

## Solution
## 解決策

```python
df.loc[20:30, 'zip code']

```
:::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Unique items
## ユニークなアイテム

How would you display:

どのように表示しますか:

1. all of the unique zip codes in the dataset?
2. the number of unique zip codes in the dataset?

1. データセット内のすべての一意の郵便番号

2. データセット内の一意の郵便番号の数


:::::::::::::::  solution

## Solution
## 解決策

```python

#1
df['zip code'].unique()

#2
df['zip code'].nunique()

```
:::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Summary statistics and groupby()
## 要約統計とgroupby()

We can apply `mean()` to pandas series' in the same way we used `sum()`, `min()`, and `max()` above. How would you display the following? 

上記の `sum()`、`min()`、および `max()`を使用したのと同じ方法で、パンダシリーズに `mean()`を適用できます。以下をどのように表示しますか？

1. the mean number of ytd checkouts grouped by zip code?
2. the mean number of ytd checkouts grouped by zip code, and sorted from smallest to largest?

1. 郵便番号でグループ化されたytdチェックアウトの平均数

2. 郵便番号でグループ化され、最小から最大にソートされたytdチェックアウトの平均数

:::::::::::::::  solution

## Solution
## 解決策

```python
#1
df.groupby('zip code')['ytd'].mean()

#2
df.groupby('zip code')['ytd'].mean().sort_values()

```
:::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::: keypoints

- Use builtin methods `.sum()`, `.mean()`, `unique()`, and `nunique()` to explore summary statistics on the rows and colums in your DataFrame.
- Use `.groupby()` to work with subsets of your dataset.
- Sort pandas series with `.sort_values()`.
- Use `.loc()` and `.iloc()` to pinpoint specific locations in Pandas DataFrames.
- Save DataFrames to CSV and pickle files using `.to_csv()` and `.to_pickle()`.
- 組み込みメソッド `.sum()`、`.mean()`、`unique()`、および `nunique()` を使用して、DataFrame の行と列の要約統計を調べます。

- `.groupby()`を使用して、データセットのサブセットを操作します。

- パンダシリーズを`.sort_values()`で並べ替えます。

- `.loc()`と`.iloc()`を使用して、Pandas DataFramesの特定の場所を特定します。

- DataFramesをCSVに保存し、`.to_csv()`と`.to_pickle()`を使用してファイルをピクルスします。
::::::::::::::::::::::::::::::::::::::::::::::::::


