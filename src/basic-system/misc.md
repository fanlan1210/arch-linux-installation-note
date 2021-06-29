# 雜項
## 安裝所需的無線網路工具
```
pacman -S iwd
```

## 安裝 AUR Helper：yay
AUR Helper 是泛指那些提供使用者可以簡單下載安裝 [Arch User Repository](https://aur.archlinux.org) 上套件的輔助程式，而這裡使用 yay 這個套件。

首先開啟 pacman 設定檔：
```
sudo vim /etc/pacman.conf
```

找到以下兩行(約在第93行)，將前方的 # 刪除：
```
#[multilib]
#Include = /etc/pacman.d/mirrorlist
```

下載 yay 及所需的依賴套件：
```
sudo pacman -Sy git
git clone https://aur.archlinux.org/yay.git
```

安裝 yay：
```
cd yay
makepkg -si
```