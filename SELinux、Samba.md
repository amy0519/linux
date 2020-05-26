---
tags: linux,伺服器
---

# linux伺服器( 5/13 )- SELinux、Samba

## SELinux
> 有關於 SELinux 對 Apache 運作的影響，大致有如下問題：
> * 目錄權限無法存取
> * 程式把檔案寫入指定的目錄位置
> * 程式無法經由網路和別的系統服務交換資料
> * Apache 無法在標準的連埠服提供服務

### 示範SELnux的影響

* 建立檔案
`vi root-file.htm`
![](https://i.imgur.com/8uEVhIr.png)
    
![](https://i.imgur.com/Heyse8H.png)

![](https://i.imgur.com/BgXvrdN.png)
    
* 權限開最大
`chmod 777 root-file.htm`

![](https://i.imgur.com/GGJgqQg.png)

![](https://i.imgur.com/iri7dJI.png)

* 發現無法在瀏覽器顯示
![](https://i.imgur.com/KsPSZLp.png)

* 使用restorecon便可在瀏覽器顯示
```
restorecon root-file.htm
```
![](https://i.imgur.com/kW8sw5r.png)
    
![](https://i.imgur.com/bgmzgNu.png)












