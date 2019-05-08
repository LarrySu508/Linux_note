# 第九周
## 1. 大致上會做出被監控端CPU、NetWork、Waiting connect和新建windows被監控端的狀態。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/a.png)
## 2. 被監控端CPU、NetWork的狀態指令被放在/etc/nrpe.d/lcgdm-common.cfg設定檔中(此檔為預設監控指令以外的新監控指令)，在此檔的資料夾下下指令，會出現CPU、NetWork狀態(因為nrpe會用到port 5666，所以最好檢查一下是否開啟)。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/b.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/c.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/d.png)
## 3. 而監控端會把被監控端的狀態指令放在/usr/lib64/nagios/plugins下，所以在此檔的資料夾下下指令，會出現被監控端CPU、NetWork狀態。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/f.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/e.png)
## 4. 再來修改監控端的/etc/nagios/objects/command.cfg設定檔，這樣監控端在下設定檔的指令時，才能用nrpe抓來的狀態。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/o.png)
## 5. 再來修改監控端的/etc/nagios/objects/localhost.cfg設定檔，加入兩個監控狀態，改完後，systemctl restart nagios，重啟nagios，最後會在網頁顯示這兩個狀態。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/g.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/h.png)
## 6. 因為check_waiting_connect等待連線數，為完全新的監控指令，所以要在被監控端的/usr/lib64/nagios/plugins，直接寫出檔名為check_waiting_connect的腳本，再來記得改check_waiting_connect的權限，改完後就可以在現在的資料夾下指令測試看看。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/IMAG0733.jpg)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/i.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/j.png)
## 7. 因為被監控端的/etc/nagios/nrpe.cfg設定檔(此檔其實為監測指令的預設檔)裡沒有check_waiting_connect的指令，新增狀態指令被放在/etc/nrpe.d/lcgdm-common.cfg設定檔中(此檔為預設監控指令以外的新監控指令)，新增完後可以在/etc/nrpe.d/資料夾下指令是試試，最後，systemctl restart nagios，重啟nagios，結果會在網頁上多出check waiting connections的監控數據。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week8/m.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/k.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/l.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/m.png)
## 8. 再來是監控架設虛擬機的windows系統，先把/etc/nagios/nagios.cfg設定檔裡windows系統的設定註解去掉，意思就是開啟windows系統的監控，接著是設定與windows系統建置連線，systemctl restart nagios，重啟nagios。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/n.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/o.png)
## 9. 接著在windows上下載NSClient++，最後開啟nagios網頁就會有winserver的狀態。[Nagios利用NSClient++監控Windows主機](https://www.itread01.com/content/1505803218.html)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/p.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/q.png)
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week9/r.png)
