#初探 Node-Red

## Node-Red 簡介

Node-Red 為 IBM 所開發的視覺化物聯網(IOT)開發工具，主要以流程(Flow)為導向，流程東每個節點代表著動作與功能。

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

## 啟動 Node-Red (Raspberry pi3上)

1. 在樹莓派桌面上啟用 (Menu→Progamming→Node-RED)

會跳出終端機並開始運作，只要顯示 **[info] Started flows** ，代表正常啟動

再打開瀏覽器輸入 http://127.0.0.1:1880(此 IP 為樹梅派的localhost IP)

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