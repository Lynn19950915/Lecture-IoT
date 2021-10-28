<h2 align="center">Lesson 06: 資料取得：Elasticsearch (2)</h2>

### 安裝流程
1. 下載 jdk8、Elasticsearch
```
> wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.rpm

> wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.4.0.rpm
```

2. 安裝 Elasticsearch
```
> sudo yum remove java
# Uvh: 若有則升級、無則安裝
> sudo rpm -Uvh jdk-8u131-linux-x64.rpm
> java -version

# Uvh: 若有則升級、無則安裝
> sudo rpm -Uvh elasticsearch-7.4.0.rpm
> sudo chkconfig --add elasticsearch
```
| 檔案 | 位址 |
| :---: | :---: |
| 安裝檔 | ./usr/share/elasticsearch |
| 設定檔 | ./etc/elasticsearch/elasticsearch.yml |
| log 檔 | ./var/log/elasticsearch |

3. 設定與啟動
```
> sudo vi /etc/sysconfig/elasticsearch
JAVA_HOME=/usr/bin/java
# 設定使用記憶體為 2G
ES_JAVA_OPTS="-Xms2g -Xmx2g"
MAX_OPEN_FILES=65536
 
> sudo vi /etc/elasticsearch/elasticsearch.yml
cluster.name: es-lab
network.host: 0.0.0.0
path.data: /var/lib/elasticsearch
path.logs: /var/log/elasticsearch
bootstrap.memory_lock: false
bootstrap.system_call_filter: false

> sudo vi /etc/security/limits.conf
elasticsearch - nofile 65536
elasticsearch - nproc 4096  

> sudo service elasticsearch restart
> sudo service elasticsearch status
```

4. 啟動後檢查
```
> sudo tail -20 /var/log/elasticsearch/es-lab.log
> sudo service elasticsearch status

# 觀察佔用 port 埠位 (0:::9200, 0:::9300)
> netstat -an | more
> curl -XGET "http://localhost:9200"
```
