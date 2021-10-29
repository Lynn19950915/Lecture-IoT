<h2 align="center">Lesson 02: 開發環境準備</h2>

### 2-1 環境準備
1. CentOS: 下載 x86_64 DVD iso 檔光碟。

2. VMWare
- 下載、安裝 VMWare workstation player。
- 配置虛擬環境，設定硬體條件
  - CPU (處理器): 4 核心 (2x2)
  - RAM (記憶體): 4G 
  - HDD (硬碟): 20G
- 安裝檢查：以 root 身分登入
```
(terminal)
# 檢查網路設定
> ifconfig
# 執行系統更新
> yum update -y
```

---
### 2-2 工具選擇比較
1. 優勢分析
- Logstash: 可負責資料篩濾、清洗與轉換。
- Metricbeat: `輕量且即時串流`之蒐集元件。

2. 情境分析

| 資料... | 需清洗、轉換 | 可直接寫入儲放 |
| :---: | :---: | :---: |
| **需即時串流處理** | Metricbeat+Logstash | `Metricbeat`(+Logstash) |
| **可批次處理** | `Logstash` |  Kafka/Logstash |
