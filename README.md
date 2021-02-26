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

* ***函式的回覆值與執行流程***  

```
def <function_name>(parameters):  
    <body>   #記住本體要縮排
    return <value> #return後可接一個或多個值或表示式
```
ps:函式定義必須要再呼叫函式之前，不然會出現錯誤。且如沒有寫明回覆值(return)，那麼預設回覆值就是``None``  

* ***函式的參數與變數***  
＊「區域變數」->只能在函式內使用，在函式外面就無法使用  
ps1 :在函式中，在指派指令左方使用變數名稱，python就會產生一個區域變數  
ps2: 區域變數只能在其所定義中的區域中使用，區域外就無法使用，其壽命執行時開始，執行完畢就結束  
＊[全域變數]->變數在所有地方皆可使用  



