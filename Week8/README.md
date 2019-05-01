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
### 2.接著是把client設定成可以被server監控，且http或ssh等套件運作狀態顯示設定，另外還可分群設定。(本人serverIP設192.168.42.200，clientIP設192.168.42.10)
#### 1.修改/etc/nagios/objects/localhost.cfg檔
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/e.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/g.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/f.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/h.png)
#### 2.修完後，systemctl restart nagios，就可以在nagios看到狀態，如果未顯示可能要等自動跟新狀態。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/i.png)
.![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/j.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/k.png)
### 3.接下來是增加一些其他的監控狀態，要用到nrep，還可設定只允許server機查詢狀態。
#### 1.在client端下載nrpe套件。
```
yum install epel-release nrpe nagios-plugin*
```
#### 2.修改/etc/nagios/nrpe.cfg檔，改完後systemctl restart nrpe，重啟nrpe。(/etc/nagios/nrpe.cfg裡，最後有一些查詢指令的格式，可依格式設定要增加的監控項目)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/l.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/m.png)
#### 3.最後回server機，修改/etc/nagios/objects/localhost.cfg和/etc/nagios/objects/command.cfg，改完後，systemctl restart nagios，重啟nagios。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/n.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/o.png)
#### 4.結果如下圖所示。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/u.png)