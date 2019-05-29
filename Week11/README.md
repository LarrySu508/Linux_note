# 第十一周
## 1.IPtable規則說明

![image](https://github.com/LarrySu508/Linux_note/blob/master/Week11/IMAG0778.jpg)

![image](https://github.com/LarrySu508/Linux_note/blob/master/Week11/IMAG0779.jpg)

|命令                  |意思                  |實例|
|---------------------|-------------------------|----------------|
|-A                |追加規則|iptables -A INPUT|
|-D                |刪除規則|iptables -D INPUT 1| 
|-R                |修改規則|iptables -R INPUT 1 -s 192.168.12.0 -j DROP | 
|-I                |插入規則|iptables -I INPUT 1 --dport 80 -j ACCEPT | 
|-L                |查看規則|iptables -L INPUT | 
|-N                |新的規則|iptables -N allowed| 

|參數                  |意思                  |實例|
|---------------------|-------------------------|----------------|
|-p                |協議|iptables -A INPUT -p tcp|
|-s                |來源位置|iptables -A INPUT -s 192.168.1.1| 
|-d                |目的位置|iptables -A INPUT -d 192.168.12.1| 
|-sport            |來源端口|iptables -A INPUT -p tcp --sport 22| 
|-dport            |目的端口|iptables -A INPUT -p tcp --dport 22| 
|-i                |指定入口網卡|iptables -A INPUT -i eth0|
|-o                |指定出口網卡|iptables -A FORWARD -o eth0|  

|-j指定的動作                  |意思                  |
|---------------------|-------------------------|
|DROP              |丟棄|
|REJECT            |拒絕|
|ACCEPT            |允許|
|SNAT              |基於原地址的轉換|
|DNAT              |目標地址的轉換|

### 1.表 (table)[iptables命令、规则、参数详解](https://www.cnblogs.com/zclzhao/p/5081590.html)
4个表的優先級數由高到低：raw>mangle>nat>filter

#### 1.RAW
只使用在PREROUTING鏈和OUTPUT鏈上,因為優先級最高，從而可對收到的數據封包在連接跟踪前進行處理。一但用戶使用了RAW表,在某個鏈上,RAW表處理完後,將跳過NAT表和ip_conntrack處理,不再做地址轉換和數據包的鏈接跟踪處理了。

#### 2.filter
預設規則表，擁有 INPUT、FORWARD 和 OUTPUT 三個規則鏈，這個規則是用來進行封包過濾的理動作。

#### 3.net
擁有prerouting和postrouting兩個規則鏈， 主要功能為進行一對一、一對多、多對多等網址轉譯工作（SNATDNAT）。

#### 4.mangle
擁有prerouting、FORWARD、postrouting三個規則鏈，除了進行網址轉譯工作會改寫封包外，在某些特殊應用可能也必須去改寫封包(ITL、TOS)或者是設定MARK(將封包作記號，以進行後續的過濾)這時就必須將這些工作定義在mangles規則表中。

