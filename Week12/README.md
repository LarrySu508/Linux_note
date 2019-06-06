# 第十二周

![image](https://github.com/LarrySu508/Linux_note/blob/master/Week12/IMAG0801.jpg)

## 1.ssh公私密金鑰連線建置

![image](https://github.com/LarrySu508/Linux_note/blob/master/Week12/a.png)

## 2.ansible安裝說明

最主要在台灣只要下這兩行指令。

```
yum install epel-release
yum install ansible -y
```

若是大陸地區要先翻牆，請參考[ansible从入门到放弃](https://blog.51cto.com/11886307/2385720)。

## 3.ansible語法說明(參考:[ansible从入门到放弃](https://blog.51cto.com/11886307/2385720))

```
ansible <host-patten> [命令選項] [-a 參數]
```

### 1.host-patten設定

![image](https://github.com/LarrySu508/Linux_note/blob/master/Week12/b.png)

在此檔設定剛剛做好ssh公私密金鑰連線的主機IP

### 2.命令選項統整

|命令選項                |意思                  |
|-----------------------|-------------------------|
|--version              |ansible版本顯示|
|-m module              |指定模組(選取模式)| 
|-v                     |顯示詳細過程(-vv部分詳細過程／-vvv全部詳細執行過程)| 
|--list-hosts           |顯示設定的主機列表，可縮寫成--list| 
|-k                     |顯示輸入的ssh連線密碼，默認KEY驗證| 
|-C                     |檢查但不執行，通常用於yml腳本除錯| 
|-T，--timeout=TIMEOUT  |執行命令的超時時間| 
|-u,--user=REMOTE_USER  |指定遠程主機執行的用戶| 
|-b，--become           |作為舊版的sudo替代| 
|--become-user=USERNAME |指定sudo的runas用戶，默認為root| 
|-K,--ask-become-pass   |顯示輸入sudo時的指令|

### 3.模組說明

每個模組都會有不同的參數，所以可以下 ansible-doc [模組名稱] 來查看參數用法。

|模組                  |意思                  |實例|
|---------------------|-------------------------|----------------|
|ping         |用來測試HOST連通狀態|ansible app2 -m ping|
|command      |用於執行簡易命令，為預設的模組|ansible app2 -m command -a "ls /root"| 
|shell        |用於執行shell命令|ansible app2 -m shell -a "chdir=/data cat test.txt"| 
|script       |用於在遠端HOST上運行ansible伺服器上的腳本|ansible app2 -m script -a a.sh| 
|copy         |從ansible伺服器複製文件至遠端HOST|ansible app2 -m copy -a "src=/root/mya.txt dest=/tmp/myb.txt backup=yes mode=600 owner=user"| 
|fetch        |從遠端HOST提取文件，只能是文件，若要提取資料夾要先打包好|ansible app2 -m fetch -a "dest=/data src=/etc/fstab"| 
|file         |設置文件屬性|ansible app2 -m file -a "path=/root/aa owner=user mode=600"|
|hostname     |管理主機名稱|ansible app2 -m hostname -a 'name=mylinuxops.com'|  
|cron         |規劃任務模組|ansible app2 -m cron -a 'name=backupetc hour=1 job="/usr/bin/cp -a /etc /data/`date +%F`"'| 
|yum          |安裝包管理|ansible app2 -m yum -a "name=httpd"| 
|service      |管理遠端HOST服務|ansible app2 -m service -a "name=httpd state=started"| 
|user         |用戶管理模組|ansible app2 -m user -a "name=mysql system=yes shell=/sbin/nologin"| 

### 4.ansible腳本playbook

playbook為ansible中執行腳本，格式大致如下。

![image](https://github.com/LarrySu508/Linux_note/blob/master/Week12/c.png)

