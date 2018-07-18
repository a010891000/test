## 第1章 配置樹梅派
1. 摘要
+ 由Eben Upton和幾個同事在英國發明的。
+ 核心：使用Python編程語言(=程式語言)
+ 啟動和運行樹梅派的基本外接的周邊設備
    - SD卡
        * 至少4G(8G更好)的標準SDHC記憶卡
    - 電源
        * 基本要求：5V(伏特)、700mA(毫安)、USB to Micro USB 轉接線
    - HDMI接口的電視或計算機顯示器
        * 不支持VGA
    - USB鍵盤
        * 方便輸入Python指令
2. 筆記

+ 樹莓派的不同稱呼，如：PRi或Pi

種類    | A型 | B型
------ | -----| ------
記憶體  | 256MB | 512MB 
USB接口 | 1個 | 2個 
網路接口 | 無 | 有 


## 第2章 認識Raspbian linux發行版
1. 摘要
+ Linux是世界上第三流行的桌面操作系統，在微軟Windows和蘋果OS X後。
+ 樹莓派的操作系統Raspbian是Linux的分支。
+ Debian是許多流行的Linux發行版的基礎，如：Ubuntu、Raspbian。
2. 筆記
+ 初次使用，輸入用戶名pi和密碼raspberry(注意再輸入密碼的時候，螢幕是不會顯示任何東西，這是正常的)
+ 登入成功後，Raspbian的提示符：

```
pi@raspberrypi ~ $
```

+ 輸入whoami命令後，會顯示出鍵入命令的用戶是誰。

![whoami](https://raw.githubusercontent.com/a010891000/test/master/image/Raspbian/1.png)

+ 一些基本的命令行命令

命令   | 描述 
------ | -----
cd     | 改變當前的位置到提供的路徑 
cat    | 顯示一個文件的內容
mkdir  | 使用提供的資料夾路徑創建一個新的資料夾
ls     | 顯示當前位置的文件和文件夾
pwd    | 顯示妳所在的位置的路徑（當前的工作路徑）

## 第3章 搭建編碼環境
1. 摘要
+ Python由Guido van Rossum發明。名字源自於電視節目「Monty Python's Flying Circus」
+ Python v3和Python v2
    - Python v3基於Unicode，可支援英文字符和非英文字符。 
    - Python v2基於ASCII，只能處理英文字符。
    - Unicode是一種計算機字符集的編碼方式，用來表示各種字符。
2. 筆記
+ Python解釋器
    - 交互式Shell：允許輸入一條Python語句且立即檢查錯誤並解釋。
    - 開發環境Shell：通過交互式Shell，每條Python語句在輸入時馬上被解釋。也可編寫整個Python程序（即腳本）。
    - 文本編輯器：創造和修改文件文本的程序，僅幫助個人創建一個Python腳本文件。
+ 交互式Shell在LXTminal(終端機)內運行。
+ IDLE開發環境Shell
    - IDLE能在三個桌面操作系統上使用（Linux、Windows、OS X）。
    - 可在最初打開的IDLE窗口（IDLE交互模式窗口）輸入Python語句，也可直接開啟腳本(.py)並開始編譯或使用。
    - 在腳本內，更改完後要執行，系統會先要求儲存(按`Ctrl+S`組合鍵或點擊File→Save as→Save)，才可執行(按`F5`鍵或點擊Run→Run Module)。

## 第4章 腳本的輸出
1. 摘要
+ 使用 print 函數進行輸出及使用 input 函數進行輸入。
+ 建立各種變量，並賦予變量一個值，且學習各種數據類型和在 Python 使用時的情況。
2. 筆記
+ print 函數顯示字符
    - `print('This is an example of using single quotes.')`  **使用單引號**
    - `print("This is an example of using single quotes.")`  **使用雙引號**
    - 產出結果皆為：`This is an example of using single quotes.`
    - 建議選擇一種引號並持續保持一次，前一個單引號，下一個雙引號，會讓代碼難以理解及混亂。

+ 一些Python轉義序列
    - 轉義字符是一種特殊的字符常量。轉義字符以反斜線「\」開頭，後跟一個或幾個字符。
    

轉義序列 | 敘述
------- | -------
\'      | 顯示一個單引號
\"      | 顯示一個雙引號
\a      | 製造一個鐘聲
\f      | 插入一個換頁
\n      | 插入一個換行符號
\t      | 插入一個水平製表符
\u####  | 顯示以四個十六進位（簡體書稱進制）數字(####)所表示的 Unicode 字符


+ 參考及注意事項 
    - [Unicode 編碼表](http://jicheng.tw/hanzi/unicode.html)
    - 網頁內的 `U+####` ，在python裡要輸入成 `\u####` 。
    - 如：圓周率( π )的十六進位數 U+03C0 ，就要輸入成 `\u03c0` (**大小寫不影響**)

使用轉義序列添加換行符號

![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/1.png)

使用 Unicode 轉義序列

![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/2.png)

## 第5章 程序中使用算數
1. 摘要
+ 需要更高級的數學運算，可將 math 引入腳本中。( math 提供計算、三角函數和基本統計學的函數)
+ NumPy 數學庫，包含許多線性幾何、高級統計學和信號處理運算所需要的多為數組操作函數。
    - 數組 (Array)，亦名為陣列。

2. 筆記

運算符號 | 敘述
------- | -------
+| 加法
-| 減法
*| 乘法
/| 除法
% | 整除後得到的稱為**餘數**
//| 整除後得到的稱為**商數**
**| 求冪
& | 二進位的 **與**
｜ | 二進位的 **或**
and | 邏輯的 **與**
or  | 邏輯的 **或**
not | 邏輯的 **非**
^ | 按位異或
~ | 二進位補碼


運算中使用一個變量時一定要賦值，不然 Python 會報錯。

![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/3.png)

## 第6章 控制你的程序
1. 摘要
+ if基本語法的使用，可用elif來建立多個比較狀況。
+ 當不符合條件時，else語法用來表示失敗的結果，也就是說提供另一個邏輯路徑。
2. 筆記
+ 使用if語句

最基本的結構化命令就是 if 語句。 if 語句的再 Python 的基本格式

``` if (condition): statement ```

數字比較運算符號

運算符號 | 描述
--------| ------
==      | 等於
!=      | 不等於
<>      | 不等於
＞      | 大於
＜      | 小於
＞=     | 大於或等於
＜=     | 小於或等於

## 第7章 循環
1. 摘要
+ 運用 for 或 while 語句，處理重複的問題。

2. 筆記
+ for 函數
    - 被稱為記數控制迴圈（簡體書稱為循環），迴圈的任務是被設定為執行一定的次數。

    - for 語法結構

    `for variable in date_list:`

       `set_of_Python_statements`

    - 易犯之錯誤：缺少冒號

    ![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/4.png)

    - 易犯之錯誤：不一致的縮排

    ![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/5.png)

+ range 函數
    - 只接受整數作為參數，不接受浮點數或是字符串。
    
    - range 函數默認情況下，會從0開始產生到停止之間的所有數字列表

    ![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/6.png)

    如圖所示，5 作為停止數字，顯示的數字相當於列表[0, 1, 2, 3, 4]。



    - 加入起始參數改變 range 的行為

    `range(start,stop)`

    ![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/7.png)

    如圖所示，從 1 開始到 5 前停下來



    - 改變 range 函數產生數字列表的增加量，可以增夾一個步進參數。（默認情況下，數字遞增為 1 ）

    `range(start,stop,step)`

    ![image](https://raw.githubusercontent.com/a010891000/test/master/image/Python_for_Raspberry_Pi/8.png)

    如圖所示，起始為 1 到 12 前停下，輸出數字差距為 2

+ while 函數
    - 被稱為條件控制的迴圈，因為迴圈的任務會一直執行下去，直到達到設定的條件，迴圈就會停止。

    - while 語法結構

    `while condition_test_statement`

       `set_of_Python_statements`
