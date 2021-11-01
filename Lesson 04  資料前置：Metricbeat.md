<h2 align="center">Lesson 04: 資料前置：Metricbeat</h2>

### 4-1 Metricbeat 概論
1. Metricbeat 具備`輕量化、即時`之特色，能協助串流資料之處理工作。

2. 與 Logstash 蒐集、前處理等工作不衝突，可銜接於前做為資料來源。
- 需串流處理，資料需要清洗、轉換：`Metricbeat－Logstash－Elasticsearch－Kibana`
- 需串流處理，資料可直接寫入儲放：`Metricbeat－Elasticsearch－Kibana`

3. 其他 beats 家族
- 參考 [https://www.elastic.co/products/beats](https://www.elastic.co/products/beats)，可直接將串流資料寫入 Elasticsearch 運用。
- 如 filebeat (log file), winlogbeat (windows log), auditbeat (監控 user 活動), functionbeat (雲端服務事件蒐集) 等。

---
### 4-2 安裝流程
1. 下載 Metricbeat
```shell
> wget https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.4.0-x86_64.rpm
```

2. 安裝 Metricbeat
```shell
# Uvh: 若有則升級、無則安裝
> sudo rpm -Uvh metricbeat-7.4.0-x86_64.rpm
```
| 檔案 | 位址 |
| :---: | :---: |
| 安裝檔 | ./usr/share/metricbeat |
| 設定檔 | ./etc/metricbeat/metricbeat.yml |
| log 檔 | ./var/log/metricbeat |

3. 設定與啟動
```shell
> sudo vi /etc/metricbeat/metricbeat.yml
setup.dashboards.enabled: true
output.elasticsearch: hosts: ["localhost:9200"]
setup.kibana: hosts: "localhost:5601"

> sudo service metricbeat start
(瀏覽器)
> http://localhost:5601
```

4. 安裝後檢查
```shell
> curl -XGET "http://localhost:9200/metricbeat-*/_search?pretty"
```
