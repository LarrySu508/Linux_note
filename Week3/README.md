# 第三周
## 1.通配符 二(正規表示法)
|符號                  |  意思                   |
|---------------------|-------------------------|
|[:alnum:]             |代表英文大小寫字元及數字，像是0-9, A-Z, a-z。 |
|[:alpha:]             |代表任何英文大小寫字元，像是A-Z, a-z。       |
|[:digit:]             |代表數字而已，像是 0-9。               |
>參考於:[命令执行绕过之Linux通配符](http://byd.dropsec.xyz/2018/05/29/%E5%91%BD%E4%BB%A4%E6%89%A7%E8%A1%8C%E7%BB%95%E8%BF%87%E4%B9%8BLinux%E9%80%9A%E9%85%8D%E7%AC%A6/)、[鳥哥的 Linux 私房菜](http://linux.vbird.org/linux_basic/0330regularex.php)
## 2.管理網域(建置正向解析&反向解析)
### 1.正向解析
#### 1.先設定/etc/named.rfc1912.zones，在/etc/named.rfc1912.zones網域設定檔中新增一個zone區塊，如下圖：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week3/%E6%AD%A3%E5%90%91%E8%A8%AD%E5%AE%9A1.png)
新增一個"newtest.com"網域設定值，而網域資源記錄檔是"named.newtest"，這兩個的"newtest"可以自由命名，只是要和後面步驟要有一致性。
#### 2.在/var/named資料夾中新增一個網域資源記錄檔"named.newtest"，內容如下圖：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week3/%E6%AD%A3%E5%90%912.png)
圖中紅框部分改成你個人設定的IP，格式其實可參照同資料夾下的"named.localhost"檔案。
#### 3.在重啟named service後，最後在cmd下可以用正向解析找到自己設定的格式，如下圖：
##### 1.
```
systemctl restart named
```
##### 2.
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week3/%E7%B5%90%E6%9E%9C1.png)
>如果有權限問題請在restart named前下下方指令，更改資源紀錄檔的權限。
```
chown root:named /var/named/named.newtest
```
### 2.反向解析
#### 1.先設定/etc/named.rfc1912.zones，在/etc/named.rfc1912.zones網域設定檔中新增一個zone區塊，如下圖：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week3/%E5%8F%8D%E5%90%91%E8%A8%AD%E5%AE%9A1.png)
有點類似正向，但因為反向是用IP解析Domain Name，所以要先放反向的IP。
#### 2.在/var/named資料夾中新增一個網域資源記錄檔"named.newtest.ip"，內容如下圖：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week3/%E5%8F%8D%E5%90%91.png)
格式其實可參照同資料夾下的"named.loopback"檔案，但還是有點不一樣所以我參考[CentOS7下部署DNS服务器](https://www.linuxidc.com/Linux/2017-07/145879.htm)。
#### 3.在重啟named service後，最後在cmd下可以用反向解析找到自己設定的格式，如下圖：
##### 1.
```
systemctl restart named
```
##### 2.
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week3/%E7%B5%90%E6%9E%9C2.png)
>如果有權限問題請在restart named前下下方指令，更改資源紀錄檔的權限。
```
chown root:named /var/named/named.newtest.ip
```
