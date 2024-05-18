---
title: Libraries & Pandas
タイトル: 5. 図書館とパンダ
teaching: 20
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explain what Python libraries and modules are.
- Write Python code that imports and uses modules from Python's standard library.
- Find and read documentation for standard libraries.
- Import the pandas library.
- Use pandas to load a CSV file as a data set.
- Get some basic information about a pandas DataFrame.
- Pythonライブラリとモジュールとは何かを説明してください。

- Pythonの標準ライブラリからモジュールをインポートして使用するPythonコードを書く。

- 標準ライブラリのドキュメントを見つけて読む。

- パンダライブラリをインポートします。

- パンダを使用して、CSVファイルをデータセットとしてロードします。

- pandas DataFrameに関する基本的な情報を入手してください。
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I extend the capabilities of Python?
- How can I use Python code that other people have written?
- How can I read tabular data?
- Pythonの機能を拡張するにはどうすればよいですか?

- 他の人が書いたPythonコードを使用するにはどうすればよいですか?

- 表形式のデータを読むにはどうすればよいですか?
::::::::::::::::::::::::::::::::::::::::::::::::::

## Python libraries are powerful collections of tools.
## Pythonライブラリは強力なツールのコレクションです。

A *Python library* is a collection of files (called *modules*) that contains functions that you can use in your programs. Some libraries (also referred to as packages) contain standard data values or language resources that you can reference in your code. So far, we have used the Python [standard library][stdlib], which is an extensive suite of built-in modules. You can find additional libraries from [PyPI][pypi] (the Python Package Index), though you'll often find references to useful libraries as you're reading tutorials or trying to solve specific programming problems. Some popular libraries for working with data in library fields are:

*Pythonライブラリ*は、プログラムで使用できる関数を含むファイル(*モジュール*と呼ばれる)のコレクションです。一部のライブラリ(パッケージとも呼ばれる)には、コードで参照できる標準データ値または言語リソースが含まれています。これまでのところ、組み込みモジュールの広範なスイートであるPython[標準ライブラリ][stdlib]を使用してきました。[PyPI][pypi](Pythonパッケージインデックス)から追加のライブラリを見つけることができますが、チュートリアルを読んだり、特定のプログラミングの問題を解決しようとすると、便利なライブラリへの参照が見つかることがよくあります。ライブラリフィールドでデータを操作するためのいくつかの一般的なライブラリは次のとおりです。

- [Pandas](https://pandas.pydata.org/) - tabular data analysis tool.
- [Pymarc](https://pypi.org/project/pymarc/) - for working with bibliographic data encoded in MARC21.
- [Matplotlib](https://matplotlib.org/) - data visualization tools.
- [BeautifulSoup](https://pypi.org/project/beautifulsoup4/) - for parsing HTML and XML documents.
- [Requests](https://pypi.org/project/requests/) - for making HTTP requests (e.g., for web scraping, using APIs)
- [Scikit-learn](https://scikit-learn.org/stable/) - machine learning tools for predictive data analysis.
- [NumPy](https://numpy.org/) - numerical computing tools such as mathematical functions and random number generators.
- [パンダ](https://pandas.pydata.org/) - 表形式のデータ分析ツール。

- [Pymarc](https://pypi.org/project/pymarc/) - MARC21でエンコードされた書誌データを操作するため。

- [Matplotlib](https://matplotlib.org/) - データ視覚化ツール。

- [BeautifulSoup](https://pypi.org/project/beautifulsoup4/) - HTMLおよびXMLドキュメントの解析用。

- [リクエスト](https://pypi.org/project/requests/) - HTTPリクエストの作成（Webスクレイピング、APIの使用など）

- [Scikit-learn](https://scikit-learn.org/stable/) - 予測データ分析のための機械学習ツール。

- [NumPy](https://numpy.org/) - 数学関数や乱数発生器などの数値計算ツール。

## You must import a library or module before using it.
## 使用する前にライブラリまたはモジュールをインポートする必要があります。

Use `import` to load a library into a program's memory. Then you can refer to things from the library as `library_name.function`. Let's import and use the `string` library to generate a list of lowercase ASCII letters and to change the case of a text string:

「Import」を使用して、ライブラリをプログラムのメモリにロードします。その後、ライブラリのものを `library_name.function` として参照できます。「文字列」ライブラリをインポートして使用して、小文字のASCII文字のリストを生成し、テキスト文字列の大文字小文字を変更しましょう。


```python
import string

print(f'The lower ascii letters are {string.ascii_lowercase}')
print(string.capwords('capitalise this sentence please.'))
```

```output
The lower ascii letters are abcdefghijklmnopqrstuvwxyz
Capitalise This Sentence Please.
```

:::::::::::::::::::::::::::::::::::::::::  callout

## Dot notation
## ドット表記

We introduced Python dot notation when we looked at methods like `list_name.append()`. We can use the same syntax when we call functions of a specific Python library, such as `string.capwords()`. In fact, this dot notation is common in Python, and can refer to relationships between different types of Python objects. Remember that it is always the case that the object to the right of the dot is a part of the larger object to the left. If we expressed capitals of countries using this syntax, for example, we would say, `Brazil.São_Paulo()` or `Japan.Tokyo()`.

`list_name.append()`のようなメソッドを見たときに、Pythonのドット表記を導入しました。`string.capwords()` など、特定の Python ライブラリの関数を呼び出すときに、同じ構文を使用できます。実際、このドット表記はPythonでは一般的であり、異なるタイプのPythonオブジェクト間の関係を参照することができます。ドットの右側のオブジェクトは、左側のより大きなオブジェクトの一部であることを覚えておいてください。たとえば、この構文を使用して国の首都を表現した場合、`Brazil.São_Paulo()`または`Japan.Tokyo()`と言うでしょう。

::::::::::::::::::::::::::::::::::::::::::::::::::

## Use `help` to learn about the contents of a library module.
## `help`を使用して、ライブラリモジュールの内容について学びます。

The `help()` function can tell us more about a module in a library, including more information about its functions and/or variables.

`help()`関数は、その関数や変数に関する詳細情報を含め、ライブラリ内のモジュールの詳細を伝えることができます。

```python
help(string)
```

```output
Help on module string:

NAME
    string - A collection of string constants.

MODULE REFERENCE
    https://docs.python.org/3.6/library/string
    
    The following documentation is automatically generated from the Python
    source files.  It may be incomplete, incorrect or include features that
    are considered implementation detail and may vary between Python
    implementations.  When in doubt, consult the module reference at the
    location listed above.

以下のドキュメントはPythonから自動的に生成されます

ソースファイル。不完全、不正確、または次のような機能が含まれている可能性があります

実装の詳細と見なされ、Pythonによって異なる場合があります

実装。疑わしい場合は、モジュールリファレンスを参照してください。

上記の場所。

DESCRIPTION
    Public module variables:
    
    whitespace -- a string containing all ASCII whitespace
    ascii_lowercase -- a string containing all ASCII lowercase letters
    ascii_uppercase -- a string containing all ASCII uppercase letters
    ascii_letters -- a string containing all ASCII letters
    digits -- a string containing all ASCII decimal digits
    hexdigits -- a string containing all ASCII hexadecimal digits
    octdigits -- a string containing all ASCII octal digits
    punctuation -- a string containing all ASCII punctuation characters
    printable -- a string containing all ASCII characters considered printable

CLASSES
    builtins.object
        Formatter
        Template
⋮ ⋮ ⋮
```

## Import specific items
## 特定のアイテムをインポートする

You can use `from ... import ...` to load specific items from a library module to save space. This also helps you write briefer code since you can refer to them directly without using the library name as a prefix everytime.

`from ... import ...` を使用して、ライブラリモジュールから特定のアイテムをロードし、スペースを節約できます。これは、毎回ライブラリ名をプレフィックスとして使用せずに直接参照できるため、より簡単なコードを書くのにも役立ちます。

```python
from string import ascii_letters

print(f'The ASCII letters are {ascii_letters}')
```

```output
The ASCII letters are abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
```
:::::::::::::::::::::::::::::::::::::::::  callout

## Module not found error
## モジュールが見つかりません エラー

Before you can import a Python library, you sometimes will need to download and install it on your machine. Anaconda comes with many of the most popular Python libraries for scientific computing applications built-in, so if you installed Anaconda for this workshop, you'll be able to import many common libraries directly. Some less common tools, like the PyMarc library, however, would need to be installed first.

Pythonライブラリをインポートする前に、マシンにダウンロードしてインストールする必要がある場合があります。Anacondaには、科学コンピューティングアプリケーション用の最も人気のあるPythonライブラリの多くが組み込まれているため、このワークショップにAnacondaをインストールすると、多くの一般的なライブラリを直接インポートできます。ただし、PyMarcライブラリなど、あまり一般的ではないツールを最初にインストールする必要があります。

```python
import pymarc
```

```error
ModuleNotFoundError: No module named 'pymarc'
```

You can find out how to install the library by looking at the documentation. [PyMarc](https://pypi.org/project/pymarc/), for example, recommends using a command line tool, `pip`, to install it. You can install with pip in a Jupyter notebook by starting the command with a percentage symbol, which allows you to run shell commands from Jupyter:

ドキュメントを見て、ライブラリのインストール方法を見つけることができます。たとえば、[PyMarc](https://pypi.org/project/pymarc/)は、コマンドラインツール「pip」を使用してインストールすることをお勧めします。Jupyterからシェルコマンドを実行できるパーセンテージ記号でコマンドを開始することで、Jupyterノートブックにpipでインストールできます。

```python
%pip install pymarc
import pymarc
```

::::::::::::::::::::::::::::::::::::::::::::::::::

## Use library aliases
## ライブラリエイリアスを使用する

You can use `import ... as ...` to give a library a short *alias* while importing it. This helps you refer to items more efficiently. 

「インポート...として...」を使用して、インポート中にライブラリに短い*エイリアス*を与えることができます。これは、アイテムをより効率的に参照するのに役立ちます。

```python
import pandas as pd
```

Many popular libraries have common aliases. For example:

多くの人気のある図書館には共通のエイリアスがあります。例えば:

- ```import pandas as pd```
- ```import numpy as np```
- ```import matplotlib as plt```

Using these common aliases can make it easier to work with existing documentation and tutorials. 

これらの一般的なエイリアスを使用すると、既存のドキュメントやチュートリアルでの作業が容易になります。

## Pandas
##パンダ

`Pandas` is a widely-used Python library for statistics using tabular data.
Essentially, it gives you access to 2-dimensional tables whose columns have names and can have different data types. We can start using pandas by reading a `Comma Separated Values` (CSV) data file with the function `pd.read_csv()`. The function `.read_csv()` expects as an argument the path to and name of the file to be read. This returns a dataframe that you can assign to a variable.

`Pandas`は、表形式のデータを使用した統計用に広く使用されているPythonライブラリです。

基本的に、列に名前があり、異なるデータ型を持つことができる2次元テーブルにアクセスできます。関数 `pd.read_csv()` を持つ `Comma Separated Values` (CSV) データファイルを読み取ることで、パンダの使用を開始できます。関数 `.read_csv()` は、引数として、読み込まれるファイルのパスと名前を期待します。これにより、変数に割り当てることができるデータフレームが返されます。

### Find your CSV files
### CSVファイルを探す

From the file browser in the left sidebar you can select the `data` folder to view the contents of the folder. If you downloaded and uncompressed the dataset correctly, you should see a series of CSV files from 2011 to 2022. If you double-click on the first file, `2011_circ.csv`, you will see a preview of the CSV file in a new tab in the main panel of JupyterLab. 

左側のサイドバーのファイルブラウザから、「データ」フォルダを選択して、フォルダの内容を表示できます。データセットを正しくダウンロードして解凍すると、2011年から2022年までの一連のCSVファイルが表示されるはずです。最初のファイル「2011_circ.csv」をダブルクリックすると、JupyterLabのメインパネルの新しいタブにCSVファイルのプレビューが表示されます。

Let's load that file into a pandas DataFrame, and save it to a new variable called `df`.

そのファイルをパンダのDataFrameにロードして、`df`という新しい変数に保存しましょう。

```python
df = pd.read_csv('data/2011_circ.csv')
print(df)
```

```output
                       branch                  address     city  zip code  \
0                 Albany Park     5150 N. Kimball Ave.  Chicago   60625.0   
1                     Altgeld    13281 S. Corliss Ave.  Chicago   60827.0   
2              Archer Heights      5055 S. Archer Ave.  Chicago   60632.0   
3                      Austin        5615 W. Race Ave.  Chicago   60644.0   
4               Austin-Irving  6100 W. Irving Park Rd.  Chicago   60634.0   
..                        ...                      ...      ...       ...   
78           Woodson Regional      9525 S. Halsted St.  Chicago   60628.0   
79         Wrightwood-Ashburn      8530 S. Kedzie Ave.  Chicago   60652.0   
80          Renewals - Online                      NaN      NaN       NaN   
81  Talking Books and Braille                      NaN      NaN       NaN   
82         Downloadable Media                      NaN      NaN       NaN   

```
:::::::::::::::::::::::::::::::::::::::::  callout

## File Not Found
## ファイルが見つかりません

Our lessons store their data files in a `data` sub-directory,
which is why the path to the file is `data/2011_circ.csv`.
If you forget to include `data/`, or if you include it but your copy of the file is somewhere else in relation to your Jupyter Notebook, you will get an error that ends with a line like this:

私たちのレッスンは、データファイルを「データ」サブディレクトリに保存します。

そのため、ファイルへのパスは「data/2011_circ.csv」です。

`data/`を含めるのを忘れた場合、またはそれを含めるが、ファイルのコピーがJupyter Notebookに関連してどこかにある場合は、次のような行で終わるエラーが発生します。

```error
FileNotFoundError: [Errno 2] No such file or directory: 'data/2011_circ.csv'
```

::::::::::::::::::::::::::::::::::::::::::::::::::

`df` is a common variable name that you'll encounter in pandas tutorials online, but in practice it's often better to use more meaningful variable names. Since we have twelve different CSVs to work with, for example, we might want to add the year to the variable name to differentiate between the datasets.

`df`は、オンラインでパンダのチュートリアルで遭遇する一般的な変数名ですが、実際には、より意味のある変数名を使用する方が良いことがよくあります。たとえば、12の異なるCSVがあるため、データセットを区別するために変数名に年を追加することをお勧めします。

Also, as seen above, the output when you print a dataframe in Jupyter isn't very easy to read. We can use `.head()` to look at just the first few rows in our dataframe formatted in a more convenient way for our Notebook.

また、上記のように、Jupyterでデータフレームを印刷するときの出力はあまり読みにくいです。`.head()`を使用して、ノートブックにとってより便利な方法でフォーマットされたデータフレームの最初の数行だけを見ることができます。

```python
df_2011 = pd.read_csv('data/2011_circ.csv')
df_2011.head()
```

## Use the `DataFrame.info()` method to find out more about a dataframe.
## `DataFrame.info()`メソッドを使用して、データフレームの詳細を確認してください。

```python
df_2011.info()
```

```output
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 83 entries, 0 to 82
Data columns (total 18 columns):
 #   Column     Non-Null Count  Dtype  
---  ------     --------------  -----  
 0   branch     83 non-null     object 
 1   address    80 non-null     object 
 2   city       80 non-null     object 
 3   zip code   80 non-null     float64
 4   january    83 non-null     int64  
 5   february   83 non-null     int64  
 6   march      83 non-null     int64  
 7   april      83 non-null     int64  
 8   may        83 non-null     int64  
 9   june       83 non-null     int64  
 10  july       83 non-null     int64  
 11  august     83 non-null     int64  
 12  september  83 non-null     int64  
 13  october    83 non-null     int64  
 14  november   83 non-null     int64  
 15  december   83 non-null     int64  
 16  ytd        83 non-null     int64  
 17  year       83 non-null     int64  
dtypes: float64(1), int64(14), object(3)
memory usage: 11.8+ KB
```

The `info()` method tells us
- we have a RangeIndex of 83, which means we have 83 rows.
- there are 18 columns, with datatypes of
  - objects (3 columns)
  - 64-bit floating point number (1 column)
  - 64-bit integers (14 columns).
- the dataframe uses 11.8 kilobytes of memory.

`info()`メソッドは私たちに教えてくれます

- RangeIndexは83です。つまり、83行があります。

- 18の列があり、データ型は

- オブジェクト(3列)

- 64ビット浮動小数点数(1列)

- 64ビット整数(14列)。

- データフレームは11.8キロバイトのメモリを使用します。

## The `DataFrame.columns` variable stores info about the dataframe's columns.
## `DataFrame.columns`変数は、データフレームの列に関する情報を保存します。

Note that this is data, *not* a method, so do not use `()` to try to call it. It helpfully gives us a list of all of the column names.

これはデータであり、メソッドではないので、`()`を使用して呼び出そうとしないでください。すべての列名のリストが記載されています。

```python
print(df_2011.columns)
```

```output
Index(['branch', 'address', 'city', 'zip code', 'january', 'february', 'march',
       'april', 'may', 'june', 'july', 'august', 'september', 'october',
       'november', 'december', 'ytd', 'year'],
      dtype='object')
```

## Use `DataFrame.describe()` to get summary statistics about data.
## `DataFrame.describe()`を使用して、データに関する要約統計を取得します。

`DataFrame.describe()` gets the summary statistics of only the columns that have numerical data. All other columns are ignored, unless you use the argument `include='all'`.

`DataFrame.describe()`は、数値データを持つ列のみの要約統計を取得します。引数 `include='all'` を使用しない限り、他のすべての列は無視されます。

```python
df_2011.describe()
```

This gives us, for example, the count, minimum, maximum, and mean values from each numeric column. In the case of the `zip code` column, this isn't helpful, but for the usage data for each month, it's a quick way to scan the range of data over the course of the year.

これにより、たとえば、各数値列のカウント、最小値、最大値、平均値が得られます。「郵便番号」列の場合、これは役に立ちませんが、毎月の使用状況データについては、年間を通してデータの範囲をスキャンする簡単な方法です。

:::::::::::::::::::::::::::::::::::::::  challenge

## Importing With Aliases
## エイリアスでインポートする

1. Fill in the blanks so that the program below prints `0123456789`.
2. Rewrite the program so that it uses `import` *without* `as`.
3. Which form do you find easier to read?


1. 以下のプログラムが「0123456789」を印刷するように空白を埋めてください。
2. `import` *without* `as` を使用するようにプログラムを書き換えます。
3. どのフォームが読みやすいと思いますか?


```python
import string as s
numbers = ____.digits
print(____)
```

:::::::::::::::  solution

## Solution
## 解決策

```python
import string as s
numbers = s.digits
print(numbers)
```

can be written as

と書くことができます

```python
import string
numbers = string.digits
print(numbers)
```

Since you just wrote the code and are familiar with it, you might actually
find the first version easier to read. But when trying to read a huge piece
of code written by someone else, or when getting back to your own huge piece
of code after several months, non-abbreviated names are often easier, expect
where there are clear abbreviation conventions.

あなたはコードを書いたばかりで、それに精通しているので、あなたは実際に

読みやすい最初のバージョンを見つけてください。しかし、巨大な作品を読もうとするとき

他の誰かによって書かれたコード、またはあなた自身の巨大な作品に戻るとき

数ヶ月後のコードの、短縮されていない名前はしばしばより簡単です、期待してください

明確な略語規則があるところ。



:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Locating the Right Module
## 適切なモジュールを見つける

Given the variables `year`, `month` and `day`, how would you generate a date in the standard iso format:

変数 `year`、`month`、`day`を考えると、標準のiso形式で日付をどのように生成しますか。

```python
year = 1971
month = 8
day = 26
```

1. Which [standard library][stdlib] module could help you?
2. Which function would you select from that module?
3. Try to write a program that uses the function.


1. どの[標準ライブラリ][stdlib]モジュールが役立ちますか?
2. そのモジュールからどの機能を選択しますか？
3. 関数を使用するプログラムを書いてみてください。


:::::::::::::::  solution

## Solution
## 解決策

The [datetime module](https://docs.python.org/3/library/datetime.html) seems like it could help you.

[Datetimeモジュール](https://docs.python.org/3/library/datetime.html)は、あなたを助けることができるようです。

You could use `date(year, month, date).isoformat()` to convert your date:

`date(year, month, date).isoformat()`を使用して日付を変換できます。

```python
import datetime

iso_date = datetime.date(year, month, day).isoformat()
print(iso_date)
```

or more compactly:

またはよりコンパクトに:

```python
import datetime

print(datetime.date(year, month, day).isoformat())
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

[stdlib]: https://docs.python.org/3/library/
[pypi]: https://pypi.org/

:::::::::: spoiler
### Is there something special about that date in library history?
###図書館の歴史の中で、その日付について何か特別なことはありますか？

According to [Washington County Cooperative Library Services](https://www.wccls.org/news/brief-history-library-catalog):
"1971, August 26 – Ohio University’s Alden Library takes computer cataloging online for the first time, building a system where libraries could electronically share catalog records over a network instead of by mailing printed cards or re-entering records in each catalog. That catalog eventually became the core of OCLC WorldCat – a shared online catalog used by libraries in 107 countries and containing 517,963,343 records."

[ワシントン郡協同図書館サービス](https://www.wccls.org/news/brief-history-library-catalog)によると:

「1971年8月26日 - オハイオ大学のオールデン図書館は、初めてコンピュータカタログをオンラインで取り、図書館が印刷されたカードを郵送したり、各カタログにレコードを再入力したりするのではなく、ネットワークを介してカタログレコードを電子的に共有できるシステムを構築します。そのカタログは最終的に、107カ国の図書館で使用され、517,963,343件のレコードを含む共有オンラインカタログであるOCLC WorldCatの中核となりました。

::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Most of the power of a programming language is in its libraries.
- A program must import a library module in order to use it.
- Use `help` to learn about the contents of a library module.
- Import specific items from a library to shorten programs.
- Create an alias for a library when importing it to shorten programs.

- プログラミング言語の力のほとんどは、そのライブラリにあります。

- プログラムを使用するには、ライブラリモジュールをインポートする必要があります。

- 「ヘルプ」を使用して、ライブラリモジュールの内容について学びます。

- ライブラリから特定のアイテムをインポートして、プログラムを短縮します。

- プログラムを短くするためにインポートするときに、ライブラリのエイリアスを作成します。

::::::::::::::::::::::::::::::::::::::::::::::::::


