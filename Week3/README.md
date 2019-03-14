# 第三周
## 1.通配符 二(正規表示法)
|符號                  |  意思                   |
|---------------------|-------------------------|
|[:alnum:]             |代表英文大小寫字元及數字，像是0-9, A-Z, a-z。 |
|[:alpha:]             |代表任何英文大小寫字元，像是A-Z, a-z。       |
|[:digit:]             |代表數字而已，像是 0-9。               |
>參考於:[命令执行绕过之Linux通配符](http://byd.dropsec.xyz/2018/05/29/%E5%91%BD%E4%BB%A4%E6%89%A7%E8%A1%8C%E7%BB%95%E8%BF%87%E4%B9%8BLinux%E9%80%9A%E9%85%8D%E7%AC%A6/)、[鳥哥的 Linux 私房菜](http://linux.vbird.org/linux_basic/0330regularex.php)
## 2.管理網域(建置正向查詢&反向查詢)
### 1.正向查詢
#### 1.先設定/etc/named.rfc1912.zones，在/etc/named.rfc1912.zones網域設定檔中新增一個zone區塊，如下圖：
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week3/%E6%AD%A3%E5%90%91%E8%A8%AD%E5%AE%9A1.png)
新增一個"newtest.com"網域設定值，而網域資源記錄檔是"named.newtest"。
#### 2.在/var/named資料夾中新增一個網域資源記錄檔"named.newtest"。
