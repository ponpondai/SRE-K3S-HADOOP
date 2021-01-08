# 製作第一個映像檔：core20.04
* 在 cvn71 虛擬主機, 執行以下命令
```
unzip core20.04.zip
tree core20.04/
```
![](https://i.imgur.com/wBzUkmS.png)
```
cd core20.04
```
* 檢視自動製作image檔案程式並執行
```
cat buildimg.sh
```
![](https://i.imgur.com/JgqeVOl.png)
```
./buildimg.sh
```
* 實建container進行測試
```
docker run --name d1 -it -d -p 22100:22 localhost/core20.04
ssh localhost -p 22100
```
![](https://i.imgur.com/XBPCh8O.png)
```
python --version
```
![](https://i.imgur.com/9ktXNyz.png)
```
exit
```
