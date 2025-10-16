# 🖥️ Raspberry Pi 5 Monitoring (Netdata & Grafana)

Мониторинг системы Raspberry Pi 5 с помощью **Netdata** и **Grafana**.  
Проект нацелен на визуализацию метрик (CPU, RAM, температура, сеть, аптайм и т.д.) в реальном времени.

---

## 🚀 Установка и настройка

### 1. Установка Netdata

```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh) --nightly-channel
sudo systemctl enable netdata
sudo systemctl start netdata
```

После установки проверь работу:
```bash
sudo systemctl status netdata
curl -I http://localhost:19999
```

Если всё верно — открой в браузере:
```
http://<IP_RPI>:19999
```

---

### 2. Установка Grafana

```bash
sudo apt-get install -y apt-transport-https software-properties-common
sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://packages.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
sudo apt-get update
sudo apt-get install grafana -y
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
```

Проверь работу Grafana:
```
http://<IP_RPI>:3000
```

---

### 3. Интеграция Netdata в Grafana

1. В Grafana добавь **Prometheus datasource**:
   - URL: `http://localhost:19999/api/v1/allmetrics?format=prometheus`
2. Импортируй дашборд (JSON-файл из репозитория).
3. Установи обновление панели каждые 10 секунд (`Refresh: 10s`).

---

## 📊 Пример визуализации

| Netdata | Grafana |
|----------|----------|
| ![Netdata Dashboard](https://github.com/Cayman152/rpi5-monitoring/blob/main/netdata.png) | ![Grafana Dashboard](https://github.com/Cayman152/rpi5-monitoring/blob/main/grafana.png) |

---

## 📁 Структура проекта

```
rpi5-monitoring/
├── dashboards/
│   └── rpi-netdata-dashboard-v2.json
├── screenshots/
│   ├── netdata.png
│   └── grafana.png
└── README.md
```

---

## 🧠 Основные метрики

- CPU Usage (%)
- CPU Temperature (°C)
- Memory Usage (MiB)
- System Uptime (hours / seconds)
- Network Traffic (eth0)

---

## 🧩 Используемые технологии

- **Netdata** — сбор и визуализация метрик
- **Grafana** — кастомные дашборды
- **Prometheus Format** — интеграция источников данных
- **Raspberry Pi 5** — хостинг и мониторинг

---

## 🧑‍💻 Автор

**NK**  
GitHub: [https://github.com/NK](https://github.com/NK)

---

# 🖥️ Raspberry Pi 5 Monitoring (Netdata & Grafana)

System monitoring setup for **Raspberry Pi 5** using **Netdata** and **Grafana**.  
Displays real-time CPU, RAM, temperature, network, and uptime metrics.

---

## 🚀 Setup

### 1. Install Netdata
```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh) --nightly-channel
sudo systemctl enable netdata
sudo systemctl start netdata
```

Access Netdata:
```
http://<IP_RPI>:19999
```

---

### 2. Install Grafana
```bash
sudo apt-get install -y apt-transport-https software-properties-common
sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://packages.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://packages.grafana.com/oss/deb stable main" | sudo tee /etc/apt/sources.list.d/grafana.list
sudo apt-get update
sudo apt-get install grafana -y
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
```

Access Grafana:
```
http://<IP_RPI>:3000
```

---

### 3. Connect Netdata to Grafana
1. Add a new **Prometheus datasource** in Grafana:
   - URL: `http://localhost:19999/api/v1/allmetrics?format=prometheus`
2. Import dashboard JSON from the repository.
3. Set refresh interval to `10s`.

---

## 📊 Visualization Example

| Netdata | Grafana |
|----------|----------|
| ![Netdata Dashboard](https://github.com/Cayman152/rpi5-monitoring/blob/main/netdata.png) | ![Grafana Dashboard](https://github.com/Cayman152/rpi5-monitoring/blob/main/grafana.png) |

---

## 🧠 Key Metrics

- CPU Usage
- CPU Temperature
- Memory Usage
- System Uptime
- Network Traffic

---

## 🧑‍💻 Author

**NK**  
GitHub: [https://github.com/NK](https://github.com/NK)
