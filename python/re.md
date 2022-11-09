# module re
# regular expression

case sensitive

`\d` - любая цифра
`\D` - либой символ, кроме цифр
`\s` - whitespace (\t\n\r\f\v)
`\S` - all except whitespaces
`\w` - любая буква, цифра или нижнее подчеркивание
`\W` - все, крому букв, цифр и нижнего подчеркивания

символы повторения:

`regex*` - ноль или более повторений предшествующего элемента
`regex+` - одно или более повторений предшествующего элемента
`regex?` - ноль или одно повторение предшествующего элемента
`regex{n}` - ровно n повторений предшествующего элемента
`regex{n,m}` - от n до m повторений предшествующего элемента
`regex{n,}` - n или более повторений предшествующего элемента

специальные символы:

`.` - любой символ, кроме символа новой строки
`^` - начало строки
`$` - конец строки 
`[abc]` - любой символ в скобках
`[^abc]` - любой символ, кроме тех, что в скобках
`a|b` - элемент a или b
`(regex)` - выражение рассматривается как один элемент. Кроме того, подстрока, которая совпала с выражением, запоминается

жадность `*+`

`<.*>` - match == `<text line> some text>` - до последнего совпадения
`<.*?>` - match == `<text line>` some text> - до первого совпадения

## группировка

`()`

`?P<name>` - group name

`(?P<int>\S+)`

`?:` - группа без запоминания - no-capturing group

`(?:\D)`

## import re

`re.search` - ищет первое совпадение

```python
int_line = "hello, mate!"
re.search(r"\d", int_line)
```

returns `None|Match object`

methods - with `()` == end()
variables - without `()` == re

```pyhton
import re

regex = r"Host (\S+) .+ port (\S+)""

with open("name.txt") as f:
    for line in f: # считываем построчно
        match = re.search(regex, line)
        if match: # если было совпадение
            print(match.group())

```

`pprint` -> отображает символы (\n, \t, etc.)


> collect unique IP addresses with set!!!!

