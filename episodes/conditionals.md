---
title: Conditionals
teaching: 15
exercises: 10
---

::::::::::::::::::::::::::::::::::::::: objectives

- Correctly write programs that use `if` and `else` statements using Boolean expressions.
- ブール式を使用して「if」と「else」ステートメントを使用するプログラムを正しく記述します。
- Trace the execution of conditionals inside of loops.
- ループ内の条件の実行をトレースします。

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can programs do different things for different data?
- プログラムは、異なるデータに対してどのように異なることを行うことができますか?

::::::::::::::::::::::::::::::::::::::::::::::::::

## Use `if` statements to control whether or not a block of code is executed.
## `if`ステートメントを使用して、コードブロックが実行されるかどうかを制御します。

An `if` statement is a *conditional* statement that controls whether a block of code is executed or not. The syntax of an `if` statement is similar to a `for` statement:

`if`ステートメントは、コードブロックが実行されるかどうかを制御する*条件付き*ステートメントです。`if`ステートメントの構文は、`for`ステートメントに似ています。

- The first line opens with `if` and ends with a colon.
- 最初の行は「if」で始まり、コロンで終わります。
- The body is indented (usually by 4 spaces)
- ボディはインデントされています(通常は4つのスペースで)

```python
checkouts = 11
if checkouts > 10.0:
    print(f'{checkouts} is over the limit.')

checkouts = 8
if checkouts > 10.0:
    print(f'{checkouts} is over the limit.')
```

```output
11 is over the limit.
```

## Conditionals are often used inside loops.
## 条件はループ内でよく使われます。

There is not much of a point using a conditional when we know the value (as above), but they're useful when we have a collection to process.

値（上記のように）を知っているときに条件を使用するポイントはあまりありませんが、処理するコレクションがある場合に便利です。

```python
checkouts = [0, 3, 10, 12, 22]
for checkout in checkouts:
    if checkout > 10.0:
        print(f'{checkout} is over the limit.')
```

```output
12 is over the limit.
22 is over the limit.
```

## Use `else` to execute a block of code when an `if` condition is *not* true.
## `if` 条件が*not* true の場合、`else` を使用してコードブロックを実行します。

An `else` statement can be used following `if` to allow us to specify an alternative code block to execute when the `if` *branch* is not taken.

`if`の後に`else`ステートメントを使用して、`if` *ブランチ*が取られていないときに実行する代替コードブロックを指定できます。

```python
for checkout in checkouts:
    if checkout > 10.0:
        print(f'{checkout} is over the limit.')
    else:
        print(f'{checkout} is under the limit.')
```

```output
0 is under the limit.
3 is under the limit.
10 is under the limit.
12 is over the limit.
22 is over the limit.
```

Notice that our `else` statement led to a false output that says 10 is under the limit. We can address this by adding a different kind of `else` statement.

私たちの「else」ステートメントは、10が制限以下であるという誤った出力につながったことに注意してください。別の種類の「else」ステートメントを追加することで、これに対処することができます。

## Use `elif` to specify additional tests.
## 追加のテストを指定するには、`elif`を使用します。

You can use `elif` (short for "else if") to provide several alternative choices, each with its own test. An `elif` statement should always be associated with an `if` statement, and must come before the `else` statement (which is the catch all).

「Elif」（「else if」の略）を使用して、いくつかの代替選択肢を提供でき、それぞれに独自のテストがあります。`elif`ステートメントは常に`if`ステートメントに関連付けられ、`else`ステートメント(キャッチオール)の前に来る必要があります。

```python
for checkout in checkouts:
    if checkout > 10.0:
        print(f'*Warning*: {checkout} is over the limit.')
    elif checkout == 10:
        print(f'{checkout} is at the exact limit.')
    else:
        print(f'{checkout} is under the limit.')
```

```output
0 is under the limit.
3 is under the limit.
10 is at the exact limit.
*Warning*: 12 is over the limit.
*Warning*: 22 is over the limit.

```

Conditions are tested once, in order and are not re-evaluated if values change. Python steps through the branches of the conditional in order, testing each in turn, so the order of your statements matters. 

条件は順番に一度テストされ、値が変更された場合は再評価されません。Pythonは条件の枝を順番に通り抜け、順番にテストするので、ステートメントの順序が重要です。

```python
grade = 85
if grade >= 70:
    print('grade is C')
elif grade >= 80:
    print('grade is B')
elif grade >= 90:
    print('grade is A')
```

```output
grade is C
```

## Compound conditionals using `and` and `or`
## `and` と `or` を使用した複合条件

Often, you want some combination of things to be true.  You can combine
relations within a conditional using `and` and `or`.  

多くの場合、あなたは物事のいくつかの組み合わせが真実であることを望んでいます。あなたは組み合わせることができます
`and`と`or`を使用した条件付き関係。

We can also check if something is less/greater than or equal to a value by using `>=` and `<=` operators.

また、`>=` および `<=` 演算子を使用して、何かが値より小さい/大きいか、または等しいかどうかを確認することもできます。


```python
checkouts = [3, 50, 120]
users = ['fac', 'grad']

for user in users:
    for checkout in checkouts:
        #faculty checkout limit is 100
        if checkout >= 100 and user == 'fac':
            print(f"*Warning*: {checkout} is over the {user} limit.")
            
        #grad limit is 50
        elif checkout >= 50 and user == 'grad':
            print(f"{checkout} is over the {user} limit.")
        
        else:
            print(f"{checkout} is under the {user} limit.")
    
    # print an empty line between users
    print()
    
```
```output
3 is under the fac limit.
50 is under the fac limit.
*Warning*: 120 is over the fac limit.

3 is under the grad limit.
*Warning*: 50 is over the grad limit.
*Warning*: 120 is over the grad limit.
```

:::::::::::::::::::::::::::::::::::::::  challenge

## Age conditionals
## 年齢条件

Write a Python program that checks the age of a user to determine if they will receive a youth or adult library card. The program should:

ユーザーの年齢をチェックして、若者や大人の図書館カードを受け取るかどうかを判断するPythonプログラムを書いてください。プログラムは次のはずです。


1. Store `age` in a variable.
1. 変数に「age」を格納します。
2. Use an `if` statement to check if the age is 16 or older. If true, print "You are eligible for an adult library card."
2.「If」ステートメントを使用して、年齢が16歳以上かどうかを確認します。もし本当なら、「あなたは大人の図書館カードを受け取る資格があります」と印刷してください。
3. Use an `else` statement to print "You are eligible for a youth library card" if the age is less than 16.
3.年齢が16歳未満の場合は、「他の」ステートメントを使用して「青少年図書館カードの資格があります」を印刷します。

If you finish early, try this challenge: 
早く終わったら、この挑戦を試してみてください。

- In a new cell, adapt your program to loop through a list of age values, testing each age with the same output as above.
- 新しいセルで、年齢値のリストをループするようにプログラムを調整し、上記と同じ出力で各年齢をテストします。
:::::::::::::::  solution

## Solution
## 解決策

For parts 1 to 3:

パート1から3の場合:

```python
age = 25

if age >= 16:
  print('You are eligible for an adult library card.')
else:
  print('You are eligible for a youth library card.')
```

For the challenge:
```python
ages = [10, 16, 30, 65]

for age in ages:
  if age >= 16:
    print('You are eligible for an adult library card.')
  else:
    print('You are eligible for a youth library card.')
```


:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::  challenge

## Conditional logic: Fill in the blanks
## 条件付きロジック: 空白を埋める

Fill in the blanks in the following program to check if both the name variable is present in the names list and the password variable is equal to 'true' before giving a user access to a library system.

ユーザーにライブラリシステムへのアクセスを許可する前に、名前変数が名前リストに存在し、パスワード変数が「true」に等しいかどうかを確認するために、次のプログラムの空欄に記入してください。

If you have extra time after you solve the fill in the blanks, change the value of `password` and re-run the program to view the output. 

空白の塗りつぶしを解いた後に余分な時間がある場合は、「パスワード」の値を変更し、プログラムを再実行して出力を表示します。

```python
names = ['Wang', 'Garcia', 'Martin']
name = 'Martin'
password = 'true'

___ item in names:
    print(item)
    if name == item ___ password == _____:
        print('Login successful!')
    elif password __ 'true':
        print(f'Your password is incorrect. Try again.')
    ____ name __ item:
        print(f'- Name does not match. Testing the next item in the list for {name}...')
  
```
:::::::::::::::  solution

## Solution
## 解決策

```python
names = ['Wang', 'Garcia', 'Martin']
name = 'Martin'
password = 'true'

for item in names:
    print(item)
    if name == item and password == 'true':
        print('Login successful!')
    elif password != 'true':
        print(f'Your password is incorrect. Try again.')
    elif name != item:
        print(f'- Name does not match. Testing the next item in the list for {name}...')
```

```output
Wang
- Name does not match. Testing the next item in the list for Martin...
Garcia
- Name does not match. Testing the next item in the list for Martin...
Martin
Login successful!
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::  challenge

## Processing Files Based on Record Length
## レコードの長さに基づいてファイルを処理する

Modify this program so that it only processes files with fewer than 85 records.

85未満のレコードを持つファイルのみを処理するように、このプログラムを変更します。


```python
import glob
import pandas
for filename in glob.glob('data/*.csv'):
    contents = pandas.read_csv(filename)
    ____ ___(______) < ____:
        print(f'{filename} : {len(contents)}')
```

:::::::::::::::  solution

## Solution
## 解決策

```python
import glob
import pandas
for filename in glob.glob('data/*.csv'):
   contents = pandas.read_csv(filename)
   if len(contents) < 85:
       print(f'{filename} : {len(contents)}')
```

:::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- Use `if` statements to control whether or not a block of code is executed.
- `if`ステートメントを使用して、コードブロックが実行されるかどうかを制御します。
- Conditionals are often used inside loops.
- 条件はループ内でよく使用されます。
- Use `else` to execute a block of code when an `if` condition is *not* true.
- `if` 条件が *not* true の場合、`else` を使用してコードブロックを実行します。
- Use `elif` to specify additional tests.
- 「Elif」を使用して、追加のテストを指定します。
- Conditions are tested once, in order.
- 条件は順番に一度テストされます。
- Use `and` and `or` to check against multiple value statements.
- `and`と`or`を使用して、複数の値ステートメントと照合します。

::::::::::::::::::::::::::::::::::::::::::::::::::


