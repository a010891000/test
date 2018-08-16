# Python錯誤訊息意思


SyntaxError: unexpected EOF while parsing

原因：這個錯誤是你語法有問題，我當時碰到是因為print(d.drop() 

//少打一個括號，別盲目地相信會自動補全，自己認真檢查一下，肯定這行代碼少了或者多了東西希望有用。

來源：[Python错误SyntaxError: unexpected EOF while parsing](https://blog.csdn.net/u011957271/article/details/52698332)

<br>

TabError: inconsistent use of tabs and spaces in indentation //縮進中不一致使用製表符和空格

Solved method:

Don't use tabs.

Set your editor to use 4 spaces for indentation.
Make a search and replace to replace all tabs with 4 spaces.
Make sure your editor is set to display tabs as 8 spaces.

來源：[python - "inconsistent use of tabs and spaces in indentation" - Stack Overflow](https://stackoverflow.com/questions/5685406/inconsistent-use-of-tabs-and-spaces-in-indentation)

<br>

ndexError: list index out of range

1. list[index]index 超出範圍

2. list 是一個空的(沒有一個元素)，進行 list[0] 就會出現錯誤
 

