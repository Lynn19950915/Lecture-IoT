<h2 align="center">Lesson 08: ELK 工具流實例</h2>

### 8-1 ELK 經典流程
1. 靜態資料 (csv 檔)
- 下載 csv 檔資料，Logstash直接匯入資料庫。
- 檢查 Elasticsearch 匯入，Kibana 建立 index-pattern。
- 探索式資料觀察：dashboard/timelion。

2. 動態資料庫 (MySQL)
- 連接 MySQL，Logstash 連接設定 (input, filter, output)。
- 檢查 Elasticsearch 匯入，Kibana 建立 index-pattern。
- 探索式資料觀察：dashboard/timelion。

---
### 8-2 Kafka工具流
1. jupyter (PyCharm) 安裝 Pandasticsearch。
2. 執行兩隻 ipynb 檔
- producer 模擬資料寫入
- consumer 接收模擬資料
3. 檢查 Elasticsearch 匯入，Kibana 建立 index-pattern。
4. 探索式資料觀察：dashboard/timelion。

---
### 8-3 時間序列分析
.es (index=索引名稱, timefield=指定時間欄位, metric=函數：資料欄位)<br>
.if (比較方式, 比較值, true 運算, false 運算)
```
> .es(index=metricbeat-*, timefield="timestamp", metric="avg: system.cpu.user.pct")
> .if(lt, 60, 100, 0)
```
