# 安裝桌面環境

## 安裝 KDE
安裝 KDE 全套，並且啟用 Wayland 支援備用：
```
pacman -S xorg-server plasma plasma-wayland-session kde-applications
```

## 啟動圖形介面
```
systemctl enable --now sddm.service
```
