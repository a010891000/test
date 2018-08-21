# 錯誤指令

pip Import Error:cannot import name main解決方案

在使用pip來進行安裝操作時碰到這樣的問題： 

```
:~$ pip install django --upgrade
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main
```

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
