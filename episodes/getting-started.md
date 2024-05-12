---
title: Getting Started
teaching: 15
exercises: 5
---

::::::::::::::::::::::::::::::::::::::: objectives

- Learners are aware of applications for Python in library and information-science work environments.
- 学習者は、図書館や情報科学の作業環境におけるPythonのアプリケーションを認識しています。
- Learners can launch JupyterLab and create a Jupyter Notebook.
- 学習者はJupyterLabを起動し、Jupyter Notebookを作成できます。

- Learners are able to navigate the JupyterLab interface.
- 学習者はJupyterLabインターフェースをナビゲートできます。
- Learners are able to write and run Python cells in a notebook.
- 学習者は、ノートブックにPythonセルを書いて実行することができます。
- Learners are able to save their code as an iPython notebook (.ipynb file).
- 学習者はコードをiPythonノートブック(.ipynbファイル)として保存できます。








::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How do I use JupyterLab?
- JupyterLabはどのように使用しますか?
- How can I run Python code in JupyterLab?
- JupyterLabでPythonコードを実行するにはどうすればよいですか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Why Python?
## なぜパイソンなのか？

Python is a popular programming language for tasks such as data collection, cleaning, and analysis. Python can help you to create reproducible workflows to accomplish repetitive tasks more efficiently. 

Pythonは、データ収集、クリーニング、分析などのタスクに一般的なプログラミング言語です。Pythonは、反復的なタスクをより効率的に達成するために、再現可能なワークフローを作成するのに役立ちます。

This lesson works with a series of CSV files of circulation data from the Chicago Public Library system to demonstrate how to use Python to clean, analyze, and visualize usage data that spans over the course of multiple years. 

このレッスンでは、シカゴ公共図書館システムからの循環データの一連のCSVファイルを使用して、Pythonを使用して、複数年にわたる使用データをクリーンアップ、分析、視覚化する方法を実演します。

:::::::::::::::::::::::::::::::::::::::  challenge
## Python in Libraries
## 図書館のPython

There are a lot of ways that library and information science folks use Python in their work. Go around the room and have helpers and co-teachers share how they have used Python.

図書館や情報科学の人々が仕事でPythonを使う方法はたくさんあります。部屋を歩き回って、ヘルパーや共同教師にPythonの使用方法を共有してもらいます。

Learners: Can you think of other ways to use Python in libraries? Do you have hopes for how you'd like to use Python in the future?

学習者：ライブラリでPythonを使用する他の方法を考えられますか？将来、Pythonをどのように使いたいか希望がありますか?

:::::::::::::::  solution

Here a few areas where you might apply Python in your work.

ここでは、あなたの仕事にPythonを適用する可能性のあるいくつかの分野があります。

**Metadata work.** Many cataloging teams use Python to migrate, transform and enrich metadata that they receive from different sources. For example, the [pymarc library](https://pypi.org/project/pymarc/) is a popular Python package for working with MARC21 records.

**メタデータ作業。** 多くのカタログチームは、Pythonを使用して、さまざまなソースから受け取ったメタデータを移行、変換、強化しています。たとえば、[pymarcライブラリ](https://pypi.org/project/pymarc/)は、MARC21レコードを扱うための一般的なPythonパッケージです。

**Collection and citation analysis.** Python can automate workflows to analyze library collections. In cases where spreadsheets and OpenRefine are unable to support specific forms of analysis, Python is a more flexible and powerful tool.

**収集と引用分析。** Pythonは、ライブラリコレクションを分析するためのワークフローを自動化できます。スプレッドシートやOpenRefineが特定の形式の分析をサポートできない場合、Pythonはより柔軟で強力なツールです。

**Assessment.** Library workers often need to collect metrics or statistics on some aspect of their work. Python can be a valuable tool to collect, clean, analyze, and visualize that data in a consistent way over time.

**評価。** 図書館の労働者は、多くの場合、仕事のいくつかの側面に関する指標や統計を収集する必要があります。Pythonは、時間の経過とともに一貫した方法でそのデータを収集、クリーンアップ、分析、視覚化するための貴重なツールです。

**Accessing data.** Researchers often use Python to collect data (including textual data) from websites and social media platforms. Academic librarians are often well-positioned to help teach these researchers how to use Python for web scraping or querying Application Programming Interfaces (APIs) to access the data they need. 

**データへのアクセス。** 研究者は、ウェブサイトやソーシャルメディアプラットフォームからデータ(テキストデータを含む)を収集するためにPythonを使用することがよくあります。学術図書館員は、多くの場合、必要なデータにアクセスするためのWebスクレイピングまたはクエリアプリケーションプログラミングインターフェイス（API）にPythonを使用する方法をこれらの研究者に教えるのに役立つ立場にあります。

**Analyzing data.** Python is widely used by scholars who are embarking on different forms of computational research (e.g., network analysis, natural language processing, machine learning). Library workers can leverage Python for their own research in these areas, but also take part in larger networks of academic support related to data science, computational social sciences, and/or digital humanities.

**データの分析。** Pythonは、さまざまな形態の計算研究(ネットワーク分析、自然言語処理、機械学習など)に着手している学者によって広く使用されています。図書館の労働者は、これらの分野で独自の研究にPythonを活用することができますが、データサイエンス、計算社会科学、および/またはデジタル人文科学に関連する学術支援のより大きなネットワークに参加することもできます。

:::::::::::::::::::::::::
::::::::::::::::::::::::::::::::::::::::::::::::::

## Use JupyterLab to edit and run Python code.
## JupyterLabを使用して、Pythonコードを編集および実行します。
  
If you haven't already done so, see [the setup instructions](../learners/setup.md) for details on how to install JupyterLab and Python via Anaconda. The setup instructions also walk you through the steps you should follow to create an `lc-python` folder on your Desktop, and to download and unzip the dataset we'll be working with inside of that directory. 

まだ行っていない場合は、Anaconda経由でJupyterLabとPythonをインストールする方法の詳細については、[セットアップ手順](../learners/setup.md)を参照してください。セットアップ手順では、デスクトップに「lc-python」フォルダを作成し、そのディレクトリ内で作業するデータセットをダウンロードして解凍する手順も説明します。

### Getting started with JupyterLab

### JupyterLabを使い始める

To run Python, we are going to use Jupyter Notebooks via [JupyterLab][jupyterlab]. Jupyter notebooks are common tools for data science and visualization, and serve as a convenient environment for running Python code interactively where we can view and share the results of our Python code.

Pythonを実行するには、[JupyterLab][jupyterlab]経由でJupyter Notebooksを使用します。Jupyterノートブックは、データサイエンスと視覚化のための一般的なツールであり、Pythonコードの結果を表示および共有できるPythonコードをインタラクティブに実行するための便利な環境として機能します。

:::::::::::::::::::::::::::::::::::::::::  callout
### Alternatives to Juypter
There are other ways of editing, managing, and running Python code. Software developers often use an integrated development environment (IDE) like [PyCharm](https://www.jetbrains.com/pycharm/), [Spyder][spyder] or [Visual Studio Code (VS Code)](https://code.visualstudio.com/), to create and edit Python scripts. Others use text editors like Vim or Emacs to hand-code Python. After editing and saving Python scripts you can execute those programs within an IDE or directly on the command line. 

### Juypterの代替品

Pythonコードを編集、管理、実行する方法は他にもあります。ソフトウェア開発者は、[PyCharm](https://www.jetbrains.com/pycharm/)、[Spyder][spyder]または[Visual Studio Code (VS Code)](https://code.visualstudio.com/)などの統合開発環境(IDE)を使用して、Pythonスクリプトを作成および編集することがよくあります。他の人は、VimやEmacsなどのテキストエディタを使用してPythonを手作業でコーディングします。Pythonスクリプトを編集して保存した後、IDE内またはコマンドラインで直接それらのプログラムを実行できます。

::::::::::::::::::::::::::::::::::::::::::::::::::

Jupyter notebooks let us execute and view the results of our Python code immediately within the notebook. JupyterLab has several other handy features:

Jupyterノートブックを使用すると、ノートブック内でPythonコードの結果をすぐに実行して表示できます。JupyterLabには、他にもいくつかの便利な機能があります。

- You can easily type, edit, and copy and paste blocks of code.
- コードブロックを簡単に入力、編集、コピー、貼り付けることができます。

- It allows you to annotate your code with links, different sized text, bullets, etc.
  to make it more accessible to you and your collaborators.
- リンク、異なるサイズのテキスト、箇条書きなどでコードに注釈を付くことができます。あなたとあなたの協力者にとってよりアクセスしやすくするために。

- It allows you to display figures next to the code to better explore your data and visualize the results of your analysis.
- コードの横に図を表示して、データをよりよく探索し、分析結果を視覚化することができます。

- Each notebook contains one or more cells that contain code, text, or images.

- 各ノートブックには、コード、テキスト、または画像を含む1つ以上のセルが含まれています。
- 
### Start JupyterLab

### JupyterLabを始める

Once you have created the `lc-python` directory on your Desktop, you can start JupyterLab by opening a shell command line interface or by using Anaconda Navigator.

デスクトップに「lc-python」ディレクトリを作成したら、シェルコマンドラインインターフェイスを開くか、Anaconda Navigatorを使用してJupyterLabを起動できます。

#### Mac users - Command Line

#### Macユーザー - コマンドライン

1. Press the <kbd>cmd</kbd> + <kbd>spacebar</kbd> keys and search for `Terminal`. Click the result or press <kbd>return</kbd>. (You can also find `Terminal` in your `Applications` folder, under `Utilities`.)

1. <kbd>cmd</kbd> + <kbd>スペースバー</kbd>キーを押して、「ターミナル」を検索します。結果をクリックするか、<kbd>return</kbd>を押します。(「アプリケーション」フォルダの「ユーティリティ」の下にある「ターミナル」を見つけることもできます。)

2. After you have launched Terminal, change directories to the `lc-python` folder you created earlier and type `jupyter lab`:

2. ターミナルを起動したら、先ほど作成した「lc-python」フォルダにディレクトリを変更し、「jupyter lab」と入力します。

```bash
$ cd ../Desktop/lc-python
$ jupyter lab
```

#### Windows users - Command Line

#### Windowsユーザー - コマンドライン

To start the JupyterLab server you will need to access the Anaconda Prompt.

JupyterLabサーバーを起動するには、Anaconda Promptにアクセスする必要があります。

1. Press the <kbd>Windows Logo Key</kbd> and search for `Anaconda Prompt`, click the result or press enter.

1. <kbd>Windowsロゴキー</kbd>を押して「アナコンダプロンプト」を検索し、結果をクリックするか、Enterキーを押します。

2. Once you have launched the Anaconda Prompt, type the command:

2. アナコンダプロンプトを起動したら、次のコマンドを入力します。

```bash
$ jupyter lab
```

#### Start JupyterLab from Anaconda Navigator

#### Anaconda NavigatorからJupyterLabを始める

If you are unfamiliar with the command line,  you can launch JupyterLab by opening the Anaconda Navigator app and choosing the `Launch` button underneath the JuypterLab icon. 

コマンドラインに慣れていない場合は、Anaconda Navigatorアプリを開き、JuypterLabアイコンの下にある「Launch」ボタンを選択して、JupyterLabを起動できます。

First [start Anaconda Navigator (click for detailed instructions on macOS, Windows, and Linux)](https://docs.anaconda.com/free/navigator/getting-started/#navigator-starting-navigator). You can search for Anaconda Navigator via Spotlight on macOS (<kbd>Command</kbd> + <kbd>spacebar</kbd>), or by using the Windows search function (<kbd>Windows Logo Key</kbd>).

まず[Anaconda Navigatorを起動する(macOS、Windows、Linuxの詳細な手順はクリック)](https://docs.anaconda.com/free/navigator/getting-started/#navigator-starting-navigator)。Anaconda Navigatorは、macOSのSpotlight（<kbd>Command</kbd> + <kbd>spacebar</kbd>）、またはWindows検索機能（<kbd>Windowsロゴキー</kbd>）を使用して検索できます。

After you have launched Anaconda Navigator, click the `Launch` button under JupyterLab. You may need to scroll down to find it. Here is a screenshot of an Anaconda Navigator page similar to the one that should open on either macOS or Windows.

Anaconda Navigatorを起動したら、JupyterLabの下にある「Launch」ボタンをクリックします。それを見つけるには、下にスクロールする必要があるかもしれません。これは、macOSまたはWindowsで開くべきページに似たAnaconda Navigatorページのスクリーンショットです。

![Launch JupyterLab from Anaconda Navigator](../episodes/fig/0_anaconda_navigator_landing_page.png){alt='screenshot of the launch button for JuypterLab in Anaconda Navigator'}

## The JupyterLab Interface

## JupyterLabインターフェース

Launching JupyterLab opens a new tab or window in your preferred web browser. While JupyterLab enables you to run code from your browser, it does not require you to be online. If you take a look at the URL in your browser address bar, you should see that the environment is located at your localhost, meaning it is running from your computer: `http://localhost:8888/lab`.

JupyterLabを起動すると、お好みのウェブブラウザで新しいタブまたはウィンドウが開きます。JupyterLabではブラウザからコードを実行できますが、オンラインである必要はありません。ブラウザのアドレスバーのURLを見ると、環境がlocalhostにあることがわかります。つまり、コンピュータから実行されていることがわかります。`http://localhost:8888/lab`。

When you first open JupyterLab you will see two main panels. In the left sidebar is your file browser. You should see a folder in the file browser named `data` that contains all of our data. 

JupyterLabを最初に開くと、2つのメインパネルが表示されます。左側のサイドバーにはファイルブラウザがあります。ファイルブラウザには、すべてのデータを含む「data」という名前のフォルダが表示されるはずです。

### Creating a Juypter Notebook

### Juypterノートブックの作成

To the right you will see a `Launcher` tab. Here we have options to launch a Python 3 notebook, a Terminal (where we can use shell commands), text files, and other items. For now, we want to launch a new Python 3 notebook, so click once on the `Python 3 (ipykernel)` button underneath the Notebook header. You can also create a new notebook by selecting *New -> Notebook* from the *File* menu in the Menu Bar.

右側には「Launcher」タブが表示されます。ここでは、Python 3ノートブック、ターミナル(シェルコマンドを使用できる場所)、テキストファイル、その他のアイテムを起動するオプションがあります。今のところ、新しいPython 3ノートブックを立ち上げたいので、ノートブックヘッダーの下にある「Python 3（ipykernel）」ボタンを1回クリックします。メニューバーの*ファイル*メニューから*新規->ノートブック*を選択して、新しいノートブックを作成することもできます。

![Launching a new Python 3 Notebook](../episodes/fig/0_jupyterlab_launcher.png){alt='screenshot of the JupyterLab for launching notebook'}

When you start a new Notebook you should see a new tab labeled `Untitled.ipynb`. You will also see this file listed in the file browser to the left. Right-click on the `Untitled.ipynb` file in the file browser and choose `Rename` from the dropdown options. Let's call the notebook file, `workshop.ipynb`.

新しいノートブックを起動すると、「Untitled.ipynb」というラベルの付いた新しいタブが表示されるはずです。このファイルは左側のファイルブラウザにも表示されます。ファイルブラウザで「Untitled.ipynb」ファイルを右クリックし、ドロップダウンオプションから「名前の変更」を選択します。ノートブックファイルを「workshop.ipynb」と呼びましょう。


:::::::::::::::::::::::::::::::::::::::::  callout

## JupyterLab? What about Jupyter notebooks? Python notebooks? IPython?

## JupyterLab？ジュピターのノートはどうですか?パイソンノート？IPython？

JupyterLab is the [next stage in the evolution of the Jupyter Notebook](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html#overview).
If you have prior experience working with Jupyter notebooks, then you will have a good idea of how to work with JupyterLab. Jupyter was created as a spinoff of IPython in 2014, and includes interactive computing support for languages other than just Python, including R and Julia. While you'll still see some references to Python and IPython notebooks, IPython notebooks are officially deprecated in favor of Jupyter notebooks.

JupyterLabは[Jupyter Notebookの進化の次の段階](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html#overview)です。

Jupyterノートブックの操作経験がある場合は、JupyterLabの操作方法について良いアイデアがあるでしょう。Jupyterは2014年にIPythonのスピンオフとして作成され、RやJuliaを含むPython以外の言語のインタラクティブコンピューティングサポートが含まれています。あなたはまだPythonとIPythonノートブックへのいくつかの参照が表示されますが、IPythonノートブックはJupyterノートブックを支持して正式に廃止されています。

::::::::::::::::::::::::::::::::::::::::::::::::::

We will share more features of the JupyterLab environment as we advance through the lesson, but for now let's turn to how to run Python code.

レッスンを進めるにつれて、JupyterLab環境のより多くの機能を共有しますが、今のところはPythonコードの実行方法に進みましょう。

### Running Python code 

### Pythonコードの実行

Jupyter allows you to add code and formatted text in different types of blocks called cells. By default, each new cell in a Jupyter Notebook will be a "code cell" that allows you to input and run Python code. Let's start by having Python do some arithmetic for us. 

Jupyterを使用すると、セルと呼ばれるさまざまな種類のブロックにコードとフォーマットされたテキストを追加できます。デフォルトでは、Jupyter Notebookの各新しいセルは、Pythonコードを入力して実行できる「コードセル」になります。Pythonに算術をやってもらうことから始めましょう。

In the first cell type 7 * 3, and then press the <kbd>Shift</kbd>\+<kbd>Return</kbd> keys together to execute the contents of the cell. (You can also run a cell by making sure your cursor is in the cell and choosing `Run > Run Selected Cells` or selecting the "Play" icon (the sideways triangle) at the top of the noteboook.)

最初のセルで7 * 3と入力し、<kbd>Shift</kbd>\+<kbd>Return</kbd>キーを一緒に押してセルの内容を実行します。（カーソルがセルにあることを確認し、「実行」>「選択したセルを実行」を選択するか、ノートブックの上部にある「再生」アイコン（横向きの三角形）を選択することで、セルを実行することもできます。）

```python
7 * 3
```

You should see the output appear immediately below the cell, and Jupyter will also create a new code cell for you. 

出力がセルのすぐ下に表示され、Jupyterも新しいコードセルを作成します。

```python
21
```

If you move your cursor back to the first cell, just after the `7 * 3` code, and hit the <kbd>Return</kbd> key (without shift), you should see a new line in the cell where you can add more Python code. Let's add another calculation to the same cell:

「7 * 3」コードの直後にカーソルを最初のセルに戻し、<kbd>Return</kbd>キー（シフトなし）を押すと、Pythonコードを追加できる新しい行がセルに表示されるはずです。同じセルに別の計算を追加しましょう。

```python
7 * 3
2 +1
```

While Python runs both calculations Juypter will only display the output from the last line of code in a specific cell, unless you tell it to do otherwise.

Pythonは両方の計算を実行しますが、Juypterは、そうでないように指示しない限り、特定のセルのコードの最後の行からの出力のみを表示します。

```python
3
```

### Editing the notebook

### ノートブックの編集

You can use the icons at the top of your notebook to edit the cells in your Notebook:

ノートブックの上部にあるアイコンを使用して、ノートブックのセルを編集できます。

- The `+` icon adds a new cell below the selected cell.
- 「+」アイコンは、選択したセルの下に新しいセルを追加します。
- The scissors icon will delete the current cell. 
- ハサミのアイコンは、現在のセルを削除します。

You can move cells around in your notebook by hovering over the left-hand margin of a cell until your cursor changes into a four-pointed arrow, and then dragging and dropping the cell where you want it.

カーソルが4点の矢印に変わるまでセルの左側の余白にカーソルを合わせ、セルを好きな場所にドラッグ&ドロップすることで、ノートブック内のセルを移動できます。

:::::::::::::::::::::::::::::::::::::::::  callout
### Markdown
::::::::::::::::::::::::::::::::::::: instructor

Instructors: Since the lesson is focused on Python we don't include any Markdown examples here. If you want to teach Markdown, note that it will slow down the lesson.

インストラクター：レッスンはPythonに焦点を当てているため、ここにはMarkdownの例は含まれていません。マークダウンを教えたい場合は、レッスンが遅くなることに注意してください。

:::::::::::::::::::::::::::::::::::::::::::::::::

You can add text to a Juypter notebook by selecting a cell, and changing the dropdown above the notebook from `Code` to `Markdown`. Markdown is a lightweight language for formatting text. This feature allows you to annotate your code, add headers, and write documentation to help explain the code. While we won't cover Markdown in this lesson, there are many helpful online guides out there:

セルを選択し、ノートブックの上のドロップダウンを「コード」から「マークダウン」に変更することで、Juypterノートブックにテキストを追加できます。Markdownは、テキストをフォーマットするための軽量言語です。この機能を使用すると、コードに注釈を付じたり、ヘッダーを追加したり、コードを説明するのに役立つドキュメントを書いたりできます。このレッスンではMarkdownを取り上げませんが、多くの役立つオンラインガイドがあります。

- [Markdown for Jupyter Cheatsheet (IBM)](https://www.ibm.com/docs/en/watson-studio-local/1.2.3?topic=notebooks-markdown-jupyter-cheatsheet)
- [Markdown Guide (Matt Cone)](https://www.markdownguide.org/)

![Changing a cell from Code to Markdown](../episodes/fig/0_jupyter_markdown_dd.png){alt='screenshot of the Jupyter notebook dropdown to change a cell to Markdown'}

You can also use "hotkeys"" to change Jupyter cells from Code to Markdown and back:

「ホットキー」を使用して、JupyterセルをCodeからMarkdownに変更することもできます。

- Click on the code cell that you want to convert to a Markdown cell.
- マークダウンセルに変換するコードセルをクリックします。
- Press the <kbd>Esc</kbd> key to enter command mode.
- <kbd>Esc</kbd>キーを押してコマンドモードに入ります。
- Press the <kbd>M</kbd> key to convert the cell to Markdown.
- <kbd>M</kbd>キーを押して、セルをMarkdownに変換します。
- Press the <kbd>y</kbd> key to convert the cell back to Code.
- <kbd>y</kbd>キーを押して、セルをコードに戻します。
::::::::::::::::::::::::::::::::::::::::::::::::::

[anaconda]: https://docs.anaconda.com/anaconda/install/
[spyder]: https://www.spyder-ide.org/
[jupyterlab]: https://jupyterlab.readthedocs.io/en/stable/

:::::::::::::::::::::::::::::::::::::::: keypoints

- You can launch JupyterLab from the command line or from Anaconda Navigator.
- コマンドラインまたはAnaconda NavigatorからJupyterLabを起動できます
- You can use a JupyterLab notebook to edit and run Python.
- JupyterLabノートブックを使用して、Pythonを編集および実行できます。
- Notebooks can include both code and markdown (text) cells.
- Notebooks can include both code and markdown (text) cells.
- 
::::::::::::::::::::::::::::::::::::::::::::::::::
