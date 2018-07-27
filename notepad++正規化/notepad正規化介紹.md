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

![paste](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/1.paste.png)

按住`Alt`，向下向右選取，並將空白處刪除

![alt](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/2.alt.png)

按`Ctrl+H`，會跳出 **取代** 視窗。在 **尋找內容** 輸入`\s+$` (可砍空白) → 勾選 **規格運算式** → 點選 **全部取代**

![\s+$](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/3.s+$.png)

按`Alr+C`，會跳出 **直行編譯** 視窗，選擇插入數字，初始數字填 1 ，增量填 1 ，勾選齊頭補零
![number](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/4.number.png)

按下編輯，結果如下

![sort](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/5.sort.png)

按`Alr+C`，會跳出 **直行編譯** 視窗，選擇插入文字，輸入.[]()

![text](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/6.text.png)

按下編輯，結果如下

![add](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/7.add.png)

按`shift+Alt`+方向鍵選取需要的範圍，並剪下貼上

![add](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/7.add.png)

貼上後結果如下，文字都會在[]內

![add](https://raw.githubusercontent.com/a010891000/test/master/notepad%2B%2B%E6%AD%A3%E8%A6%8F%E5%8C%96/img/7.add.png)

**要使用markdown格式，必須先貼網址**

因為標題長度不固定，如果先貼標題名稱會致使網址無法完全在()內

<!--Visual Studio Code 是否也能如此使用? -->