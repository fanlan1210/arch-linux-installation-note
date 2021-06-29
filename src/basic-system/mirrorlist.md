# 設定套件來源

重新排列pacman的鏡像站順序，可以提升下載的速度。

而設定方式主要有兩種：

1. 根據官網提供的[鏡像站列表](https://archlinux.org/mirrorlist/)手動編輯
2. 透過程式自動生成

## 手動編輯
```
vim /etc/pacman.d/mirrorlist
```

## 透過程式自動生成
可透過 reflector 來獲得最佳排序：
```shell
pacman -Sy reflector
reflector --verbose -l 5 --sort rate --country 'Taiwan' --save /etc/pacman.d/mirrorlist
```