# 第五周
## 1.正則表達式補充
### 1.若要抓字串直接用單引號框起來即可，"."的話是任意字符配對，如：grep '1000' passwd,grep 'root' passwd,grep 'r..t' passwd。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/a.png)
### 2.要匹配兩個字母或數字的話要再加中括號，如：grep '[0-9][0-9]' passwd,grep '[A-Z][a-z]' passwd。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/b.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/c.png)
### 3.Linux正則表達式是貪婪的，匹配不只一次，只要有配到的就會反紅，還有如果只要列出匹配的要加'-o'。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/d.png)
### 4.如果你只要你所限定的字數甂，就在頭尾加'\b'。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/e.png)
### 5.重複符號(除了\*字符號外，其他記得在符號前加上'\\'，在'('、')'和'|'前也要加)
|符號             |意思             |
|-----------------|-----------------|
|  *              |零次或多次配對。  |
|  +              |一次或多次配對。  |
|  ?              |零次或一次配對。  |  

![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/f.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/g.png)
### 6.若不想再+、?前加'\\'，有以下方式達到結果。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/h.png)
### 7.重複次數設定，在字串或[]後加上'{,}'，並在裡面設定重複幾到幾次，如：grep '[0-9]\b{2,3}\b' passwd。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/i.png)
### 8.任意字符串'.\*'，下有圖例。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/j.png)
### 9.邏輯組合簡單例子
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/k.png)
### 10.其他範例
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/l.png)
## 2.Docker 開啟 httpd
### 1.先把容器清空，接著載httpd:latest，再把httpd:latest映像開啟成容器。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/m.png)
### 2.可直接開啟瀏覽器本地端查看，也可去根目錄mydata裡的aa.htm，再用瀏覽器去觀看。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/n.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week5/o.png)
### 3.有個指令很重要，你如果要看你開啟的Docker容器IP，請下下面指令：
```
docker inspect 你Docker的ID或是你給容器的名稱
```
