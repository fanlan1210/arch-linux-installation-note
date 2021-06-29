# 安裝系統本體

## 安裝基本套件包
```
pacstrap /mnt base base-devel
```
此時將會自動下載並建立基本系統架構。

## 建立 fstab
fstab 提供了 Linux 檔案系統的相關資訊，描述了儲存裝置及其相關磁區如何初始化，與掛載至整個系統。

```shell
genfstab -U /mnt >> /mnt/etc/fstab
```

## 切換至新系統裡
`chroot` 是切換根資料夾的位置指令，而 `arch-chroot` 除了有前述作用外，還會將一些前置設定帶入。
```shell
arch-chroot /mnt
```

## 時間設定
設定時區：
```shell
timedatectl set-timezone Asia/Taipei
```

透過網路同步時間：
```shell
timedatectl set-ntp true
```

## 語言環境設定
可以自行至 `/etc/locale.gen` 取消對應語言的註解，這裡偷懶用 `echo` 的方式處理：
```bash
echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen
echo "zh_TW.UTF-8 UTF-8" >> /etc/locale.gen
locale-gen
localectl set-locale en_US.UTF-8
```

## 設定電腦名稱
```shell
hostnamectl set-hostname <your-pc-name>
```

## Linux 核心安裝
```shell
pacman -S linux
```

## 使用者設定
在建立新使用者之前，先為 root 設定密碼：
```shell
passwd
```

### sudo 群組設定
```shell
visudo
```

找到該行(約第86行)，將其取消註解：
```
#%wheel     ALL=(ALL)    ALL
```

或新增一行：
```
%<your-group-name>    ALL=(ALL)    ALL
```

### 建立新使用者
```
useradd -m <your-username>
passwd <your-username>
```

將其加入至 sudo 群組，使其擁有管理權限：
```
usermod <your-user-name> -aG <your-group-name>
```