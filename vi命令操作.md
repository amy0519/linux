---
tags: linux,伺服器
---

# linux伺服器( 3/18 )
* 下載git
    * 可以不用putty就可遠端
    * 下載 -- https://inc-s3.ntub.edu.tw/shyong/VMware/Tools/Git-2.25.1-64-bit.exe
    * gitBash遠端指令: ssh root@192.168.92.128(更換ip)


---

## 編輯檔案-使用vi
* vi –[檔名]

### 命令操作
* 命令操作
     * YY -- 複製
     * x -- 剪下
     * p -- 目前所在行數下一行貼上
     * U -- 還原
     * :w -- 存檔
  * :q -- 關檔
### 游標操作
* 游標控制
     * hJKL -- 左右上下
     * ^(shift+6) -- 將游標快速跳到句首
     * $(shift+4) -- 將游標快速跳到句尾
     * o -- 插入新的一行(下一行)
     * O -- 插入新的一行(上一行)
### 切換 命令/編輯
* Esc/i(insert) -- 切換 命令/編輯
### 查詢
* /[要查詢的] -- 查詢關鍵字
    ![](https://i.imgur.com/tEcWiN4.png)
    ![](https://i.imgur.com/ZkVVQPd.png)
    * N -- (查詢中)下一筆

---

## 新增帳號
> ntub1001: x:1001:1000:ntub1001:/home/ntub1001:/bin/bash
> 帳號 : 密碼 : UID : GID : 別名 : /家目錄 : share
* 新增帳號
    * ` tail -n 3 /etc/passwd > user-lab.txt` -- 顯示前3筆並導入 user-lab.txt 中
        ![](https://i.imgur.com/XZFJryu.png)

    * `vi user-lab.txt` -- 進到vi user-lab.txt
        ![](https://i.imgur.com/SCHuYkk.png)
    * `ntub1001:x:2001:2001:ntub1001:/home/ntub1001:/bin/bash
ntub1002:x:2002:2002:ntub1002:/home/ntub1002:/bin/bash
ntub1003:x:2003:2003:ntub1003:/home/ntub1003:/bin/bash
ntub1004:x:2004:2004:ntub1004:/home/ntub1004:/bin/bash
ntub1005:x:2005:2005:ntub1005:/home/ntub1005:/bin/bash
` 
-- 增加帳號
            ![](https://i.imgur.com/UKqUgvH.png)

    *  `id ntub1001` -- 這時還沒有帳號
        ![](https://i.imgur.com/7dFaDRu.png)

    *  `id centos` -- 此時已有centos帳號
        ![](https://i.imgur.com/byuUNug.png)

    *  `newusers user-lab.txt` -- 增加使用者  
        ![](https://i.imgur.com/I6QkB3f.png)

    *  `id ntub1001` -- 這時已有帳號
        ![](https://i.imgur.com/JLaNa4g.png)
        
* 登入新增的帳號
    * 使用git遠端登入 -- ssh [帳號名稱]@[ip]
    ![](https://i.imgur.com/F8xCrMQ.png)




---

## 使用者管理
### 新增user
* useradd
    *`useradd std01`
    ![](https://i.imgur.com/8VZaCck.png)
    ![](https://i.imgur.com/2wX6hkj.png)
    *`tail /etc/shadow` -- 沒有密碼
    ![](https://i.imgur.com/fcpB8Zk.png)
    
### 更改密碼
* passwd
     #### 使用root更改密碼(可以任性)
    * `passwd std01`
    ![](https://i.imgur.com/IakHYjD.png)
    * 測試登入
    ![](https://i.imgur.com/RB2AzMS.png)
    
    #### 用自己帳號更改密碼(密碼需嚴謹)
    ![](https://i.imgur.com/NiQfyrf.png)

### 刪除user
* userdel
    * `userdel std01` -- 無法刪除到家目錄的std01，僅砍掉帳號資訊
    ![](https://i.imgur.com/FpD2hTI.png)
    
        >`rm -rf /home/ntub1001` -- 將沒砍乾淨的砍掉
        
        ![](https://i.imgur.com/nhsG8r7.png)


    * `userdel -r std01` -- 一次砍乾淨
    ![](https://i.imgur.com/grQkiME.png)

### 增加group
* groupadd
    `groupadd g1`
    `grep g1 /etc/group` -- 查看g1
    ![](https://i.imgur.com/NWExkIx.png)
    > `useradd -g g1 std01` --將user->std01的主要群組設定為g1
    
     ![](https://i.imgur.com/1S7stRY.png)
    > `useradd -g g1 -G g2 std003` --將user->std003的主要群組設定為g1,次要群組為g2
    
     ![](https://i.imgur.com/io7gkJS.png)

* groupdel

### 更改user group
* usermod - 更改使用者群組
    `usermod -g editor std01`
    ![](https://i.imgur.com/oJC17ln.png)

    




---

# [3/25 筆記](https://hackmd.io/gr7Hiqa5RrGMHT7OrJja6Q)