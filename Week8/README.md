# 第八周
## 1.nagios監控應用。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/IMAG0710.jpg)
### 1.大致上會做出如第一張圖中上的架構，首先安裝nagios相關套件與設定，指令如下：
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