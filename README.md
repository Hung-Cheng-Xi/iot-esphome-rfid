# iot-esphome-rfid

這是一個基於 ESPHome 的 RFID 專案，使用 ESP32 開發板來讀取 RFID 標籤並將數據發送到 MQTT 伺服器。

## 安裝與設定

### 安裝 Python 版本

確保您已安裝 Python 3.12，您可以使用 `.python-version` 文件來設定 Python 版本：

```bash
pyenv install 3.12
pyenv local 3.12
```

### 安裝依賴

使用 Poetry 安裝專案依賴：

```bash
poetry install
```

### 設定 ESPHome

編輯 esphome_project/secrets.yaml 文件，填寫您的 Wi-Fi、MQTT 等相關資訊：

```toml
wifi_ssid: "Your_WiFi_SSID"
wifi_password: "Your_WiFi_Password"
mqtt_broker: "Your_MQTT_Broker"
mqtt_username: "Your_MQTT_Username"
mqtt_password: "Your_MQTT_Password"
ota_password: "Your_OTA_Password"
api_password: "Your_API_Password"
```

### 編譯與上傳

使用 ESPHome 編譯並上傳固件到 ESP32：

```bash
cd esphome_project
esphome config esp32s_rfid.yaml # 檢查
esphome run esp32s_rfid.yaml
```

使用說明

1. 啟動設備
連接 ESP32 開發板並啟動設備，設備將自動連接到 Wi-Fi 並開始讀取 RFID 標籤。

2. 查看日誌
您可以通過 ESPHome 查看設備日誌：

```bash
esphome logs esp32s_rfid.yaml
```

### MQTT 數據

設備將讀取到的 RFID 標籤數據發送到 MQTT 伺服器，您可以在 MQTT 伺服器上查看相關數據。

## 文件

- esphome_project/esp32s_rfid.yaml - 主配置文件
- esphome_project/example/esp32s_example.yaml - 範例配置文件
- esphome_project/secrets.yaml - 機密信息配置文件
- pyproject.toml - Poetry 配置文件
- poetry.lock - 依賴鎖定文件
