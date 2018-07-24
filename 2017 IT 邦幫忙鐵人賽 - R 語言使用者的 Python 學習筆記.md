# 2017 IT 邦幫忙鐵人賽 

## 作者：郭耀仁

### 基本變數類型

Python 的基本變數類型分為以下這幾類：

+ 數值
    - float
    - int
    - complex
+ 布林值（bool）
+ 文字（str）

Python 回傳變數類型的函數是 type()，如果不清楚這個函數有哪些參數可以使用，你可以在 cell 中輸入 help(type) 來看說明文件。

種類|R |python
----|--|----
複數宣告|i|j
布林值|TRUE/FLASE|true/false
索引起始值|0|1

### 變數類型的轉換

Python 轉換變數類型的函數：

+ float()：轉換變數類型為 float
+ int()：轉換變數類型為 int
+ complex()：轉換變數類型為 complex
+ bool()：轉換變數類型為 bool
+ str()：轉換變數類型為 str

轉換變數類型的函數也不是萬能，比如說 `int("True")` 不會成功，想要將 "True" 轉換為整數就要使用兩次轉換類型的函數 `int(bool("True"))`。

### 迴圈與流程控制

####Python 的 break 與 continue

利用 `break` 描述告訴 for 迴圈當迭代器（此處指變數 ironman）小於 10 的時候要結束迴圈；利用 `continue` 描述告訴 for 迴圈當迭代器小於 10 的時候要跳過它然後繼續執行。

```
# break 描述
ironmen = [49, 8, 12, 12, 6, 61]
for ironman in ironmen:
    if (ironman < 10):
        break
    else:
        print(ironman)

print("---")
print(ironman) # 把迴圈的迭代器（iterator）或稱游標（cursor）最後的值印出來看看

print("\n") # 空一行方便閱讀

# continue 描述
for ironman in ironmen:
    if (ironman < 10):
        continue
    else:
        print(ironman)

print("---")
print(ironman) # 把迴圈的迭代器（iterator）或稱游標（cursor）最後的值印出來看看
```