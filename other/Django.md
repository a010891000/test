

# 網際網路(Internet)是如何運作的

要在任意兩台機器間都有電纜連結這件事本身是不可能的。所以為了可以連結到某台機器（例如說儲存了本站檔案的 http://djangogirls.org）我們需要傳遞我們的要求（Request），經由很多很多台不同的機器。

這件事看起來就像是這樣：

![傳遞要求](https://raw.githubusercontent.com/a010891000/test/master/image/Django/internet_2.png)

想像一下當你輸入 http://djangogirls.org ，你等同於像是寄了一封信裡面寫著：「親愛的 Django Girls, 我想要看看 djangogirls.org 這個網站，請把裡面的資訊寄給我，謝謝！」

![寄信的概念](https://raw.githubusercontent.com/a010891000/test/master/image/Django/internet_4.png)

你的信會先送到最近的郵局。然後再送到下一個離你的收件地址更近一點的，然後再下一個，直到這封信被傳遞到目的地為止。唯一一件比較特別的事是如果你送了頻繁的信 (封包) 到同一個地址，每一封信都會經由完全不同的郵局路徑 (路由)，這是依據他們如何被分散到各個郵局。

# 命令列

## 什麼是命令行(command-line)

這個視窗，就是通常被稱為 命令行（command line） 或 命令行介面 的東西，這是一個以文字為主的應用程式，可以查看、處理並且控制你電腦裡的檔案們（更像是 Windows 系統中的檔案總管或是 Mac 裡的 Finder，但是少了圖形化界面）。還有其他稱呼像是 cmd, CLT, prompt, console 或是 terminal(終端機)。

### 打開命令行介面

開始試驗看看吧，首先我們需要打開命令行介面。

#### Windows

按下 開始 → 所有程式 → 附屬應用程式 → 命令提示字元

#### Mac OS X

應用程式 → 工具程式 → 終端機

#### Linux

他有可能在 應用程式 → 附屬應用程式 → 終端機 這個路徑下，但主要視你的版本而定。如果不是這裡所提到的開啟方式，就麻煩 Google 它一下 :)

### 提示字元(Prompt)
你應該看到一個白的（或黑的）視窗正在等候你的命令。

如果你是用 Mac 或 Linux, 你大概看到一個 $ 符號，像這樣：

`$`

在 Windows 下，它是 > 符號，像這樣

`>`

每個命令都將會以這個提示字元與一個空白字元來準備運行，但是你不需要鍵入這兩個字元，你的電腦會很貼心的幫你打好 :)


## 你的第一個 command （命令）! \o/

我們來點簡單的開頭的，輸入以下指令：

`$ whoami`

或

`> whoami`

然後按下「Enter」。這是我們的結果

$ whoami
olasitarska
如同你所看到的，電腦就會秀出你的使用者名稱，很簡潔對吧？

>試著鍵入每一個指令，不要複製貼上。用這個方法你可以記住更多！

基礎
每一個作業系統的命令行都有可觀的不同的指令，所以確定遵循你的自有設備，現在就容我們來試試看吧！

### 目前路徑

知道我們現在身在路徑的哪裡是很棒的事情，讓我們試試看，鍵入以下指令並按下 Enter：

```
$ pwd
/Users/olasitarska
```

如果你使用 Windows 作業系統：

```
> cd
C:\Users\olasitarska
```

你將可能在你的電腦上看到這些相似的結果。通常你打開命令行，都會以你的使用者根目錄為起點。

### 列出所有檔案和路徑

有哪些東西在這個資料夾下呢？試著找找吧，讓我們看看：

```
$ ls
Applications
Desktop
Downloads
Music
...
```

Windows:

```
> dir
 Directory of C:\Users\olasitarska
05/08/2014 07:28 PM <DIR>      Applications
05/08/2014 07:28 PM <DIR>      Desktop
05/08/2014 07:28 PM <DIR>      Downloads
05/08/2014 07:28 PM <DIR>      Music
...
```

### 改變現在的路徑

或許我們現在可以到「桌面」這個路徑去看看？

```
$ cd Desktop
```

Windows:

```
> cd Desktop
```

檢查看看是不是路徑已經變更了？

```
$ pwd
/Users/olasitarska/Desktop
Windows:
```

```
> cd
C:\Users\olasitarska\Desktop
```

就是這麼簡單！

```
進階技巧：如果你輸入 cd D 然後按一下鍵盤上的 tab 鍵，這個命令就會自動完成剩下未打完的部分。如果有超過一個開頭是 "D" 的資料夾，那就重複按 tab 鍵來選擇你真的要進入的目錄。
```

### 創建路徑

新建一個 Djangogirls 的資料夾在你的桌面上怎麼樣？你可以這麼做：

```
$ mkdir djangogirls
```

Windows:

```
> mkdir djangogirls
```

這些小指令可以建立一個叫做 djangogirls 的資料夾在你的桌面。你可以用 ls/dir 指令檢查看看是不是真的有在你的桌面上，試試看吧 :)

### 實戰！

給你的一個小挑戰： 在你新創建的 djangogirls 資料夾下創造一個叫做 test 的資料夾，使用 cd 及 mkdir 指令。

#### 解答：

```
$ cd djangogirls
$ mkdir test
$ ls
test
```

Windows:

```
> cd djangogirls
> mkdir test
> dir
05/08/2014 07:28 PM <DIR>      test
```


### 清除
我們不想弄得一團亂，所以來移除上一個練習我們所創建的全部東西。

首先，我們需要回到桌面：

```
$ cd ..
```

Windows:

```
> cd ..
```

回到上層目錄使用 cd 與 .. 將會改變你目前的資料夾令你回到上一層（父目錄）

檢查一下目前路徑（你在哪）

```
$ pwd
/Users/olasitarska/Desktop
```

Windows:

```
> cd
C:\Users\olasitarska\Desktop
```

是時候刪除 `djangogirls` 資料夾了:

```
$ rm -r djangogirls
```

Windows:

```
> rmdir /S djangogirls
djangogirls, Are you sure <Y/N>? Y
```

完成！確保這個資料夾真的被刪除了，我們可以輸入：

```
$ ls
```

Windows:

```
> dir
```

> 注意: 用 del, rmdir 或 rm 刪除檔案是無法回復的，代表 永遠刪除檔案! 所以請小心服用。

### 離開
是時候了！你現在可以安全地關閉命令行。我們用更 hacker 的方法來做這件事，試試看吧？

```
$ exit
```

Windows:

```
> exit
```


### 總結

這裡是一些常用的指令：

指令 (Windows)|指令 (Mac OS / Linux)|描述|例子
:----:|:-----:|:----:|:----:
exit|exit|關閉視窗|exit
cd|cd|修改資料夾|cd test
dir|ls|條列資料檔案路徑|dir
copy|cp|複製檔案|copy  c:\test\test.txt c:\windows\test.txt
move|mv|移動檔案|move c:\test\test.txt c:\windows\test.txt
mkdir|mkdir|新建目錄|mkdir testdirectory
del|rm|刪除目錄/檔案|del c:\test\test.txt
這裡只是一些最基礎的命令行，你可以跑跑看。

如果你還好奇，ss64.com 包含了非常完整所有作業系統的的指令。


# Django

## Django 歷史

Django 是由堪薩斯（Kansas）州Lawrence城中的一個網絡開發小組編寫的。它誕生於2003年秋天，那時Lawrence Journal-World報紙的程序員Adrian Holovaty和Simon Willison開始用Python來編寫程序。

## Django

Django 是個用 Python 寫成的，免費而且開放原始碼的 Web 應用程式框架。他是個 Web 框架 - 就是一堆零件的組成，可以幫助你輕鬆快速的開發網站。

如同當你建立一個網站的時候，你總是需要一些很類似的零件：使用者登入（註冊、登入、登出），網站後台，表單，檔案上傳等等。

幸運的世界上有很多人很久以前就幫你注意到這件事，Web 開發者蓋一個新的網站的時候總是面對著一樣的問題，所以他們合作開發了框架使你可以直接擁有你會用到的零件（Django 就是其中之一）。

各種框架的存在就是拯救你免於重造輪子，當你新建一個網站的時候可以減少重工。

## 框架 （Frameowork）

要真正了解 Django 事實上到底在做什麼，我們需要更了解伺服器。首先就是伺服器需要知道你想要如何來提供你的網頁。

想像一個信箱（埠 port）會偵測寄來的信（請求 request）。

Web 伺服器就是在做這件事。Web 伺服器讀這些信，然後寄出相對的網頁作為回應。但是當你想要寄出某個東西，你需要一些內容，而 Django 就是再幫你產生相對應的內容。

### 當某個人向你的伺服器請求的時候發生了什麼？

當伺服器收到某個請求，這個請求會通過 Django，Django 則負責判斷這個請求是什麼。Django 會先收到網址然後來判斷應該要給出什麼回應。這部分是由 Django 的 urlresolver 來處理（網址其實就是所謂的 URL - Uniform Resource Locator，所以這就是為什麼這裡取名為 urlresolver ）。它不聰明 - 他有一堆範例去判斷這個 URL 符合哪一個範例。Django 則查看範本，如果 URL 符合某一個，Django 就送出這個請求相對應的函數們（在這裡稱為 view ）

想像一個帶著信的郵差。她在街上遊走，確認每家的地址把信送給他們，如果地址對了，她就把信放進去，這就是 urlresolver 在做的事情。

在 view 函數中會做一些有趣的事情：我們會去資料庫中找某些資料。萬一使用者要求要更改某些資料呢？例如某封請求「拜託把我的工作敘述改一下吧」的信 - view 就會檢查你是不是允許他可以做這件事，然後你會在更新了他的工作敘述以後回傳給他一個「完成囉！」的訊息。之後 view 就會產生一個回應，Django 就會將回應送到使用者的瀏覽器上。