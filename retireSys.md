# 退休手冊
* 新增一台DataNode
```
kubectl apply –f wka04.yml
```
* 確認新增 Data Node 是否加入 HDFS
```
hdfs  dfsadmin –refreshNodes
```
> 顯示Refresh nodes successful
```
hdfs  dfsadmin  -printTopology
```
![](https://i.imgur.com/eEpp9BD.png)
* 設定 Data Node
1. 編輯白名單
```
nano /opt/hadoop-2.10.1/etc/hadoop/hdfs.allow
```
2. 編輯除役名單
```
nano /opt/hadoop-2.10.1/etc/hadoop/hdfs.decommission
```
3. 設定白名單、除役名單路徑
```
nano /opt/hadoop-2.10.1/etc/hadoop/hdfs-site.xml
```
* 重新啟動HDFS
```
stophdfs; starthdfs
```
* 檢視 HDFS 運作資訊
```
hdfs dfsadmin -report
```
![](https://i.imgur.com/B47fmNB.png)
