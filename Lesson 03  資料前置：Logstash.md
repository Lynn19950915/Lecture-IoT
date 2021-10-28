<h2 align="center">Lesson 03: 資料前置：Logstash</h2>

### 3-1 Logstash 概論
Logstash 扮演原始資料與儲存庫間的橋梁，其工作分為三類：<br>
- input: 從各種來源取得資料
- filter: 將原始資料做加工 (清洗、轉換等)
- output: 將資料儲放入資料庫<br>
註：對於無即時串流需求者，Logstash, Kafka 均可扮演取資料之中介角色。

---
### 3-2 安裝流程
1. 下載 Logstash
```
> wget https://artifacts.elastic.co/downloads/logstash/logstash-7.4.0.rpm
```

2. 安裝 Logstash
```
# Uvh: 若有則升級、無則安裝
> sudo rpm -Uvh logstash-7.4.0.rpm
```
| 檔案 | 位址 |
| :---: | :---: |
| 安裝檔 | ./usr/share/logstash |
| 設定檔 | ./etc/logstash/logstash.yml |
| log 檔 | ./var/log/logstash |

3. 安裝後檢查
```
> cd /usr/share/logstash
# 鍵盤為輸入源，screen 為輸出源
> bin/logstash -e "input {stdin{}} output {stdout{}}"
```
