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

![image](https://raw.githubusercontent.com/a010891000/test/master/image/Raspbian/1.png)

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

![image](https://raw.githubusercontent.com/a010891000/test/master/image/Raspbian/3.png)

使用 Unicode 轉義序列

![image](https://raw.githubusercontent.com/a010891000/test/master/image/Raspbian/4.png)

## 第5章 程序中使用算數
1. 摘要
2. 筆記

運算符號 | 敘述
------- | -------
+| 加法
-| 減法
*| 乘法
/| 除法
% | 整除後得到的稱為餘數
//| 整除後得到的稱為商數
**| 求冪
& | 二進位的 **與**
| | 二進位的 **或**
and | 邏輯的 **與**
or  | 邏輯的 **或**
not | 邏輯的 **非**

