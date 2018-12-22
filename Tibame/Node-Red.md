#初探 Node-Red

## Node-Red 簡介

Node-Red 為 IBM 所開發的視覺化物聯網(IOT)開發工具，主要以流程(Flow)為導向，流程中每個節點代表著動作與功能。

靈活開發的因素：
+ 流程
+ 節點可複製

瓶頸：
+ 複雜且龐大的開發程式(∵在可視覺化的開發程式中會非常混亂)
+ 遞迴 (∵無法停止流程，造成流程無限循環，無法到達下個階段)

優勢：
+ 快速開發
+ 對程式沒有經驗者

常用的
+ inject
+ random
+ msg.plyload

# 如何在 Raspberry Pi 3 上啟動 Node-Red

## 啟動 Node-Red (Raspberry pi 3上)

1. 在樹莓派桌面上啟用 (Menu→Progamming→Node-RED)

會跳出終端機並開始運作，只要顯示 **[info] Started flows** ，代表正常啟動

再打開瀏覽器輸入 http://127.0.0.1:1880  (此 IP 為樹梅派的localhost IP)

Xshell中

```
node-red #啟動Node-Red

node-red-stop #停止運作Node-Red

```

2. 輸入指令：`sudo node-red` (在終端機中)

## 開機自動啟動 Node-Red

輸入指令：(再 Xshell 或是 PuTTY)

```
sudo systemctl enable nodered.service
```

Menu→Shutdown→Reboot

重新登入VNC 及 Xshell，再打開瀏覽器並連線到 Node-Red 畫面。

在其他電腦上用瀏覽器輸入 Raspberry Pi 的 IP 位址再加上 port:1880

範例：http://192.168.0.105:1880/

##  NPM

Node-js 有數十萬種應用程序，需要套件管理庫來管理(npm)

```
sudo apt-get install npm
sudo npm install -g npm@2.x
```

# Node-Red 介面講解

+ Deploy：將編寫好的 Flow 上載至 Raspberry Pi上
+ info：解說各項 Node 的功能
+ Debug：將錯誤訊息與 Debug Node 的資料即時表現

# 常用 Node 介紹

+ inject：觸發開關，可以間隔，定時或手動啟動(Repeat)
+ debug：即時回饋，可以將任意節點的任意變數之值即時顯示到debug Tab，是最常用也最重要的功能
+ comment：評論。不影響流程但是很重要的功能，因為 Node-Red 採用流程圖的表示方式，要養成加上備註的習慣，才不會搞混自己寫的程式(養成註記的使用習慣)
+ random：隨機產生亂數，在測試流程時十分方便

# Social & Ping 

+ E-mail 
    - E-mail有輸出入兩種模組 
    - 它可以經由常見的 E-mail 服務，如 Gmail 與其它可以支援 POP3 的 mail server 進行收發功能
    - Gmail 低階安全性認證： https://www.google.com/settings/security/lesssecureapps?pli=1

# 溫溼度感測器自動啟動

```
sudo systemctl enable pigpiod.service
```

Node-Red

終端機輸入指令顯示溫濕度(前面加入整個過程)

method1

```
cd Adafruit_Python_DHT
cd examples
sudo ./AdafruitDHT.py 11 4
```

method2

```
sudo /home/pi/Adafruit_Python_DHT/examples/AdafruitDHT.py 11 4
```
# MySQL in Raspberry from install to using Node-Red to automatically upload data
[Database](https://www.youtube.com/playlist?list=PL-LuHXHssBEOljS2oz3-gWe-kvXa8zzVb)
# Temperature - Humidity to Dashboard /Gauge by Node-Red
[DHT11 Sensor with Node-RED Part #1 – Install the necessary program](https://www.youtube.com/watch?v=8xyMKAJxDvg)
[DHT11 Sensor with Node-RED Part #2 – Temperature - Humidity to Dashboard /Gauge](https://www.youtube.com/watch?v=xEVYTecXZmw)

port|software|
:----:|:--------:|
80|Apache
1880|Node-Red
3000|Grafana
3306|MySQL
8606|InfluxDB(資料庫)
8888|InfluxDB(圖形顯示)



1. 
2. 
3. 

# 居家溫濕度雲端紀錄

## IoT平台：ThingSpeak

+ ThingSpeak 是一個雲端圖表紀錄服務，主要可以將物聯網裝置所獲得的字料儲存並繪製圖表

+ 各位可以先到 http://thingspeak.com/users/sign_up 進行註冊
