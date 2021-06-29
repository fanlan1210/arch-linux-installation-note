# 輸入法與字型

## 安裝輸入法：RIME
安裝 RIME 本體與注音元件：
```
pacman -S ibus-rime rime-bopomofo
```

透過 KDE 輸入法視窗啟用：
```
ibus-daemon -drx --panel=/usr/lib/kimpanel-ibus-panel
```

## 字型：noto fonts
```
pacman -S noto-fonts noto-fonts-cjk noto-fonts-emoji
```
