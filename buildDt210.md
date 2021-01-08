# 準備製作 dt210.img Image
在 cvn71 虛擬主機, 執行以下命令
```
cd ~/wk; unzip dt210.img.zip; tree -L 1 dt210.img/
```
![](https://i.imgur.com/XNfU144.png)

```
cd ~/wk/dt210.img
```
# 修改HDFS設定檔
```
tree hdp210
```
![](https://i.imgur.com/kUBprHS.png)
* 設定namenode
```
nano hdp210/core-site.xml
```
> 新增rbean=soup;gbean=soup,rice;ybean=rice
![](https://i.imgur.com/bzMneCQ.png)
* 設定NameNode、DataNode儲存位置，以及最高使用者
```
nano hdp210/hdfs-site.xml
```
![](https://i.imgur.com/bTstVPd.png)
* hadoop-JAVA程式設定
```
nano hdp210/hadoop-env.sh
```
![](https://i.imgur.com/H7b7zb0.png)
* 查閱單一Node Manager運算資源
* 查閱單一Container可用運算資源
```
cat hdp210/yarn-site.xml
```
* 查閱MapReduce程式運算資源
```
cat hdp210/mapred-site.xml
```
# 開始製作第二個映像檔：dt210.img
* 實建container進行測試
```
docker run --name d2 -it -d -p 22100:22 docker.io/library/dt210.img bash
```
```
ssh localhost -p 22100
```
![](https://i.imgur.com/XBPCh8O.png)
```
hadoop checknative
```
![](https://i.imgur.com/G9CTMme.png)
```
exit
```
* 佈署dt210.img Docker Image
```
scp dt210.img.tar *master IP*:~
```
```
ssh *master IP*
```
```
sudo ctr images import dt210.img.tar
```
```
exit
```