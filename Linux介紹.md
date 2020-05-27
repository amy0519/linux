---
tags: linux,伺服器
---

# linux伺服器( 3/11 ) 

## VmWare基本設定,Linux介紹 --筆記製作-呂芷瑛

* 新增網路卡
* 網路必備
    * IP、網路遮罩、預設閘道、DNS
    *    IP、MAC address不能重複(實體位置)
* 帳密:root centos
* 遠端(putty or git) ssh root@[IP]
* 查看ip address  
    * 指令--> ip addr-->取得[IP]
    *  Download putty-->alternative binary files-->64bit-->下載後輸入ip address及帳號密碼
    *  常用指令  ip addr、reboot、poweroff
*  linux檔案目錄(樹狀)
    *  ![](https://i.imgur.com/2Dj4eDS.png)


---
## 檔案操作指令

### pwd
*  pwd --目前所在位置
--
    ![](https://i.imgur.com/r1EmIDj.png)
    ![](https://i.imgur.com/Q0auyRK.png)

### cp
* 
    `cp /etc/passwd ./` -- [複製][目錄中的檔案]至[當前目錄]

### ls
* ls --查看檔案詳細資訊
![](https://i.imgur.com/z7BIRQP.png)

### cat、tac、less
* cat、tac、less -- 查看檔案內容
    1. cat -- 從頭到尾
        ![](https://i.imgur.com/F1oWDGS.png)
    2. tac -- 從尾到頭
        ![](https://i.imgur.com/fjIhZGm.png)
    3. less -- 分段(離開-->q)
        ![](https://i.imgur.com/Ri7Xs8G.png)

### touch、copy、mv、rm
* touch、copy、mv、rm -- 新增、修改、刪除
    1. touch -- 觸碰檔案(更改時間戳記)
        若檔案不存在，會產生一個空白的
        ![](https://i.imgur.com/qTSWePX.png)
    2. copy -- 複製
        * `cp passwd passwd2` -- 複製一模一樣的passwd為passwd2 (時間戳記改變)
        ![](https://i.imgur.com/qlLFx6r.png)

        * `cp [-a] passwd passwd3` -- 複製一模一樣的passwd為passwd2 (時間戳記不變)
        ![](https://i.imgur.com/Y7QSkB8.png)


    3. mv -- 移動
        `mv passwd3 passwd4`
        ![](https://i.imgur.com/COWyjcT.png)

    4. rm -- 刪除檔案
        `rm passwd4`
        ![](https://i.imgur.com/7KteWbg.png)

        > `rm -r` -- 可刪除目錄下的子子孫孫

### stat
* stat -- 檔案狀態
    ![](https://i.imgur.com/RNa5t4O.png)

---
## 目錄操作
### cl、ls
* cd、ls -- 目錄列表

* mkdir、mv、rmdir -- 建立、修改、刪除

### mkdir

* mkdir -- 新增目錄
    >  建立完d1目錄後去touch -> 可以成功

    `mkdir d1`
    `touch d1`
    ![](https://i.imgur.com/wxSvycU.png)

    >  若先建立名為d2檔案後，再建立名為d2目錄 -> 會失敗

    `touch d2`
    `mkdir d2`
    ![](https://i.imgur.com/vaGKUkg.png)

    >  linux分大小寫，所以建立名為D2的目錄 ->可以成功

    `mkdir D2`
     ![](https://i.imgur.com/2vyuRVi.png)


    >  -p可以補中間沒有的目錄 -> 可以成功

    `mkdir [-p] d2/sub/sub-2`
    ![](https://i.imgur.com/vTfNUND.png)

### mv
 * mv -- 修改目錄
    >   * `mv d2 d3`  將目錄d2移至目錄d3

    ![](https://i.imgur.com/SiPl3S9.png)
    >   * `mv d3 d5`  由於沒有名為d5的目錄，將目錄d3名稱修改為目錄d5

    ![](https://i.imgur.com/k3oGGwx.png)

### rmdir
* rmdir -- 刪除空目錄
    >    刪除`rmdir D2`

    ![](https://i.imgur.com/TaD99Tu.png)


    > `rmdir *`-- 一次刪除所有空目錄

    ![](https://i.imgur.com/xVM8ad6.png)
    ![](https://i.imgur.com/PHzqH23.png)


### pwd、man
* pwd -- 取得路徑資訊
* ./ 、 ../ 、 /fixed/path -- 遊走不同目錄
* man [指令] --查看指令可用手冊


---

## 系統資訊
### uptime、top、last
* uptime
    ![](https://i.imgur.com/ez6bzh8.png)

* top
    ![](https://i.imgur.com/sT6re3G.png)

* last
    ![](https://i.imgur.com/ajhrB9m.png)

        

      


        
        


---


# [3/18 筆記](https://hackmd.io/IabSEEHgTxePtZJPLwaguA/)

