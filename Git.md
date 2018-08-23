# Git

Git 是一個分散式版本控制軟體，最初由林納斯·托瓦茲(Linus Torvalds)創作(Linux作者)。最初目的是為更好地管理Linux內核開發而設計。

很多著名的軟體都使用git進行版本控制，其中包括Linux內核、X.Org伺服器和OLPC內核等專案的開發流程。

## 主要功能

Git 是用於 Linux 內和開發的版本控制工具，他採用了分散式版本庫的作法，不需要伺服器端軟體，就可以運作版本控制，使得原始碼的是出汗交流及其方便。 Git 的速度很快，這對於諸如 Linux 內核這樣大專案來窩自然很重要。 Git 最為出色的是它的合併追蹤 (merge tracing) 能力。

# 完整學會 Git GitHub Git Server 的24堂課

## Git、誰與爭鋒

版本控制系統（Version Control System, VCS）是程式管理軟體的通稱，它是用來保存程式檔的修改紀錄，以及歷史版本，以便於日後檢視或是使用。

最早期的系統是採用集中控管的方式。在完成修改和回傳之前，其他人都不能更動這個程式碼（如Google簡報）。這種方式有效避免「衝突」發生（也就是不同人，同時修改同一段程式碼，造成混淆的情況）。

但是付出的代價是效率降低。因為如果有人想要修改的檔案正好有別人正在修改，就必須等程式檔回傳才能動手修改。要修改的人一多，相互等待所造成的時間浪費將非常可觀。

新的 VCS 則採用分散式的作法。每一個人隨時都可以取得任何一個程式檔來修改，等到送回 VCS 的時候，再視需要進行合併(merge)

現在有愈來愈多軟體公司開是使用 Git  管理程式專案，網路上也有專門提供 Git Server 服務的網站，如： GitHub 、 GitLab。

### 1.1 安裝與使用 //摘要

官方網站的下載網址： http://git-scm.com/downloads


1. 安裝 Git
+ 如果是 Windows 平台，請在安裝選項設定頁面中勾選 Git Bash Here 和 Git GUI Here

2. 安裝完畢後，建立一個新的資料夾(資料夾名稱可以是中文或英文) 

3. 啟動 Git Bash 程式
 
```
cd '資料夾路徑'
```

4. 讓 Git 管理資料夾，輸入下列指令

```
git init
```
Git 會回應訊息「Initialized empty Git repository in 資料夾路徑/.git/」，表示已經完成準備工作。

5. 建立一個新的文字檔來測試 Git 如何管理檔案，將文字檔命名為 poem.txt ，並在文字黨內輸入一行文字：空山新雨後 
 
6. 回到 Git Bash 程式，輸入下列指令：

```
git add poem.txt
git status //顯示目前 Git 的狀態
```

Git 會回應訊息

```
On branch master

Initial commit

Changes to be commited:
	(use "git rm --cached<file>..." to unstage)
	
		new file: poem.txt
```

這個訊息是表示說，顯再有個名稱叫做 poem.txt 的新檔案將要被送進檔案庫儲存。

7. 上一步是準備把檔案送進 Git 檔案庫，現在要確實送進去
輸入下列指令：

```
git commit -m '這是作業的說明'  --author='操作者姓名<email信箱>'
```

Git 會回應訊息，顯示是誰執行這項工作，有幾個檔案被更動：

```
[master (root-commit) 57d02a7] first commit
Author: 操作者姓名 <email信箱>  //誰執行這項工作
1 file changed, 1 insertion(+)  //有一個檔案被更動，總共加入一行文字
create mode 100644 poem.txt     //被更動的檔案名稱
```

如果執行 commit 指令以後，想要修改作業說明或是操作者資料，可以使用 `--amend`

```
git commit --amend -m '新的作業說明' --author='操作者姓名'<email信箱>
```

8. 修改 poem.txt 檔案的內容，加入第二行內文字

```
空山新雨後
天氣晚來秋 //這是新加入的文字
```

9. 回到 Git Bash 程式，輸入下列指令，將修改後的 poem.txt 送進檔案庫儲存

```
git add poem.txt
git commit -m '這是作業的說明'  --author='操作者姓名<email信箱>'
```

10. 查看目前檔案庫有哪些檔案，執行以下指令，啟動圖形檢視模式：

```
gitk //要在檔案庫資料夾的路徑下
```

![用圖形檢視模式觀察檔案庫](https://raw.githubusercontent.com/a010891000/test/master/image/Git/graphic_view_mode.png)

如圖，左上角會有不同顏色的小節點，每個節點表示執行一次 `git commit`指令。節點右邊會顯示輸入作業說明的第一行文字；左下角視窗會顯示目前選定節點完整資料。最上面的節點會多出一個 master 標籤，表示這是檔案的 「主要分支(branch)」。

節點會依照時間順序由上往下排列，最上面是最近一次 commit 。節點視窗的右邊兩個視窗，分別為顯示執行指令的人和時間。

右下角的視窗是目前選定的 commit 節點的內容，它有兩種檢視模式： patch 和 tree

檢視模式|功能
--------|:-------
patch|顯示和前一個 commit 節點的差異 
tree|顯示完整的節點內容




如果沒有在檔案庫的資料夾下輸入：

![404](https://raw.githubusercontent.com/a010891000/test/master/image/Git/not_found.png)

11. 檢視完檔案庫，結束圖形操作模式，回到 Git Bash 程式，輸入下列指令，離開 Git Bash

```
exit
```

Git 會把目前的執行狀態記錄在資料夾內，下次再啟動 Git Bash 程式，回到這個資料夾時，會自動回復到離開時的狀態。

#### 補充說明

1. Git 可以管理任何一個資料夾中的檔案和子資料夾，**只要在該資料夾中執行「 git init 」** ，就能讓 Git 完成管理前的準備工作。 Git 會在這個資料夾建立所謂的 repository(檔案庫)，裡面儲存被管理的檔案和資料夾內容，包括所有曾經被加入的歷史版本。

2. 「檔案庫」其實就是名稱叫做「.git」的子資料夾，預設它會被隱藏起來。

3. Git 可以正確處理中文名稱的檔案和資料夾，只是 Git Bash 程式在顯示中文的時候會出現亂碼， gitk 圖形檢視模式，它可以正確顯示中文。

```
加入 UTF-8 設定，避免檔案交換處理編碼錯誤

git config --global core.quotepath false
git config --global	gui.encoding utf-8
git config --global	li8n.commit.encoding utf-8
git config --global	li8n.logoutputencoding utf-8
git config --global	export LESSCHARSET = utf-8
```

4. 執行 `git help -a`則顯示完整的指令清單；執行 `git 指令 --help` 例如： `git init --help` 則會顯示該指令的網頁說明檔案。

5. 如果指令太長，像要換到下一行繼續輸入，可以用反斜線字元 '\' 結尾，然後按下 Enter 鍵，繼續輸入。

### 1-2 瞭解 Git 的運作方式 

操作 Git 的基本流程：

1.修改檔案
2.執行 `git add` 指令

指令

+ `git add`：將檔案內容加入 Git 系統的索引
+ `git commit`：將檔案內容存入檔案庫

![把檔案存入Git檔案庫的流程](https://raw.githubusercontent.com/a010891000/test/master/image/Git/process_of_git.png)

#### 補充說明

有些 Git 指令執行的時候會顯示出英文訊息，裡頭會包含 Git 專用的術語，以下就是專用術語的說明：

1. working tree：目前 Git 正在管理這個資料夾，因為資料夾是一個樹狀結構。

2. index： Git 系統索引。把檔案內容加入 Git 索引又稱為 stage 或 cache ，把檔案從索引中移除稱為 unstage。

3. repository： Git 檔案庫，就是 Git 儲存檔案的地方。

最後再做一個測試來澄清一個容易被初學者誤解的現象。

1. 啟動 Git Bash 程式，利用 cd 指令切換到剛才的工作資料表

2. 開啟 poem.txt 檔，加入第三行文字：

```
空山新雨後
天氣晚來秋
明月松間照 //這是新加入的文字
```

3. 將修改後的檔案內容加入 Git 系統的索引：

```
git add poem.txt
```

4. 再度開啟 poem.txt 檔，加入第四行文字：

```
空山新雨後
天氣晚來秋
明月松間照
清泉石上流 //這是新加入的文字
```

5. 執行 `git commit` 指令

現在執行 gitk 指令啟動圖形檢視模式，看看檔案庫中的 poem.txt 檔事顯示三行文字或是四行文字，結果發現只有三行文字，最後加入的第四行文字並沒有被送進檔案庫儲存。

這是因為執行 `git add` 指令時，只有把當下的檔案內容加入到 Git 索引。如果之後檔案內容又被修改，必須再次執行 `git add` 指令才會更新 Git 索引。**需要特別注意**

## Git 設定檔的妙用

每一個軟體都有設定檔，它可以決定程式要如何執行。

Git 有三個不同層級的設定檔，它們有不同的優先權，高優先權檔案的設定項目會覆蓋低優先權檔案中相同的設定項目。以下依照優先權由高到低依序介紹：

1. 資料夾內 `.git` 子資料夾中的 **config** 檔

這個設定檔具有最高的優先權

舉例來說，如果這個設定檔設定 A=B 就算其他兩個設定檔設定 A=C ，最終生效的還是 A=B。但是此設定檔只對它所在的檔案庫有效。

2. 登入帳號的 home directory 內的 **.gitconfig** 檔

只有前一個設定檔中沒有設定的項目，這個設定檔的設定才會生效，而且這個設定檔只對此帳號登入的使用者生效。

3. Git 程式的安裝資料夾內的 **etc\gitconfig** 檔

只有前兩個設定檔中沒有設定的項目，這個設定檔的設定才會生效，這是公用的設定檔，它對所有登入帳號和所有 Git 檔案庫都有效。

### 2-1 git config 指令的用法

顯示目前 Git 的設定值可以執行下列指令：

```
git config -l
```

就會顯示出執行後的畫面(顯示的順序是由優先權低依序到優先權高)

![執行 git config -l 指令的顯示畫面](https://raw.githubusercontent.com/a010891000/test/master/image/Git/git_config.png)

B部分是顯示檔案庫資料夾內 **.git** 子資料夾中的 config 檔的設定，想只看這部分設定可輸入下列指令：

```
git config --system -l
```

C部分是顯示登入帳號 home directory 內的 **.gitconfig**檔的設定，想只看這部分設定可輸入下列指令：

```
git config --global -l
```

我們可以指定要把操作者姓名和 email 紀錄在哪一個設定檔，如果要記錄在檔案庫中的設定檔，可輸入下列指令：

```
git config user.name "操作者姓名"
git config user.email "操作者email"
```

如果要記錄在登入帳號的 home directory 內的 **.gitconfig**，可輸入下列指令：

```
git config --global user.name "操作者姓名"
git config --global user.email "操作者email"
```

如果要記錄在 Git 程式的安裝資料夾內的 **etc\gitconfig**，可輸入下列指令：

```
git config --system user.name "操作者姓名"
git config --system user.email "操作者email"
```

我們可以利用 `git config` 指令的選項決定要寫入哪一個設定檔
+ `--global` : home directory 內的 **.gitconfig**的設定檔
+ `--system` : Git 程式資料夾內的 **etc\gitconfig**的設定檔

要移除設定檔中的項目，可使用`unset`指令，麗如要移除檔案庫設定檔中的操作者姓名，可輸入下列指令：

```
git config --unset user.name
```

如果要移除其他設定檔的項目，視情況加入 `--global` 或是 `--system`

#### 補充說明

git 指令的「長」選項和「短」選項
+ 長選項：使用二個連結字元開頭，例如：-m
+ 短選項：使用一個連結字元開頭，例如：--author

其實使用一個連結字元開頭只是簡略的形式，也可以轉換成完整的形式，例如：

簡略形式|完整形式
--------|--------
git commit -m 說明|git commit --message 說明
git commit -l | git commit --list

**並非每一個選項都有簡便的形式**

因為現在的人都習慣圖形介面的程式，所以需要輸入指令會覺得較為麻煩。尤其是長度較長的指令再搭配上選項，令人頭昏眼花。

為了提高便利性，我們可以定義指令的別名(alias)，是利用簡短的縮寫來表示正規指令。只要輸入我們定義的「指令別名」， Git 系統會自動把它換成正式的指令。

定義指令別名的方法如下：

```
git commit alias.指令別名 '正式的指令和選項'
```

例子：

```
git commit alias.con 'config -l'
```

執行以上指令，會在檔案庫的 config 設定檔中新增一個 alias 項目，然後就可下指令顯示 Git 的設定，結果等同於執行 `git config -l` ：

```
git con //alias 後的 con 代替正式指令 commit -l
```

移除 alias

```
git commit -unset alias.con
```


注意：

+ **指令別名** 不可包含空格
+ **正式的指令和選項** 就是下指令時，在 git 之後輸入的那串文字。**如果裡頭沒有空格，可以省略單引號**

### 2-2 檔案比對程式

`git diff` 指令是用來執行檔案比對的功能，它可以比對目前資料夾中的檔案，和檔案庫中最新的版本，或是已經加入索引的版本（也就是執行 git add 的檔案）之間的差異

例如： 

```
index d99f9f0..793116e 100644
--- a/poem.txt
+++ b/poem.txt
@@ -1,3 +1,3 @@
-11111
 22222
 33333
+44444
```

@@後面的數字
+ -1,3 : 表示以下資料是a檔案中第一行開始後面3行，「-」只是表示a檔案
+ +1,3 : 表示以下資料是b檔案中第一行開始後面3行，「+」只是表示b檔案

「-」只是開頭表示a檔案變成b檔案的時候，這一行被加入
「+」只是開頭表示a檔案變成b檔案的時候，這一行被刪除

沒有正負的開頭的部分表示沒有被修改

其實在 Git 的資料夾下 輸入 `gitk` 可以用圖形介面模式觀看差異

## 把檔案存入Git檔案庫

### 3-1 排除不需要加入的檔案庫的檔案

Git 會將檔案和資料夾分為三類：
1. 被忽略的 (tracked) ：檔案處與此狀態，表示檔案已經被加入 Git 檔案庫。
2. 忽略的 (ignored) ：檔案處與此狀態，表示 Git 不要檢查這個檔案。
3. 不被追蹤的 (untracked) ：檔案處與此狀態，表示檔案尚未被歸類。

一開始的時候，所有檔案都是 untracked 。執行 `git status` 指令，就會顯示 untracked 檔案清單。(提醒那些檔案商未被歸類)

要讓檔案變成 ignored 狀態，需要在資料夾中建立一個名為 **.gitignore** 的檔案，並將要忽略的檔案逐一列在檔案裡頭(一個檔案一行)

#### 動手試看看

1. 建立一個新的資料夾
2. 啟動 Git Bash 程式，利用 cd 指令切換到這個資料夾，或是對此資料夾，點擊右鍵，選擇 Git Bash Here
3. 執行 git init
4. 建立三個文字檔： poem1.txt 、 poem2.txt 和 poem3.txt

以下是文字檔的內容：

poem1.txt

```
細草微風岸
桅強獨夜舟
```

poem2.txt

```
黃河之水天上來
奔流到海不復回
```

poem3.txt

```
朝辭白帝彩雲間
千里江陵一日還
```

5. 回到 Git Bash 程式，執行 `git status` 指令。畫面會顯示以下訊息(告訴我們資料夾中有**有3個 untracked 檔案 ** 

![git status with untracked](https://raw.githubusercontent.com/a010891000/test/master/image/Git/git_status.png)

6. 現在將 poem1.txt 加入 Git 檔案庫，輸入下列指令

```
git add poem1.txt
git commit -m '1st commit'
```

7.  建立一個 **.gitignore** ，可直接在 Git Bash 程式中執行指令

```
touch .gitignore
```

8.  開啟**.gitignore**，輸入下列內容。(∵ **.gitignore** 檔案本身也在資料夾中，所以要把它列為 ignored 檔案之一)

```
.gitignore
folder
```

9. 執行 `git status` 現在程式會顯示 poem2.txt 和 poem3.txt 是 tracked  

![git status](https://raw.githubusercontent.com/a010891000/test/master/image/Git/git_status_add_poem1.png)

10. 開啟 poem1.txt 、 poem2.txt 和 poem3.txt ，修改內容。

poem1.txt

```
細草微風岸
桅強獨夜舟
星垂平野闊 // 新加入的文字
月湧大江流 // 新加入的文字
```

poem2.txt

```
黃河之水天上來
奔流到海不復回
高堂明鏡悲白髮 // 新加入的文字
朝如青絲暮成雪 // 新加入的文字
```

poem3.txt

```
朝辭白帝彩雲間
千里江陵一日還
兩岸猿聲啼不住 // 新加入的文字
輕舟已過萬重山 // 新加入的文字
```

11. 再次執行 `git status` ，現在程式會顯示以下訊息

![git status](https://raw.githubusercontent.com/a010891000/test/master/image/Git/git_status_moified_poem1.png)

另外關於 **.gitignore** 檔案的用法，另外在下方補充說明：

1. **.gitignore** 檔案的影響範圍是它所在的資料夾和所有子資料夾。

2. 每個資料夾都可以建立自己的 **.gitignore** 檔案，如果它上層的資料夾也有 **.gitignore** 檔案，這個資料夾也會上層的影響。

3. **.gitignore** 檔案中用符號開頭
+ #　：表示註解
+ /　：資料夾路徑
+ *　：檔案名稱
+ !　：表示排除

例如以下設定表示要忽略所有副檔名是 txt 的檔案，但是不包括 note.txt

```
*.txt
#設定不要忽略 note.txt
!note.txt
```