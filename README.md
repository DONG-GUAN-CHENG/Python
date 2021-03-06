# Python
#### The process of learning and side project
***
#### ***函式***  
* ***函式目的***  
1. 函式為具有名稱的一群指令->為提供程式多次呼叫 (function call)，以避免重複撰寫程式碼，使程式的可讀性增加  
2. 將相關的程式指令集合再一起，可讓程式更為模組化 (Modularization)  
3. 會將函式內縮的程式區塊儲存在記憶體中，用函式名稱綁定。直到程式呼叫函式時才會真正執行程式  
4. 函式也一樣是物件，任何可以放物件的地方，像是運算式、參數、傳回值...等等

* ***函式的語法***  
```
def <function_name>(parameters):  
    <body>   #記住本體要縮排，若無參數仍須保留小括號
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

```
argument VS parameter  
parameter(參數):指的是定義函式時的形式變數，數值未定，可以說是佔位置用的place holder
argument(引數):必須等到程式呼叫時才真正傳入參數值，這時才會把參數值填入參數的位置。像以下三種都是引數如何代入參數位置的方法
```
->位置參數法
```
def fun(a,b,c): #定義
    fun(1,2,3)  #呼叫
```
->鍵值參數法(指名參數法)  
```
def fun(a,b,c): #定義
    fun(a=3,b=4,c=5)  #呼叫
```
->預設參數法：預設正式參數值(無預設值必須放在有預設值之參數之前，否則會報錯)，跟指名參數法不同，在定義函式時使用，是代表參數的預設值
```
def fun(a,b,c=3):
    fun(1,2)

ps:在呼叫函式時，若省略該參數，參數值就會使用預設值
```

PS:可以使用``help(函式名稱)``就可得知函式的參數名亥相關的說明  

* ***函式的回覆值與執行流程***  

```
def <function_name>(parameters):  
    <body>   #記住本體要縮排
    return <value> #return後可接一個或多個值或表示式
```
ps:函式定義必須要再呼叫函式之前，不然會出現錯誤。且如沒有寫明回覆值(return)，那麼預設回覆值就是``None``  

* ***函式的參數與變數***  
變數的有效範圍遵守LEGB原則->``Local(函式內)->Enclosing(外一層函數)->Global(主程式)->Built-ins(內建變數或函式)``，只會往外找，不會往外找。當看到變數必須在同層看有沒有建立該變數，沒有的話則往外層找  
＊「區域變數」->只能在函式內使用，在函式外面就無法使用  
ps1 :在函式中，在指派指令左方使用變數名稱，python就會產生一個區域變數  
ps2: 區域變數只能在其所定義中的區域中使用，區域外就無法使用，其壽命執行時開始，執行完畢就結束  
＊「全域變數」->變數在所有地方皆可使用  
ps1: 在函式不要輕易使用全域變數，很容易會有問題產生。應該以參數方式將值傳給函式  
ps2: 當區域變數名稱與全域變數名稱相同，區域變數會遮蓋(shadow)全域變數

```
def square(x):
    power = 4 
    y = x**power
    return y


power = 2
result = square(10)
print(result)
print(power)

Ans: 10000,2
```
* ***定義及使用主函式***  
一般程式包含主程式及函式。將主程式轉為主函式可讓我們的程式更加模組化(Modularization)  
```
def main():  ＃將主程式改寫為main()函式
    <body>
main()  #呼叫
```

* ***支援程式匯入而不立即執行***  
我們所寫的函式，也可以提供其他人匯入使用。先匯入不立即執行，需要時再呼叫，如同匯入模組一樣  

呼叫語法為``<ModuleName>.<functionName>``或``<ModuleName>.<VariableName>``。匯入模組只需寫主檔名，不需加入副檔名``.py``
```
import draw #draw為draw.py檔裡面內含許多函式 ex:drawfun

draw.drawfun(參數)

```
* ***匯入在其他套件裡的模組***  
上述所提都是以匯入與被匯入模組都在同一目錄下，但專案常會依不同功能建立不同的套件目錄，例如:  
```
project/
   packageA/
      __init__.py
      modA.py
      ...
   packageB/
      __init__.py
      modB.py
      ...
 ```
* 專案 (Project) 根目錄： project/  
✶ 套件 (Package) 目錄：packageA/, packageB/, ...，因為這些目錄裡都有 __init__.py 檔案 (內容可以是空的)，因此 Python 認定為套件，允許匯入模組  
✶ 模組 (Module)：__init__.py, modA.py, modB.py, ...  
ex:
```
from packageA import modA
modA.drawfun(...)
...
```
可嘗試在 if __name__ == '__main__': 指令前加上一行 print(__name__)，分別觀察執行或匯入模組的 __name__值->來確定程式是被匯入還是被執行，如果是被執行就呼叫 main() 函式，否則就不呼叫  

* ***不定數目的參數 *args和 **kwargs 的打包***  

->用*args來接收不定數目的位置參數  
在定義函式時，可以用``「*args」``來接收``不定數目的位置參數``，其中arg表示argument，在函式被呼叫時，所有從 *args 位置開始所對應的參數會被打包成tuple指定給args參數。  
```
ex:
def prnsum(name,*args):
    print(name,args,'=',sum(args))
prnsum("加總",1,2,3,4)

ANS輸出:加總 (1,2,3,4)=10
```
->用**kwargs來接收不定數目的指定參數  
在定義函式時，可以用``「**kwargs」``來接收``不定數目的指名參數``，在呼叫時對應的參數會被打包成dict在指定給kwargs("參數名=參數值"，符合dict格式)
```
ex:
def prnsum(name,**kwargs):
    print(name,kwargs)
prnsum("飲料",紅茶=40,綠茶=30,咖啡=70,)

ANS輸出:飲料 {'紅茶':40,'綠茶':30,'咖啡':70}
```
PS:再呼叫函式時，可用*,**將容器解包  


* ***lambda 匿名函式***  
函式如果很簡短，只需要``參數列``和``傳回值``，那麼就可以簡寫成一個lambda運算式，語法如下:  
```
lambda 參數1,參數2,...:傳回值
```
```
ex:  
lambda w,h:w * h  
相當於  
def calc(w,h):  
return w*h
```
#### ***內建函式庫與第三方套件***  
* ***Module模組的載入與使用***  
模組->將程式寫在一個檔案中，讓此檔案可重複載入使用  
```
載入模組方法:
import 模組名稱
OR
import 模組名稱 as 模組別名
OR 
from 模組名稱 import 函數(OR類別)名稱 (as 替代名稱)
OR
from 模組名稱 import 函數(or類別)名稱1, 函數(or類別)名稱2,...,函數(or類別)名稱n
OR 
from 模組名稱 import * #為導入模組內所有函數or類別
```
```
使用模組方法:
模組名稱或別名.函式名稱(參數資料)
OR
模組名稱或別名.變數名稱
OR
模組名稱或別名.類別名稱
```
```
import sys
sys.path.append("modules")  #在模組的搜尋路徑中『新增搜尋路徑』
print(sys.path) #印出模組搜尋路徑
```
* ***Package封包的設計與使用***  
包含模組的資料夾->用來整理及分類模組程式
```
-專案資料夾
--主程式.py
--封包資料夾
----__init__.py #此檔案有才會被視為封包
----模組一.py
----模組二.py
```
```
基本語法：
import 封包名稱.模組名稱
OR
import 封包名稱.模組名稱 as 模組別名
```
* ***應用模組***  
```隨機random模組```  
1. randint()->可隨機產生指定區間的整數 2. choice()->可在一個列表(list)中隨機傳回一個元素 3. shuffle()->可將list元素重新排列  #使用方式random.randint(min, max)...  
```時間time模組```  
1. time()->傳回自1970年1月1日 00:00:00AM以來的秒數 2. sleep()->可以讓工作暫停，參數單位為秒，常用於設計動畫 3. asctime()->以可以閱讀方式列出目前系統時間 4. localtime()->可返回目前時間的結構資料，所返回的結構可以用索引方式獲得個別內容  
```系統sys模組```  
1. version屬性->列出目前所使用python版本訊息 2. stdin此物件，可以搭配readline()方法，可以讀取螢幕輸入直到按下鍵盤enter的字串 3. stdout此物件，可以搭配write()方法，然後可以從螢幕輸出資料   
```keyword模組```  
1. kwlist屬性->可列出所有python關鍵字 2. iskeyword()->可利用此方法傳回參數的字串是否是關鍵字，如是傳回true，如否傳回false  

#### ***物件導向程式設計(object-oriented programming, OOP)以及物件 (object)與類別(class)***  

3. 物件就是由類別產生的，可以把類別想成就像是物件的設計藍圖。同一類別所產生的物件都具有相同的屬性和操作方法，但相同類別的不同物件其屬性值可能不一樣  
4. 類別規劃了物件的資料儲存的方式，這些儲存的資料就稱為物件的屬性 (attribute) 
5. 類別規劃了物件的操作方式，這些操作方式就稱為物件的方法 (method)  
ps:模組 (module)->就是儲存程式碼(可包含變數、函式、或類別)的檔案，將模組集合起來放在資料夾中，則可以組成套件 (package)，也可以把它想成儲存程式的檔案和資料夾  

```
用類別建立物件 : 物件名=類別名(可能會加參數) 
win=Tk() #等號左邊是物件名，可以理解為它被綁在一個Tk類別的物件上，通常習慣上會使用大寫作為類別名稱的開頭，所以看到等號右邊是大寫字母開頭，就要想到類別建立物件。而物件名、變數名、函式名一樣用小寫
-----------------
使用物件 : 物件.xxx
寫法總結  
1. 物件名.method(可能會加參數) 
2. 物件名.屬性
3. 物件名.屬性＝屬性值
4. 物件名=類別名(可能會加參數)
```
```
ex:假如pkg(資料夾)內中含有__init__.py(內含i_var以及i_fun()兩個函數)和mdp.py(內含var 以及 fun()兩個函數)兩個模組
1. import pkg->使用方式pkg.i_var或pkg.i_fun()
2. from pkg import mdp->使用方式mdp.var或mdp.fun()
3. from pkg.mdp import fun->使用方式fun()
```
```
可以用as來自訂匯入物件的名稱->可用來避免名稱衝突，也常用來縮短名稱
ex:
from mdu import var as v, fun ad f
```
#### ***實體物件的建立***  
* ***類別(class)與實體物件、實體屬性***  
透過類別建立->先定義類別，再透過類別建立實體物件，然後才能使用實體屬性(封裝在實體物件中的變數)  
基本語法:  
```
以類別建立實體物件
class 類別名稱(單字字首大寫):  
#定義初始化函式(建構式 constructor)
    def __init__(self): 
        透過操作self來定義實體屬性
#以類別建立實體物件，放入變數obj中
obj=類別名稱() #呼叫初始化函式
```
```
ex:
#類別建立
class Point:
    #建構式建立
    def __init__(self,x,y):
        self.x=x #屬性
        self.y=y #屬性
#建立實體物件
#建立時，可直接傳入參數資料
p=Point(1,5)
```
```
使用實體屬性
#建立實體物件，並取得實體屬性
p=Point(1,5)
print(p.x+p.y)
```
* ***類別(class)與實體方法***  
基本語法：
```
以類別建立實體物件
class 類別名稱:  
#定義初始化函式
    def __init__(self): 
        透過操作self來定義實體屬性
    def 方法名稱(self,更多自訂參數)： #第一個參數固定是self，代表實體物件本身
        方法主體，透過 self操作實體物件
#以類別建立實體物件，放入變數obj中
obj=類別名稱() #呼叫初始化函式
```
```
使用實體方法
#建立實體物件，並取得實體方法/函式
實體物件.實體方法名稱(參數資料)
```
```
ex:
class Point:
    def __init__(self,x,y):
        self.x=x
        self.y=y
    def show(self):
        print(self.x,self.y)
p=Point() #建立實體物件
p.show() #呼叫實體方法
```
-----------------------------
* ***其它用法***  
可利用``isinstance()``來判斷類別與物件的關係  
```
isinstance(object_name, class_name) -> 假如該物件屬於該類別則執行結果為True，否則為False
```
#### ***檔案的讀取與寫入***  
* ***資料夾與檔案路徑***  
(1) 絕對路徑與相對路徑  
絕對路徑->路徑從根目錄開始表示  
    ex:D:\Python\ch14\ch14_1.py  
相對路徑->是指相對於當前工作目錄的路徑  
    ex:若當前工作目錄為 D:\Python\ch14 ，他的相對路徑為ch14_1.py  
PS:在作業系統中，"."->指的是目前資料夾，".."->指的是上層資料夾，在使用上".\ch14_1.py"和"ch14_1.py"意義相同    

(2)os模組與os.path模組 
os.getcwd()->可取得當前工作目錄 

    

