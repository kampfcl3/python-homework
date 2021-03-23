
## 檔案開啟
```
#file.py
f = open('news.txt','r')
print(f.read())
close
```
```
讀取檔案後以閱讀模式 印出news.txt的內容
```
## 讀取模式
```
r - 讀取(檔案需存在)
w - 新建檔案寫入(檔案可不存在，若存在則清空)
a - 資料附加到舊檔案後面(游標指在EOF)
r+ - 讀取舊資料並寫入(檔案需存在且游標指在開頭)
w+ - 清空檔案內容，新寫入的東西可在讀出(檔案可不存在，會自行新增)
a+ - 資料附加到舊檔案後面(游標指在EOF)，可讀取資料
b - 二進位模式
```
## 補充資料
basic(https://ithelp.ithome.com.tw/articles/10161708) 
[python讀寫不同編碼txt檔案](https://www.itread01.com/content/1549798591.html)
[Python 把txt文檔的編碼批量轉化為utf-8](https://blog.csdn.net/weixin_42342968/article/details/104553130)
