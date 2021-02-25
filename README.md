# Python
#### The process of learning and side project
***
#### ***函式***  
* ***函式目的***  
1. 函式為具有名稱的一群指令->為提供程式多次呼叫 (function call)，以避免重複撰寫程式碼  
2. 將相關的程式指令集合再一起，可讓程式更為模組化 (Modularization)  

* ***函式的語法***  
```
def <function_name>(parameters):  
    <body>   #記住本體要縮排
```
```
ex:  
def printsum(a,b):  
    print("兩數之和:",a+b) ＃可用,或+隔開數值與字串差別

a=30
b=50 
printsum(a+2,b+5)
```
Parameter傳值方式有分三種:
->位置參數
```
def fun(a,b,c): #定義
    fun(1,2,3)  #呼叫
```
->鍵值參數  
```
def fun(a,b,c) 
    fun(a=3,b=4,c=5)
```
->預設正式參數值(無預設值必須放在有預設值之參數之前，否則會報錯) 
```
def fun(a,b,c=3):
    fun(1,2)
```


   
