# 雜項
## 安裝所需的無線網路工具
```
pacman -S iwd
```

## 安裝 AUR Helper：yay
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