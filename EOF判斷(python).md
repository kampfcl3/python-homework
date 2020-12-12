```
c語言中可以使用while(scanf(“%d”,x) !=EOF)，python則有這兩種寫法可以代替
```
## 用sys.stdin
```
import sys 
for line in sys.stdin: 
    a=int(line) 
    if a!=0: 
        print(a)
```
## 用try…except
```
try:
    while True:
        s = input()
except EOFError:
    pass
```
