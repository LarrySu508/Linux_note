# 第八周
## 1.nagios監控應用。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/IMAG0710.jpg)
### 1.大致上會做出如第一張圖，中間上面的架構，首先安裝nagios相關套件與設定，還有兩台機子都是配NAT+HostOnly兩張網卡，指令如下：
```
yum install epel-release
yum install httpd nagios* nrpe
systemctl start httpd
systemctl start nagios
htpasswd -c /etc/nagios/passwd nagiosadmin //這裡是設定登入帳密，nagiosadmin是帳號，接著輸入密碼，登入畫面如下圖所示。
systemctl restart httpd
systemctl restart nagios
```
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/d.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/c.png)
### 2.接著是把client設定成可以被server監控，且http或ssh等套件運作狀態顯示設定，另外還可分群設定。
#### 1.修改/etc/nagios/objects/localhost.cfg檔
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/e.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/g.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/f.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/h.png)
#### 2.修完後，systemctl restart nagios，就可以在nagios看到狀態，如果未顯示可能要等自動跟新狀態。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/i.png)
.![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/j.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/k.png)