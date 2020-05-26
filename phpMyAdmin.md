---
tags: linux,伺服器
---

# linux伺服器( 5/06 ) 

## phpMyAdmin
### 1.下載phpMyAdmin -依版本不同更改連結(https://www.phpmyadmin.net/downloads/)
* ` curl -OJL https://files.phpmyadmin.net/phpMyAdmin/4.9.5/phpMyAdmin-4.9.5-all-languages.tar.gz`
    ![](https://i.imgur.com/fG9aga3.png)


### 2.移動壓縮檔到html目錄中
* `mv phpMyAdmin-4.9.5-all-languages.tar.gz /var/www/html`
    ![](https://i.imgur.com/L6dYqpT.png)

### 3.切到目錄中並解壓縮，再將檔案放到sql目錄中
* `cd /var/www/html`
* `tar zxf phpMyAdmin-4.9.5-all-languages.tar.gz`
* ` mv phpMyAdmin-4.9.5-all-languages sql`
    ![](https://i.imgur.com/sYKfeQd.png)
    ![](https://i.imgur.com/f0Mf9Zo.png)

### 4.加載套件
* `dnf install php-mysqli php-pdo php-mbstring php-gd php-json`
* `systemctl restart php-fpm`
    ![](https://i.imgur.com/DIeN9al.png)
    ![](https://i.imgur.com/aJiG1W5.png)
    ![](https://i.imgur.com/71Ep3fs.png)

### *補充 忘記phpMyAdmin密碼如何重設
* ` cd /var/lib/mysql/`
* `ls -l`
* `rm -rf *`
* `ls -l`
* `systemctl start mariadb`

### 5.登入phpMyAdmin，查看目前databases
* `mysql -u root -p -h localhost`
* `show databases;`
    ![](https://i.imgur.com/47JXSAZ.png)
    ![](https://i.imgur.com/jZ0NgYb.png)
    ![](https://i.imgur.com/s945UEj.png)

#### 增加資料庫
```
create database linuxdb;
show databases;
```
![](https://i.imgur.com/S26pt95.png)
![](https://i.imgur.com/iNEgQlK.png)

#### 刪除資料庫
```
drop databases linuxdb;
```
![](https://i.imgur.com/f9HYPXv.png)

#### 還原資料庫
> 查看資料庫文件原檔
    ```
    mysqldump -u root -p -h localhost linuxdb
    ```
    
![](https://i.imgur.com/TmVNmWt.png)

> 將資料庫linuxdb標準輸出至linux.sql
    ```
    mysqldump -u root -p -h localhost linuxdb > linux
    ```
    
![](https://i.imgur.com/s46neMU.png)

![](https://i.imgur.com/O0XUaYa.png)

> 將linux.sql倒入db3資料庫中(還原linuxdb至db3中)
    ```
    mysqldump -u root -p -h localhost linuxdb > linux.sql
    ```
    
![](https://i.imgur.com/DHoaSXp.png)

![](https://i.imgur.com/4PB3ni1.png)



# [5/13 筆記](https://hackmd.io/26ABCGcrQlikFP3Z3M9_7A) 
