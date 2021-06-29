# Step 2 磁碟分割
基本上一個可開機的系統，至少會有開機磁區與 Linux 系統磁區，而後者又可以在進行更細緻的分割。

## 硬碟分割範例
* /dev/sda1：EFI System
* /dev/sda2：Linux（root）
* /dev/sda3：Linux（home）
* /dev/sda4：Swap

在此透過 `cgdisk` 進行磁碟分割：
```
cgdisk /dev/sda
```
### /dev/sda1：開機磁區
  * 大小建議為 256M ，類型為 EFI System
  * 該區作為系統開機磁區使用，若已存在，則不必再分割。

### /dev/sda2：Linux（root）
  * 大小自訂，類型為 Linux filesystem
  * 系統將會安裝至此分區

### /dev/sda3：Linux（home）
  * 大小自訂，類型為 Linux filesystem
  * 預計給儲存個人資料的家目錄使用

### /dev/sda4: Swap
  * 大小自訂，這裡使用 2G ，類型為 Linux Swap

基本上在分割時，都會習慣為 Linux 系統加上 Swap(置換) 分區，就像是 Windows 系統通常也會有 pagefile(分頁檔) 一樣。當然這個不是必須的，如果覺得自己的 RAM 容量非常足夠，那麼也不一定需要切出此分區。

另外，在系統安裝完成後，也可以透過建立以檔案形式存在的 swap file，來建立虛擬記憶體。

## 格式化與掛載新磁區

### 格式化系統磁區
```shell
mkfs.ext4 /dev/sda2
mkfs.ext4 /dev/sda3
```
### 格式化置換分區
```shell
mkswap /dev/sda4
```

### 掛載所需磁區
```shell
mount /dev/sda2 /mnt
mount /dev/sda3 /mnt/home
```

### 啟用置換分區
```shell
swapon /dev/sda4
```