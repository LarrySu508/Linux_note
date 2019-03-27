# 第四周
## 1.Linux三劍客(另加正則表達式&通配符)參考於：[聊聊 Linux"三剑客"](https://zhuanlan.zhihu.com/p/51392253)
### 1.grep
#### 1.主要用於文本內容查詢，支持正則表達式，全面搜索正規表達式並打印出來。
#### 2.簡單例子如下：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/grep.png)
### 2.awk
#### 1.主要用於文本內容分析處理，也用於處理數據生成報告，適用於需要按列處理的數據，空格為預設分割。
#### 2.簡單例子如下：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/awk3.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/awk1.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/awk2.png)
### 3.sed(Stream editor)
#### 1.主要用於文本內容編輯，默認下只處理模式空間，不改變原本數據，使用逐行讀取方式處理數據，可以將數據進行替換、刪除、新增、選取等工作。
#### 2.簡單例子如下：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/sed.png)
### 4.正則表達式&通配符
#### 1.抓取具體字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/1.png)
#### 2.抓取單個字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2.png)
#### 3.抓取反向字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/3.png)
#### 4.抓取任意字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/4.png)
#### 5.抓取小數點字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/4-1.png)
#### 6.抓取頭字符、尾字符、頭尾字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/6.png)
#### 7.抓取任何字類字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/7.png)
#### 8.抓取非任何字類字符例子：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/8.png)
#### 9.抓取需單字分隔的字符例子：
##### 1.
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/9.png)
##### 2.
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/10.png)
## 2.Docker 
### 1.設定Docker名稱。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-1.png)
### 2.用Docker名稱或ID開啟。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-2.png)
### 3.關閉開啟的Docker。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-3.png)
### 4.於Docker中顯示IP。
#### 若有兩台Docker，請先在兩台上下載net-tools。
```
yum -y net-tools
```
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-4.png)
### 5.Docker刪除容器指令。
```
docker rm -f id(name)     //-f為強制執行
docker rm -f $(docker ps -a -q)   //刪除ps中能看到的所有容器
docker rmi id(name)
```
### 6.Docker image上傳
#### 1.先到Docker官網申請帳號。
> [Docker.com](https://www.docker.com/)
#### 2.容器匯出image。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-5.png)
#### 3.更改標籤名稱(上傳才不會撞名稱)。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-6.png)
#### 4.登入Docker，並push上去。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-7.png)
#### 5.最後可在網站上看到你傳的image。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week4/2-8.png)
