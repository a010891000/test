樹莓筆記
===
## 樹莓派 硬體準備
pi3 架構
![](https://4.bp.blogspot.com/-6-gKYTBwmWs/WMaWKx1OEsI/AAAAAAAAPjE/Rre1gbuI4NUdJoN49G0uUlVShLt7Fy0DgCPcB/s640/raspberrypi-3b.jpg)


| 項次 | 名稱 | 說明 |
| -------- | -------- | -------- |
| 1     | 樹莓派   | respberry pi3     |
| 2     | SD卡| 至少8G容量大小 class10(傳輸速度)較好     |
| 3     | 電源  | Micro USB B型接頭 電壓5V     |
| 4     | 網卡  | 有線(RJ45接頭)或無線用USB無線網卡(Pi3內建)     |
| 5     | 遠端  |  一般桌機 筆電    |



## 樹梅派操作系統 Raspbian 安裝方式
1. **買預設卡**
2. **用NOOBS安裝Raspbain**
3. [下載影像檔](https://www.raspberrypi.org/downloads/raspbian/)
![圖片](https://1.bp.blogspot.com/-McR3Xy0qeII/VuwcGT6lwnI/AAAAAAAAMxw/MbHnS-SxgaII5ArZNrfQZ9h1s_7GtgjKQ/s640/clean-installation-and-setup-on-raspbian-jessie-022.jpg)

### 1.用NOOBS安裝
這邊有兩種版本：一般版跟 Lite 版，最主要的差別是在 Lite 版不含 X Window，特別適合用不到圖形介面的朋友，除了容量需求少了很多，系統資源負擔也少了很多。




## Window 環境
下載SD formatted 將SD卡清空
[下載網址](https://www.sdcard.org/downloads/formatter_4/)

## NOOBS安裝注意地方
==**任何大於32GB的SD卡都是SDXC卡 都需要經過exFAX來格式化**==
樹莓派內置GPU 不可更新 ==**只支持FAT文件系統包括FAT16和FAT32**==因此任何大於32GB都需要格式化

**任何大於32GB的SD卡都是SDXC卡 需要使用exFAT文件系統
進行格式化**

## NOOBS SD放入 環境下載步驟
### 系統下載步驟
* step1 先找台電腦安裝NOOBS到記憶卡
![](https://pic.pimg.tw/o4043380/1434876340-1796969555_n.png?v=1434878597)
* step2 安裝Raspbian系統
![](https://pic.pimg.tw/o4043380/1434878574-3856678419_n.jpg?v=1434878597)
* step3 最後看到安裝完成的小視窗 案Enter之後重開 給他跑一下 第一次安裝會到這裡
![](https://pic.pimg.tw/o4043380/1434882439-211838042_n.jpg?v=1434882462)
* step4 選第三個 設定啟動系統
![](https://pic.pimg.tw/o4043380/1434882441-3124712787_n.jpg?v=1434882462)
* step5 擇圖形化的作業系統 以Pi登入
![](https://pic.pimg.tw/o4043380/1434882443-897317711_n.jpg?v=1434882462)
* step6 地區語言選項
![](https://pic.pimg.tw/o4043380/1434882444-2361076773_n.jpg?v=1434882462)
* step7 先選第一個 設定語言
![](https://pic.pimg.tw/o4043380/1434882445-2239259674_n.jpg?v=1434882462)
* step8 按空白鍵 選擇 zh_TW UTF-8 UTF-8 後按Enter
![](https://pic.pimg.tw/o4043380/1434882433-834823602_n.jpg?v=1434882462)
![](https://pic.pimg.tw/o4043380/1434882435-4109694564_n.jpg?v=1434882462)
* step9選 ASIA ENTER 後按TAB 選 Finish 重新開機
![](https://pic.pimg.tw/o4043380/1434882437-2367161434_n.jpg?v=1434882462)
* 安裝 GPIO套件 打開LX終端機(上面工作列) 輸入 ==`sudo apt-get update`== 後給他跑一下
![](https://pic.pimg.tw/o4043380/1434878575-2660701480_n.jpg)
上面完成後換輸入  ==`sudo apt-get  install python-rpi.gpio`==
安裝完就好囉~



### 2.直接下載影像檔
![](https://1.bp.blogspot.com/-McR3Xy0qeII/VuwcGT6lwnI/AAAAAAAAMxw/MbHnS-SxgaII5ArZNrfQZ9h1s_7GtgjKQ/s640/clean-installation-and-setup-on-raspbian-jessie-022.jpg)

### 燒入前需要運用SD formatter
[SD formatter 下載區](https://www.sdcard.org/cht/downloads/formatter_4/)
### window系統燒入
去下載win32Diskimage 將下載好的影像的檔案 讓入裡面寫入SD卡
![](http://2.bp.blogspot.com/-NlSln9tnNao/U9CpY9yscxI/AAAAAAAABhc/xhQkR-ZWgHM/s640/USB%E7%87%92%E9%8C%8401.png)
[win32Diskimage下載位置](https://sourceforge.net/projects/win32diskimager/)


### window初始設定連線(putty pietty MobaXterm)
#### MobaXterm (支援除了 SSH 之外，還支援 SFTP、FTP、VNC、Xdmcp ... 等協定)
[連結位置](http://blog.itist.tw/2016/03/clean-installation-and-setup-on-raspbian-jessie.html)
![](https://4.bp.blogspot.com/-8mXbrQigteU/VuwcGwXhHjI/AAAAAAAAMxY/b-PFhvbrcHwvR1-nIUrGSlK6zXSyJpC9A/s640/clean-installation-and-setup-on-raspbian-jessie-031.jpg)
#### putty

#### pietty



### Mac 系統燒入 
[推薦下載連結](http://www.tweaking4all.com/hardware/raspberry-pi/macosx-apple-pi-baker/)
![](https://1.bp.blogspot.com/-KshJw1ExPZU/VuwcGo6WGYI/AAAAAAAAMxw/z0vCGd6zTegZHL1_-7lPmi0U9_CVDTn8A/s640/clean-installation-and-setup-on-raspbian-jessie-024.jpg)

### Mac連線初始設定(終端設定 , iTerm2)
#### iTerm2
[下載連結](https://www.iterm2.com/)
![](https://3.bp.blogspot.com/-Fdgy23a4Bgg/VuwcHGaKseI/AAAAAAAAMxY/f19t_np5RS0eofN2M0bh0QGzCxSluTA1w/s640/clean-installation-and-setup-on-raspbian-jessie-032.jpg)


### 網路線 接上 連線囉(serial)
#### serial連線法
插上網路線，第一次連線會要求接受 SSH 的指紋碼，預設帳號是 pi，預設密碼是 raspberry。
首先準備 將黑色 白色 綠色 插入6號 8號 10號
![首先準備](http://hophd.com/wp-content/uploads/2016/04/2016-04-19-19.28.04.jpg)

在來進行serial 套件安裝

裝置管理員搜尋安裝完的狀態
![裝置管理員顯示](http://hophd.com/wp-content/uploads/2016/04/2016-04-19_19-33-05.png)
#### **遇到驚嘆號處理辦法**
![serial驚嘆號解決法](https://annhanmovienight.files.wordpress.com/2016/07/img_3506.jpg)

* step1 打開裝置管理員（下圖）先把驅動解除安裝
* step2 控制台>>裝置與印表機>>電腦的圖示按右鍵>>裝置安裝設定（否）>>絕不安裝
* step3 下載驅動程式(PL2303 Prolific Driverinstaller v110)[套件下載](https://www.dropbox.com/s/u2y07mv78i4m5db/PL2303_Prolific_DriverInstaller_v110.exe)
* step4 -   
拔除自己的裝置
右鍵>>以系統管理員執行
第一次他會解安裝（應該是把舊驅動殘餘的檔案移除）
再以系統管理員重新執行一次就會進行安裝

右鍵>>==**以系統管理員執行**==
第一次他會解安裝（應該是把舊驅動殘餘的檔案移除）
再以系統管理員重新執行一次就會進行安裝
* step5 接上自己的裝置就會發現黃色驚嘆號不見了！！

## 第二步驟
[putty安裝](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
**開啟介面**

[putty操作詳細影片說明](https://www.youtube.com/watch?v=uNStEDWnPxY)
**有連線到的呈現**![](https://i.imgur.com/m8vQ5sW.png)

## 本機連線樹莓派 的遠端桌面方法(cable)
* [參考資料](https://www.youtube.com/watch?v=WBlXvGwkZa8)
* 要載入 img黨前 先用SD [formatter](https://www.sdcard.org/cht/downloads/formatter_4/)清除好在燒入
* 在燒入的SD卡內 新增一個SSH的檔案 屬性:file (先創一個文字txt黨 之後刪除txt 即可轉file)
* 在putty 以SSH 連線 ip:raspberrypi.local  登入帳密 帳號:pi 密碼:raspberry
* 之後進入設定 `sudo raspi-config` 到interfacing opinion 啟動VNC
[VNC下載](https://www.realvnc.com/en/connect/download/viewer/windows/)
或者在樹莓派putty的連線視窗打上 `sudo apy-get install tightvncserver` 然後打上'tightvncserver'
* 在VNC Viewer 打上raspberrypi.local 帳密 同 putty登入時 帳號:pi 密碼:raspberry
* 完成

## WIFY連線
在樹莓派VNC連線後 點擊右上角的 雙螢幕 點擊 輸入wify的密碼 即可連線

#### 指定連線wify的工具
在命令提示字窗 下達 `sudo apt-get install wicd-gtk` 下載工具wicd-gtk

## 藍芽工具下載
在命令提示字元打上 `sudo apt-get install blueman`
## 若是下載的時候出問題
在命令提示字元 輸入`sudo apt-get update --fix-missing` 然後再輸入要載入的套件一次

## 再來就是輸入帳密的過程囉!!
1. 因為我的port是COM4 裝置管理員上的 所以在putty打com4
![](https://i.imgur.com/Xd50ggq.png)

2. putty serial 設定
![](https://i.imgur.com/z7bOm0K.png)

3. 預設帳號是 pi，預設密碼是 raspberry。 打完如下表
![](https://i.imgur.com/te0pncg.png)


## 進入設定介面 在命令端輸入
語法:`sudo raspi-config`
![](https://3.bp.blogspot.com/-d1T3sqmGqJo/VuwcHcYewGI/AAAAAAAAMxY/pP1fLzno4RYnaqXtdq0p4VbYWHtHo7mFw/s640/clean-installation-and-setup-on-raspbian-jessie-034.jpg)



## 初始環境設定
![](https://i.imgur.com/kduCExQ.png)

### 選項說明


* 1 Change User Password
修改 pi 帳號的密碼。
點進去


* 4 Localisation Options
修改地區及語系設定。
點進去
![](https://i.imgur.com/L6RKlpq.png)


* 6 Overclock
Raspberry Pi 1/2 最高可以超頻到 1GHz，但是 Raspberry Pi 3 不支援，可能因為 CPU 太燙，再超下去的話會短命。


* 9 Advanced Options
A2 Hostname

* 11 Change Locale
取消 en_GB.UTF-8 UTF8，改成 zh_TW.UTF8 UTF8；如果像我一樣喜歡看英文訊息的話，就選擇 en_US.UTF8 UTF8。


* 12 Change Timezone
將時區指定到 Asia / Taipei。
![](https://i.imgur.com/DRteane.png)

* 14 Change Wi-fi Country
由於 Raspberry Pi 3 支援 WiFi，所以多了頻段的選項，請選擇 TW Taiwan。
![](https://i.imgur.com/PYjIEMp.png)




## 更新系統套件
* 初始設定完成之後，最後的工作就是更新一下系統了，同步一下官方套件庫的資訊。
語法:`sudo apt-get update`


* 由於是全新安裝，所以我們將所有的套件及相依套件都更新到最新的版本。
語法:`sudo apt-get -y dist-upgrade`


* 更新完畢後，同樣重新開機一下。
語法:`sudo reboot`

* 確認一下所有的服務與元件的狀況，目前所有載入的核心模組有這些。
語法:`lsmod`

* wify確認
語法:`iwconfig`

* BLE確認
語法:`hciconfig`

* 設定系統自動校時
語法:`sudo timedatectl set-ntp yes`


* 文字編輯器vi vim設定
語法:`sudo vi /etc/vim/vimrc.tiny

* 而單一使用者的設定檔自然就存到使用者各自的設定檔中。  
vi ~/.vimrc

-   自動顯示行號。  
    set nu
-   修正四個方向鍵無效。  
    set nocompatible
-   修正 BackSpace 按鍵無效。  
    set backspace=2






## 中文介面 與 輸入法
安裝酷音中文輸入法:`sudo apt-get install scim-chewing`
安裝其他中文字型:`sudo apt-get install ttf-wqy-microhei ttf-wqy-zenhei xfonts-wqy`


## 中文化...

要使中文桌面正常顯示
pi@raspberrypi ~ $ `sudo aptitude -y install task-chinese-t-desktop`

Raspberry Pi 樹莓派更改鍵盤配置成 us
編輯 /etc/default/keyboard
sudo nano /etc/default/keyboard
**把 XKBLAYOUT="gb" 改成 XKBLAYOUT="us"**

KEYBOARD CONFIGURATION FILE

Consult the keyboard(5) manual page.

XKBMODEL="pc105"
**XKBLAYOUT="us"**
XKBVARIANT=""
XKBOPTIONS="lv3:ralt_switch"

BACKSPACE="guess"


### 遠端桌面連線協定
工具:xrdp
[官網](http://www.xrdp.org/)





### 有線 或 無線 的DHCP 設定或固定IP設定
主要是在 `/etc/network/interfaces` 檔案


更新SD卡
1.點擊窗口終端:
2.更新語法:`sudo apt-get update`
檢查是否有足夠空間:`df -h`








## debian9 安裝注意事項
[安裝程序](https://www.server-world.info/en/note?os=Debian_9&p=install)
#### 代名詞
* GRUB:磁盤區
* 

程式碼
進入樹莓派 設定用:`sudo raspi-config`
進入桌面環境:`startx`


## Linus 
* 安裝中文字形:`sudo apt-get install ttf-wqy-zenhei ttf-wqy-microhei xfonts-wqy`
* 安裝中文輸入法:`sudo apt-get install ibus ibus-chewing`
* 安裝遠端桌面服務:`sudo apt-get install xrdp

## windown與樹莓派的資料傳輸(WIFY為例)
[參考影片](https://www.youtube.com/watch?v=W2zQxEO0t2A)
* 工具:winscp
* 開啟winscp 選擇新的伺服器 選擇SFTP  hostname:樹莓派IP
* 運用`ipconfig` 可以從gateway 可以運用gateway的IP 打在網址上 透過登入 得知樹莓派真正的ip
* WINSCP帳密 樹莓派帳密

## 資料參考
[連線 wify](https://www.youtube.com/watch?v=fLtsXwdM4n0&list=PLkpY6D9q0Zg6MxfR1sFgXEfJTRjwJr9Jv)

## 語法
關閉系統:`sudo shutdown -h now`

启用root账户    
root账户默认没有密码，但账户锁定   
需要root权限时，由sudo执行    
[pi@raspberrypi](mailto:pi@raspberrypi) ~ $  sudo su -    
  
重新开启root账号，可执行    
[pi@raspberrypi](mailto:pi@raspberrypi) ~ $  sudo passwd root   
  
再执行以下命令解锁账户    
[pi@raspberrypi](mailto:pi@raspberrypi) ~ $  sudo passwd --unlock root


直接查詢樹莓ip:`hostname -i`