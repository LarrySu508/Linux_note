# 第二周
## 1.通配符
|符號                  |  意思                  |實例|
|---------------------|-------------------------|----------------|
|*                    |匹配0、單個或多個任意字符。|下a*b會出現類似的檔案，如a1b,a5456b,ajb,afdkvb,a%b,a?#b。|*
|?                    |只會匹配單個任意字符。     |下a?b會出現單個字符類似的檔案，如a1b,ajb,a%b。| 
|[menu]               |配對menu中的任意單個字符。 |下a[1f%]b會出現單個字符類似的檔案，如a1b,afb,a%b。|
|[!menu]or[^menu]     |配對除了menu中的任意單個字符。|下a[!1f%]b不會出現單個字符類似的檔案，如a2b,aib,a^b。|
|[b1-b2]              |配對b1-b2中的任意單個字符。|下a[0-2]b會出現單個字符類似的檔案，如a0b,a1b,a2b。|
|[!b1-b2]or[^b1-b2]   |配對不在b1-b2中的任意單個字符。|下a[!0-2]b不會出現單個字符類似的檔案，如a3b,aib,a^b。|
|{string1,string2,…}  |配對string1,string2或string…中的符合的字符串。|下a{123,2gsd32%@ks4@,%?,fij}b會出現符合字符串類似的檔案，如a123b,a2gsd32%@ks4@b,a%?b,afijb。|
## 2.DNS
### 1.DNS Server:直接去詢問Domain Name的IP，再回傳給詢問者，也快取作用。
### 2.DNS Cache:顧名思義是把查到的Domain Name—IP存起來，如果有人問到一樣的Domain Name直接傳給詢問者，可減低DNS Server負擔。
### 3.DNS Forworder:代理從別人的DNS Server或DNS Cache抓取過來給詢問者，可減低DNS Server負擔。
>其他類型可參考:[DNS架構](http://dns-learning.twnic.net.tw/dns/02ArchDNS.html)。
## 3.DNS Server
### 1.做為名稱解拆，早期有做負載均衡作用。
### 2.有分正向Domain Name —> IP，和反向IP —> Domain Name。
### 3.谷歌 Google Public DNS Server 8.8.8.8 (主) 8.8.4.4 (副)，IBM 免費 DNS Server 9.9.9.9，Cloudflare與亞太網路資訊中心（Asia-Pacific Network Information Centre，APNIC）合作的公共DNS Server 1.1.1.1。
### 4.DNS也可用來做DDoS，概念如下圖:
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week2/DDoS.png)
#### 最後User會被大量流量攻擊到無法連網。
## 4.完全網域域名(Fully qualified domain name,FQDN):
#### 維基百科概念圖:
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week2/350px-DNS-names-ru.svg.png)
#### 現在Browser都知道怎麼找Domain Name，網址最後的"."可以不用打，所以在Browser上打`https://www.google.com.tw.`或`https://www.google.com.tw`，結果都一樣不信可以試試。
## 5.架設DNS Server(請在root模式下執行)
### 1.安裝BIND(Berkeley Internet Name Domain)。
```
yum -y install bind bind-chroot bind-utils
```
### 2.設定或關閉防火牆，SELinux關閉。
#### 設定防火牆。
```
firewall-cmd --permanent --add-service=dns
firewall-cmd --reload
```
#### 關閉防火牆。
```
systemctl stop firewalld.service
systemctl disable firewalld.service
```
#### SELinux關閉。
修改/etc/selinux/config檔，改成disable。
```
gedit /etc/selinux/config
SELINUX=disable
```
### 3.啟動named服務，測試DNS Server。
```
systemctl start named
systemctl enable named
```
#### 測試DNS Server。
```
dig @127.0.0.1 www.pchome.com.tw
```
#### 結果會有一行;; ANSWER SECTION，下一行是你查詢的Domain Name的ip。
### 4.開放給外部連線查詢。
#### 編輯bind的主設定檔。
```
gedit /etc/named.conf
```
#### 把"listen-on port 53"與"allow-query"的127.0.0.1與localhost都改成"any"。
```
// named.conf
//
(略)
option  {
        listen-on port 53 { any; };
        (略)
        allow-query   { any; };
        (略)
};
(略)
```
#### 改完存檔後，重啟named服務。
```
systemctl start named
```
### 5.最後在自己的主機，而非虛擬機上(虛擬機別關啊，他是你要用的Server)，下查詢Domain Name指令。
#### 打開主機的Terminal輸入:([NDS Server IP]請輸入你虛擬機的IP，因為那是你開的NDS Server，還有網頁你可隨便挑一個找不一定要照範例輸入。)
```
nslookup www.nqu.edu.tw [NDS Server IP]
```
#### 下指令前先ping虛擬機的IP看可否連線。
#### 結果會有虛擬機IP和查詢Domain Name的IP，如下圖:
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week2/DN.jpg)
#### 有一個地方觀念很重要，有看到"未經授權的回答:"這幾個字的話，代表DNS Server內部就有快取到，不用再去找，如果沒快取，就沒"未經授權的回答:"這幾個字。
