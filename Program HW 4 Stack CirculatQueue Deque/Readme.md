# Template Bag Class and Inheritance  

## 目的&功能  
1. 使用陣列實現堆疊(Stack)、環形佇列(Circular Queue)、雙向佇列(Deque)。  

## 方法  
Bag為基本類別，堆疊與佇列均繼承於Bag類別。其中Bag資料不須在意順序，只須確保資料可取出和刪除即可。  
1. 使佇列(Queue)使用陣列中所有空間  
環形佇列中兩指標相等時需用來判斷其佇列已滿(或為空)，若需使用所有陣列空間則可有以下處理方式。
> 1. 將指標設為一般情況下不產生數值。  
> 若佇列已滿則將指標設為特定值(如NULL)用以判斷。如此題中 int rear, front 可再佇列已滿時將rear設為INT_MAX或-1，在修改佇列時先判斷rear以使用不同方式處理資料。  
> 此種方式能陣列中所有空間，但會多出較多程式個別處理不同情況下佇列的修改。另外可產生的陣列最大大小較小。  
> 2. 使用額外變數紀錄  
> 只須1 boolean變數 isFull 判斷其是否已滿，於加入數值(Push)後若 rear==front 則將isFull設為True；其餘其餘情況在處理完成後均將isFull設為False。則可用此變數判斷是否已滿，決定是否可加入新資料。  
> 此種方式須使用而外空間紀錄佇列狀態。實作中也使用類似此方式，由於佇列(Queue)繼承自Bag，而Bag中具整數變數int top與int MaxSize，故利用其記錄已使用大小與最大可儲存大小，可快速得知佇列是否已滿決定是否可存入新資料。  
2. 雙向佇列(Deque)  
基本與佇列(Queue)相同，而外製作Popr()、Pushf()，顧繼承佇列(Queue)做修改。其中主要只需將移動指標1與修改資料2執行順序順序對調即可。  

## 討論 
1. Pop功能 引述與回傳值不明確。  
   有時會使用Pop刪除資料，程式中使用call by reference則需先宣告一變數作為Pop引數才可使用。Pop改為刪除資料並回傳(return)刪除資料較符合一班使用情況。
2. 使用陣列完成不易調整資料數量。
   未來可配合List以便調整大小。

## 結果  
[]()