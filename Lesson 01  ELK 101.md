<h2 align="center">Lesson 01: ELK 101</h2>

### 1-1 大數據導論
1. 數據處理的三大階段

| 階段 | 處理工作 | 常用工具 |
| :---: | :---: | :---: |
| 資料前置 | 生 (資料源)、流 (協定)、蒐 (前處理) | HTTP、FTP、`Logstash` |
| 資料取得 | 存 (儲存)、取 (取用)、算 (資料處理) | RDB、HDFS、`Elasticsearch`、Python |
| 資料分析 | 析 (分析)、用 (報表)、看 (解讀) | R、SPSS、Excel、`Kibana` |
 
2. ELK 工具
- Logstash 從各管道`抓取`資料、進行`加工轉換`－資料前置
- Elasticsearch 將資料進行`儲放、索引化`供查詢－資料處理
- Kibana 是資料`分析與視覺化`介面－資料分析

---
### 1-2 大數據技術挑戰 (4V)
1. Volume: 資料量龐大，需處理大量、複雜且不規律之資訊。

2. Variety: 資料`樣式繁雜`，通常是結構、半結構與非結構三者混合。

3. Velocity: 處理時間短，需在時限內完成大量資料運算處理。

4. Veracity: 處理過程中需辨識資料之`真實 (可用) 性`。
