<h2 align="center">Lesson 07: 資料分析：Kibana</h2>

### 7-1 Kibana 概論
Kibana 是很好的資料`視覺化介面`，主要可執行下列功能：<br>
- dashboard: 多種儀錶板工具的組合混搭
- timelion: `時間序列操作`分析
- managements: index 管理，資料彙整設定

### 7-2 安裝流程
1. 下載 Kibana
```shell
> wget https://artifacts.elastic.co/downloads/kibana/kibana-7.4.0-x86_64.rpm
```

2. 安裝 Kibana
```shell
# Uvh: 若有則升級、無則安裝
> sudo rpm -Uvh kibana-7.4.0-x86_64.rpm
> sudo chkconfig --add kibana
```
| 檔案 | 位址 |
| :---: | :---: |
| 安裝檔 | ./usr/share/kibana |
| 設定檔 | ./etc/kibana/kibana.yml |
| log 檔 | ./var/log/kibana |
  
3. 設定與啟動
```shell
> sudo vi /etc/kibana/kibana.yml
server.host: "0.0.0.0"
elasticsearch.hosts: "https://localhost:9200"

> sudo service kibana restart
(瀏覽器)
> http://localhost:5601
```

4. 啟動後檢查
```shell
> netstat -an | more
```
