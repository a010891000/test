## Xpath 抓取

到 Chrome 線上應用程式商店，搜尋 XPath 會看到一個名為 XPath Helper 的擴充程式，點選`+ 加到 CHROME`

假設要抓一個網站的連結及標題，如：
[第三天：作一隻最簡單的 Line 聊天機器人](https://ithelp.ithome.com.tw/articles/10192928)

檢視網頁原始碼的方法：
+ `F12`(會從頁面右邊跑出原始碼)
+ `Ctrl+U`(會跑出整個網頁的原始碼)
+ 選取欲抓取的標題，按右鍵並點選檢查。(較快速，能直接看到欲抓取的內容的相關資訊)


```
<h3 class="qa-list__title">
<span class="title-badge title-badge--select">
    達標好文
</span>
<a href="
https://ithelp.ithome.com.tw/articles/10192928
" class="qa-list__title-link">
第三天：作一隻最簡單的 Line 聊天機器人
</a>
</h3>
```

我們看到相關內容的一些資訊，我們要抓取標題及網址，我們在 X path 擴充程式左邊欄位輸入：
+ `//h3/a`        會出現標題
+ `//h3/a/@href`  會出現網址

所以要抓取整個網頁的資料，可以使用此方法抓取，不用打開網頁原始碼使用搜尋一個一個找尋。

## nodepad++ 正規表示法(步驟)

使用XPath Helper 的擴充程式，抓取到的名稱或網址，經過複製並貼上到notepad++

![paste]()

按著`Alt`將前面空白處刪除，按`Ctrl+H`，點擊 **搜尋** 在取代內容輸入 /s+$ 點選全部取代，則會將空格全部取代。

<!--Visual Studio Code 是否也能如此使用? -->