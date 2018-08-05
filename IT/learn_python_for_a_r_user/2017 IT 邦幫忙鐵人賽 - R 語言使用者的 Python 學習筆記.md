# 2017 IT 邦幫忙鐵人賽 

## 作者：郭耀仁

### 關鍵字( keyword )

+ Numpy:高階統計軟體
+ pandas


## 基本變數類型

Python 的基本變數類型分為以下這幾類：

+ 數值
    - float
    - int
    - complex
+ 布林值（bool）
+ 文字（str）



Python 回傳變數類型的函數是 type()，如果不清楚這個函數有哪些參數可以使用，你可以在 cell 中輸入 help(type) 來看說明文件。

種類| Python |R
----|--|----
複數宣告|j|i
布林值|true/false|TRUE/FLASE
索引起始值|0|1

## 變數類型的轉換

Python 轉換變數類型的函數：

+ float()：轉換變數類型為 float
+ int()：轉換變數類型為 int
+ complex()：轉換變數類型為 complex
+ bool()：轉換變數類型為 bool
+ str()：轉換變數類型為 str

轉換變數類型的函數也不是萬能，比如說 `int("True")` 不會成功，想要將 "True" 轉換為整數就要使用兩次轉換類型的函數 `int(bool("True"))`。

## 資料結構

Python 基本的資料結構大致分為三類：
+ list
+ tuple
+ dictionary

種類|Python|R
:-----:|:-----:|:----:
回傳變數類型的函數|type()|class()
資料結構|list、tuple、dictionary|vector、factor、matrix、data frame、list

Python 的 list 時候我們只需要使用中括號 `[]` 將元素包起來，而在選擇元素也是使用中括號 `[]` 搭配索引值，Python 的索引值由 0 開始，這跟 R 語言索引值由 1 開始有很大的區別。

tuple 跟 list 很像，但是我們不能新增，刪除或者更新 tuple 的元素。我們可以使用 `tuple()` 函數將既有的 list 轉換成為 tuple，或者在建立物件的時候使用小括號 `()` 有別於建立 list 的時候使用的中括號 `[]`。

dictionary 是帶有鍵值（key）的 list，這樣的特性讓我們在使用中括號 `[]` 選擇元素時可以使用鍵值，在建立 Python 的 dictionary 時候我們只需要使用大括號 `{}` 或者使用 `dict()` 函數轉換既有的 list。



## 迴圈與流程控制

### Python 的 break 與 continue

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

## 載入資料

我們選擇幾種常見的讀入資料格式，分別使用 Python 進行載入。

+ csv
+ 不同分隔符號的資料
    - 以 `tab 鍵（"\t"）` 分隔
    - 以 `空格（"\s"）` 分隔
    - 以 `冒號（":"）`分隔
+ Excel 試算表
+ JSON


### 載入 csv

副檔名為 .csv 的資料格式顧名思義是逗號分隔資料（comma separated values），是最常見的表格式資料（tabular data）格式。

我們使用 `pandas` 套件的 `read_csv()` 方法來載入。

```
import pandas as pd

url = "https://storage.googleapis.com/2017_ithome_ironman/data/iris.csv" # 在雲端上儲存了一份 csv 檔案
iris_df = pd.read_csv(url)
iris_df.head()
```

![csv](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/1.csv.png)

### 載入不同分隔符號的資料

我們使用 `pandas` 套件的 `read_table()` 方法來載入，並且依據分隔符號指定 `sep = `參數。

#### 以 tab 鍵（"\t"）分隔

```
import pandas as pd

url = "https://storage.googleapis.com/2017_ithome_ironman/data/iris.tsv" # 在雲端上儲存了一份 tsv 檔案
iris_tsv_df = pd.read_table(url, sep = "\t")
iris_tsv_df.head()
```

![tab](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/2.tab.png)

#### 以冒號（":"）分隔

```
import pandas as pd

url = "https://storage.googleapis.com/2017_ithome_ironman/data/iris.txt" # 在雲端上儲存了一份 txt 檔案
iris_colon_sep_df = pd.read_table(url, sep = ":")
iris_colon_sep_df.head()
```

![colon](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/3.colon.png)

### 載入 Excel 試算表

我們以副檔名為 `.xlsx` 的 Excel 試算表檔案為例。

我們使用 `pandas` 套件的 `read_excel()` 方法來載入。

```
import pandas as pd

url = "https://storage.googleapis.com/2017_ithome_ironman/data/iris.xlsx" # 在雲端上儲存了一份 Excel 試算表
iris_xlsx_df = pd.read_excel(url)
iris_xlsx_df.head()
```

![excel](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/4.excel.png)


### 載入 JSON

JSON（JavaScript Object Notation）格式的資料是網站資料傳輸以及 NoSQL（Not only SQL）資料庫儲存的主要類型，R 語言與 Python 有相對應的套件可以協助我們把 
JSON 資料格式載入後轉換為我們熟悉的 data frame。


我們使用 `pandas` 套件的 `read_json()` 方法來載入。

```
import pandas as pd

url = "https://storage.googleapis.com/2017_ithome_ironman/data/iris.json" # 在雲端上儲存了一份 JSON 檔
iris_json_df = pd.read_json(url)
iris_json_df.head()
```

![json](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/5.json.png)

我們透過 pandas 套件的 `read_csv()`、`read_table()`、`read_excel()` 與 `read_json` 等方法可以將不同的資料格式轉換為我們熟悉的 data frame 資料結構

## 網頁解析

`BeautifulSoup` 我們使用的選擇概念是 CSS 選擇器；`rvest` 我們則是使用 XPATH 選擇器

## 資料視覺化 matplotlib

我們的開發環境是 Jupyter Notebook，這個指令可以讓圖形不會在新視窗呈現。

```
%matplotlib inline
```

我們今天試著使用看看 **matplotlib** 來畫一些基本的圖形，包括：

- 直方圖（Histogram）
- 散佈圖（Scatter plot）
- 線圖（Line plot）
- 長條圖（Bar plot）
- 盒鬚圖（Box plot）

### 直方圖（Histogram）

使用 `matplotlib.pyplot` 的 `hist()` 方法。

```
%matplotlib inline

import numpy as np
import matplotlib.pyplot as plt

normal_samples = np.random.normal(size = 100000) # 生成 100000 組標準常態分配（平均值為 0，標準差為 1 的常態分配）隨機變數

plt.hist(normal_samples)
plt.show()
```

![histogram](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/6.histogram.png)

### 散佈圖（Scatter plot）

使用 `matplotlib.pyplot` 的 `scatter()` 方法。

```
%matplotlib inline

import matplotlib.pyplot as plt

speed = [4, 4, 7, 7, 8, 9, 10, 10, 10, 11, 11, 12, 12, 12, 12, 13, 13, 13, 13, 14, 14, 14, 14, 15, 15, 15, 16, 16, 17, 17, 17, 18, 18, 18, 18, 19, 19, 19, 20, 20, 20, 20, 20, 22, 23, 24, 24, 24, 24, 25]
dist = [2, 10, 4, 22, 16, 10, 18, 26, 34, 17, 28, 14, 20, 24, 28, 26, 34, 34, 46, 26, 36, 60, 80, 20, 26, 54, 32, 40, 32, 40, 50, 42, 56, 76, 84, 36, 46, 68, 32, 48, 52, 56, 64, 66, 54, 70, 92, 93, 120, 85]

plt.scatter(speed, dist)
plt.show()
```

![Scatter plot](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/7.scatter_plot.png)

### 線圖（Line plot）

使用 `matplotlib.pyplot` 的 `plot()` 方法。

```
%matplotlib inline

import matplotlib.pyplot as plt

speed = [4, 4, 7, 7, 8, 9, 10, 10, 10, 11, 11, 12, 12, 12, 12, 13, 13, 13, 13, 14, 14, 14, 14, 15, 15, 15, 16, 16, 17, 17, 17, 18, 18, 18, 18, 19, 19, 19, 20, 20, 20, 20, 20, 22, 23, 24, 24, 24, 24, 25]
dist = [2, 10, 4, 22, 16, 10, 18, 26, 34, 17, 28, 14, 20, 24, 28, 26, 34, 34, 46, 26, 36, 60, 80, 20, 26, 54, 32, 40, 32, 40, 50, 42, 56, 76, 84, 36, 46, 68, 32, 48, 52, 56, 64, 66, 54, 70, 92, 93, 120, 85]

plt.plot(speed, dist)
plt.show()
```

![Line plot](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/8.line_plot.png)

### 長條圖（Bar plot）

使用 `matplotlib.pyplot` 的 `bar()` 方法。

```
%matplotlib inline

from collections import Counter
import matplotlib.pyplot as plt
import numpy as np

cyl = [6 ,6 ,4 ,6 ,8 ,6 ,8 ,4 ,4 ,6 ,6 ,8 ,8 ,8 ,8 ,8 ,8 ,4 ,4 ,4 ,4 ,8 ,8 ,8 ,8 ,4 ,4 ,4 ,8 ,6 ,8 ,4]

labels, values = zip(*Counter(cyl).items())
width = 1

plt.bar(indexes, values)
plt.xticks(indexes + width * 0.5, labels)
plt.show()
```

郭耀仁先生的結果：

![Bar plot for 郭耀仁](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/9.1bar_plot.png)

自己使用相同程式碼跑出的結果(目前只知道，有名稱未被定義，後續追蹤為何跑不出相同圖形的原因)

![Bar plot for me](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/9.2bar_plot.png)

嘗試修改之後的結果，刪除`plt.xticks(indexes + width * 0.5, labels)`的部分，但卻無法像郭耀仁先生所輸出的圖形一樣由大至小排列

![Bar plot for me trail and error](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/9.3bar_plot.png)


### 盒鬚圖（Box plot）

使用 matplotlib.pyplot 的 boxplot() 方法。

```
%matplotlib inline

import numpy as np
import matplotlib.pyplot as plt

normal_samples = np.random.normal(size = 100000) # 生成 100000 組標準常態分配（平均值為 0，標準差為 1 的常態分配）隨機變數

plt.boxplot(normal_samples)
plt.show()
```

![Box plot](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/10.box_plot.png)

### 輸出圖形

使用圖形物件`savefig()`方法。

```
import numpy as np
import matplotlib.pyplot as plt

nomal_samples = np.random.normal(size = 100000) # 生成 100000 組標準常態分配（平均值為 0，標準差為 1 的常態分配）隨機變數

plt.hist(normal_samples)
plt.savefig(fname = "my_hist.png", format = "png") # 檔名為 my_hist，輸出檔案類型為 png 
```


### 補充資料

plot 函數的調用方式很靈活，第一句將 x,y 陣列傳遞給 plot 之後，用關鍵字參數指定各種屬性：

+ label : 給所繪製的曲線一個名字(即是圖例名稱)，此名字在圖示 (legend) 中顯示。只要在字串前後添加 "$" 符號， matplotlib 就會使用其內嵌的 latex 引擎繪製的數學公式。
+ color : 指定曲線的顏色
+ linewidth : 指定曲線的寬度

設置繪圖物件的各個屬性：

+ xlabel : 設置 X 軸的文字
+ ylabel : 設置 Y 軸的文字
+ title : 設置圖表的標題
+ xlim : 設置 X 軸的範圍(最小值, 最大值) 
+ ylim : 設置 Y 軸的範圍(最小值, 最大值)
+ legend : 顯示圖例
+ savefig : 輸出圖片檔

以線圖為例

```
%matplotlib inline

import matplotlib.pyplot as plt

temperature = [28, 27, 27, 27, 27, 28, 29, 30, 31, 32, 32, 32, 32, 32, 32, 32, 31, 30, 29, 29, 29, 28, 28, 28] 
hour = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24]
# x和y軸的筆數要相同!!

# plt.plot(hour, temperature) # plt.plot(x,y) 

plt.plot(hour, temperature,label="$temperature$",color="red",linewidth=2) #圖例名稱為 temperature ，曲線的顏色為紅色，曲線寬度為2
plt.xlabel("Time(hr)") # X 軸單位 
plt.ylabel("°C")       # Y 軸單位   # ALT+0176 = °
plt.title("Celsius") # 圖表名稱為Celsius
plt.legend() # 顯示圖例
plt.show() # 繪製輸出的圖像
```

![Line plot](https://raw.githubusercontent.com/a010891000/test/master/IT/learn_python_for_a_r_user/img/11.line_plot.png)

#### plt.savefig()

```
savefig(fname, dpi=None, facecolor='w', edgecolor='w',
        orientation='portrait', papertype=None, format=None,
        transparent=False, bbox_inches=None, pad_inches=0.1,
        frameon=None)
```
參考資料：
[matplotlib.pyplot.savefig — Matplotlib 2.2.2 documentation](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.savefig.html)  # **matplotlib.plat.savefig 基本介紹及應用**