# Содержание
- [ЛР № 1–3](#лабораторная-работа--1--3)
- [ИСР № 1](#инвариативная-самостоятельная-работа--1)
    - [1 задание]
    - [2 задание]
    - [3 задание]
- [ВСР № 1](#вариативная-самостоятельная-работа--1)

# [Лабораторная работа № 1–3](https://repl.it/@Rakleed/programming4-lab1-3)
```python
import sqlite3


conn = sqlite3.connect("example.db")
c = conn.cursor()


def insert():
    values = [("2020-02-20", "BUY", "APL", 100, 42.00)]
    try:
        c.executemany(f'INSERT INTO stocks VALUES (?, ?, ?, ?, ?)', values)
        conn.commit()
    except sqlite3.Error as error:
        print("Не получилось обновить таблицу ", error)


def update():
    price = 10.4
    symbol = "APL"
    try:
        c.execute('UPDATE stocks SET price = ? WHERE symbol = ?', (price, symbol))
        conn.commit()
    except sqlite3.Error as error:
        print("Не получилось обновить таблицу", error)
    

def delete():
    try:
        c.execute("DELETE FROM stocks WHERE price = 56.0")
        conn.commit()
    except sqlite3.Error as error:
        print("Не получилось обновить таблицу ", error)


def main():
    print("Хотите просто увидеть содержимое таблицы? (Y/N)")
    answer = input()
    if answer == "n":
        insert()
        update()
        delete()
    if answer == "y":
        for row in c.execute('SELECT * FROM stocks ORDER BY price'):
            print(row)
    if answer != "y" and answer != "n":
        print("Вы ввели неверные данные.")
    for row in c.execute('SELECT * FROM stocks ORDER BY price'):
            print(row)
    

main()
conn.close()
```
[example.db](src/example.db)

![Result of lab1](src/programming4-lab1-3-result.png)

# Инвариативная самостоятельная работа № 1
### [1.1. ](https://repl.it/@Rakleed/programming4-indepworkinvar1-1)
```python

```
![Result of indepworkinvar1-1](src/programming4-indepworkinvar1-1-result.png)

### [1.2. ](https://repl.it/@Rakleed/programming4-indepworkinvar1-2)
```python

```
![Result of indepworkinvar4-2](src/programming4-indepworkinvar1-2-result.png)

### [1.3. ](https://repl.it/@Rakleed/programming4-indepworkinvar1-3)
```python

```
![Result of indepworkinvar4-3](src/programming4-indepworkinvar1-3-result.png)

# [Вариативная самостоятельная работа № 1]https://repl.it/@Rakleed/programming4-indepworkvar1)
```python

```
![Result of indepworkvar4](src/programming4-indepworkvar1-result.png)
