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
>最後User會被大量流量攻擊到無法連網。
