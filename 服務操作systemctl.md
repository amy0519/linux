---
tags: linux,伺服器
---

# linux伺服器( 4/29 )- 服務操作systemctl(設定下次開機時會on起來)

## 下載cockpit(圖形化管理工具)
### 1.下載cockpit
* `dnf install -y cockpit*`
    ![](https://i.imgur.com/prAJrjP.png)

### 2.查看cockpit.socket狀態
* `systemctl status cockpit.socket`
    ![](https://i.imgur.com/CpHmItK.png)


    
### 3.檢查防火牆
* `firewall-cmd --list-all`  - 有在list中皆可連上
    ![](https://i.imgur.com/by5Vx5F.png)

### 4.將服務開啟
#### enable並啟動socket
* `systemctl enable cockpit.socket`  
* `systemctl start cockpit.socket`
    ![](https://i.imgur.com/ubR0Lqp.png)

#### 再次查看socket status
* `systemctl status cockpit.socket` - 此時已啟動
    ![](https://i.imgur.com/fB4s2TB.png)
    
### 5.確認IP後至瀏覽器進入介面化linux
* `ip addr` 
    ![](https://i.imgur.com/P5vKng8.png)
    
* 到瀏覽器
    ![](https://i.imgur.com/TfVFCOQ.png)
    
    ![](https://i.imgur.com/FX0ji7Q.png)
    
    ![](https://i.imgur.com/NEoWHY6.png)


---


## 下載MariaDB
### 1.先查看先前是否已裝
* `dnf list mariadb-server` - 如果有@符號代表有裝，反之
    ![](https://i.imgur.com/2k26s3E.png)

### 2.安裝MariaDB
* `dnf install mariadb-server` - 之後按y
    ![](https://i.imgur.com/zrePIsk.png)

### 3.查看MariaDB狀態
* `systemctl status mariadb`
    ![](https://i.imgur.com/6gW5sVz.png)

### 4.enable MariaDB
* `systemctl enable --now mariadb`  
    ![](https://i.imgur.com/T7K4SVd.png)


### 5.再次查看MariaDB
* `systemctl status mariadb` - 此時已啟動
    ![](https://i.imgur.com/4aMKCgu.png)

### 6.驗證是否能連上MariaDB
* `mysql -u root -h localhost` 
    ![](https://i.imgur.com/jIfp77N.png)

#### 停止MariaDB
* `systemctl stop mariadb` 
#### 啟動MariaDB
* `systemctl start mariadb`

### 7.設定MariaDB的密碼(第一次才需要，一開始是空的)
* `mysql_secure_installation` 
    ![](https://i.imgur.com/GReOdqp.png)

#### 密碼設定後連上MariaDB要打密碼，否則進不去，如下
* `mysql -u root -h localhost` 
    ![](https://i.imgur.com/RYfXlHe.png)

### 8.連上MariaDB
* `mysql -u root -h localhost -p` 
    ![](https://i.imgur.com/KYTSXck.png)


---

## 下載httpd(Apache服務)
### 1.先查看先前是否已裝httpd
* `dnf list httpd` - 如果有@符號代表有裝，反之
    ![](https://i.imgur.com/lwUtyxK.png)
    
### 2.安裝httpd
* `dnf install httpd` - 之後按y
    ![](https://i.imgur.com/6dyF9bR.png)

### 3.查看httpd狀態
* `systemctl status httpd`
    ![](https://i.imgur.com/ZYTf813.png)


### 4.enable httpd
* `systemctl enable --now httpd`  
    ![](https://i.imgur.com/MAmUbh4.png)



### 5.再次查看httpd
* `systemctl status httpd` - 此時已啟動
    ![](https://i.imgur.com/TgU6Jvr.png)

### 6.查看firewall是否有開放給httpd連
* `!firewall` - 此時沒開放給httpd
    ![](https://i.imgur.com/6R1ckw0.png)

### 7.將firewall開放給httpd連
* ` firewall-cmd --add-service=http --permanent` 
* `firewall-cmd --reload`
    ![](https://i.imgur.com/iZHq5BO.png)

#### 再次查看firewall是否有開放給httpd連
* `!firewall` 或`firewall-cmd --list-all` - 此時已開放給httpd
    ![](https://i.imgur.com/6u5qv8m.png)

### 7.至瀏覽器確認已安裝成功
![](https://i.imgur.com/1gQidlC.png)


### 8.將測試頁隱藏
#### 進到html目錄
* ` cd /var/www/html/`
    ![](https://i.imgur.com/a9qPMuF.png)
* ` cat /etc/httpd/conf.d/welcome.conf`
    ![](https://i.imgur.com/R8pZcuX.png)
* ` touch index.html`
    ![](https://i.imgur.com/MWosmR0.png)
*     此時測試頁已被取代成index.html
    ![](https://i.imgur.com/CBvJgbV.png)




---
## 建立php
### 1.進到html目錄
* ` cd /var/www/html/`
    ![](https://i.imgur.com/a9qPMuF.png)
    
### 2.進到vi改php檔案
* ` vi phpinfo.php`
    ![](https://i.imgur.com/eAKKSLC.png)
    
* ` <?php phpinfo(); ?>`
    ![](https://i.imgur.com/dNIYpGe.png)
    
    >  此時瀏覽器上會噴出原始碼

![](https://i.imgur.com/6Gmh5Hu.png)

### 3.安裝php服務套件
* `dnf install php-fpm php` - 之後按y
    ![](https://i.imgur.com/i1UJhdr.png)

### 4.enable php
* `systemctl enable --now php-fpm`  
    ![](https://i.imgur.com/zk392tU.png)
    
### 5.restart httpd
* `systemctl restart httpd`  
    ![](https://i.imgur.com/AjnKh7Q.png)
    
    >  此時瀏覽器上原始碼已隱藏
    
    ![](https://i.imgur.com/7bYZbO8.png)
    
## 小結: 要run php至少要2個服務 (1)http (2)php

### ***改port
```
 firewall-cmd --permanent --add-port=888/tcp
```

# [5/06 筆記](https://hackmd.io/NcmJiiVJRBytf3h0s_sICA) 



