# 開機管理程式
將安裝 GRUB。

## 前置作業
為 intel 處理器下載微碼（microcode）：
```shell
pacman -S intel-ucode
```

## 安裝 GRUB
先下載需要的套件：
```
pacman -S grub efibootmgr os-prober
```
* *os-prober*：可選，用來偵測 Windows 系統

進行安裝：
```
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
```

生成開機設定檔：
```
grub-mkconfig -o /boot/grub/grub.cfg
```

如果有需要 Windows 開機選項，得去調整 grub 設定，解鎖選項。
```
echo "GRUB_DISABLE_OS_PROBER=false" >> /etc/default/grub
```

此時再重新生成應可看到 Windows。