# 樹莓派3

## Raspberry pi 基本介紹

### Raspberry pi 簡介
+ Node-red 不同的操作系統對樹莓派操作的差異
    - Windows 需搭配 XShell 使用
    - OS X 和 Linux 可直接使用指令輸入

+ 樹莓派(Raspberry Pi)是一種基於 Linux 的單機版電腦，且可當開發版，也可當多媒體播放器、檔案伺服器、 Web Server 等多種應用。
    - GPIO(General-purpose input/output)：通用型輸入輸出簡稱，其接角可供使用者由程是控制並自由使用。
    - GPIO 可接上各式各樣的擴充版、馬達或電器設備。

### 家族介紹（發行順序由上往下）
    - Raspberry Pi A
        * 體積較小
        * 價格較便宜（約 25 美金）
    - Raspberry Pi B (基準)
        * Braodom設計
        * 700 MB/Hz
        * 記憶體 256 MB / 512 MB
        * 價格：約為 35 美金
    - Raspberry Pi B+
        * 消除 V 端子
        * 增加兩個 USB
        * 更多的 GPIO
    - Raspberry Pi 2
        * 四核心 900 MB/Hz
        * 記憶體 1G
    - Raspberry Pi Zero
        * 效能介於 B+ 和 2 之間
        * 價格最便宜（約 5 美金），但因易缺貨造成價格不固定
    - Raspberry Pi 3
        * 四核心 1.2 G/Hz
        * 無線網路(可少買一個網卡)
        * 無線藍芽

樹莓派差異（B型）

配置|第一代|第二代|第三代
----|------|-----|------
USB孔|  2  |  4 |   4  
GPIO PIN數|26|40|40
記憶卡種類|SD|MicroSD|MicroSD
記憶卡放置|按壓式|按壓式|插拔式
wifi|無|無|802.11 和 藍芽 4.1

## Raspberry pi 環境建置

### 設定網路

2016/03/18前，樹莓派要設定網路必須要先接受螢幕、鍵盤及滑鼠，才能從設定介面內，設定無線網路 ID 及密碼。但因 Raspberry pi 3 問世後，因為其內建無線網路，可直接透過設置擋寫入執行，上載到樹莓派作業系統並連線網路。

新增文件檔(.txt)在 SD 卡內，並在文件檔內輸入以下內容並儲存

```
country=TW
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="無線網路名稱"  **根據使用的無線網路做更改，且大小寫和下底線有差，所以要照上面的 SSID 輸入**
    psk="無線網路密碼"
}
```

將新增的文件檔案名稱更改為 wpa_supplicant.conf      **.txt要記得刪除**

`新文字文件.txt　→　wpa_supplicant.conf`

接下來退出記憶卡，並插進樹莓派即可。

### 周邊連線





# 資料來源

*[Raspberry Pi 1, 2, 3 compared. See the differences](https://www.stewright.me/2016/03/raspberry-pi-1-2-3-compared/)

*[樹莓派](https://zh.wikipedia.org/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE)


