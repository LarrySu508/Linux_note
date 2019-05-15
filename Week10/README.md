# 第十周
## 1. rsync + inotify自動備份。[CentOS 7使用rsync實現數據備份](https://www.itread01.com/content/1511251328.html)、[Centos7 下 配置 rsync 以及 rsync+inotify 實時同步](https://www.itread01.com/content/1532780568.html)
## 2. 先在兩台機子安裝rsync。
```
yum install rsync -y
```
## 3. 在需要備份的機子上修改/etc/rsyncd.conf檔。
![image](https://github.com/LarrySu508/Linux_note/blob/master/Week10/a.png)
## 4. 然後在兩台機子建要連動的資料夾，兩個資料夾都要改權限(本人兩個資料夾都用相同的名字)。
```
mkdir /data/nextcloud
chmod 600 /data/nextcloud
```
## 5. 在需要備份的機子上建帳號密碼認證文件，建完更改權限。
```
gedit /etc/rsyncd.pass
backup:123456 //新建的使用者帳密

chmod 600 /etc/rsyncd.pass
```
## 6. 啟動服務。
```
systemctl start rsyncd.service
```
## 7. 在存放備份的機子上，建認證密碼文件，建完更改權限，啟動服務。
```
gedit /etc/rsyncd.pass
123456 //使用者帳密

chmod 600 /etc/rsyncd.pass
systemctl start rsyncd.service
```
## 8. 在存放備份的機子上，下以下指令，即可手動備份。
```
rsync -vzrtopg --delete --progress --password-file=/etc/rsyncd.pass backup@10.x.x.x::nextcloud /data/nextcloud //10.x.x.x此處請改成需要備份機子的IP
```
