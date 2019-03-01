# 第一周
## CentOS 7 SSH 連線驗證(Google Authenticator)  參照:[CentOS 7 SSH 兩步驟驗證](https://kenwu0310.wordpress.com/2016/12/09/centos-7-ssh-%E9%9B%99%E5%9B%A0%E7%B4%A0%E8%AA%8D%E8%AD%89-using-google-authenticator/)
1.因為要用到git的套件，所以要先看看你虛擬機上的git版本是否最新，如果不是請在root模式下
```
[root@user]# yum update nss curl\
```
參考於:[git clone 报错 incompatible or unsupported protocol version處理方法](https://pages.github.com/)
