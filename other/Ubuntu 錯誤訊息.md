# 錯誤指令

pip Import Error:cannot import name main解決方案

在使用pip來進行安裝操作時碰到這樣的問題： 

![pip_error_message](https://img-blog.csdn.net/20180426112703696?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RpbnRpbmV0bWlsb3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

後來發現是因為將pip更新為10.0.0後庫裡面的函數有所變動造成這個問題。 

解決方案：

1. 呼喚出 pip 檔案

```
sudo gedit /usr/bin/pip
```

2. 將原來的：

```
from pip import main
if __name__ == '__main__':
    sys.exit(main())
```

3. 改成：

```
from pip import __main__
if __name__ == '__main__':
    sys.exit(__main__._main())
```

就OK了
