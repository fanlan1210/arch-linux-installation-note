# Step 1 網路連線設定
首先測試網路連線：
```shell
ping google.com
```

如果是有線網路，會自動連線，而無線網路需要再進行設定：
```shell
iwctl station <device> connect <SSID>
```
* `<device>`：無線網卡名稱（可透過 `iwctl device list` 查詢）
* `<SSID>`：欲連線的無線網路名稱

如果需要密碼將會進行提示輸入，完成後即連線成功。