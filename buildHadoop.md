# Hadoop系統建置
建置Hadoop系統規格：
* ResourceManger(rma)*1
* NameNode、Secondary NameNode (nna)*1
* 資料架構師用(adm100)*1
* 資料分析師，資料科學家用(ds101)*1
* DataNode、NodeManger (wka)*3

編輯HeadlessService讓pod之間可以名稱互通

```
apiVersion: v1
kind: Service
metadata:
  name: hdp
spec:
  selector:
    dt: hdp
  clusterIP: None
```
編輯yml創建Hadoop系統所需電腦
```
apiVersion: v1
kind: Pod
metadata:
  name: adm100 #名字
  labels:
    dt:  hdp #headless service名稱
spec:
  hostname: adm100
  subdomain: hdp #headless service名稱 才能註冊pod名稱到core dns
  containers:
  - name: adm100 #container名字
    image: dt210.img   
    imagePullPolicy: Never
    ports:
     - containerPort: 22
       hostPort: 22100
    stdin: true
    tty: true
    command: [/bin/bash]
  dnsConfig:
    searches:
    - hdp.default.svc.dt.io   #coredns subdomain搜尋順序
  nodeSelector:
  kubernetes.io/hostname : lcs83 #指定運行機台
```
一鍵建置機器
```
cd dt;cnt start
```
```
ssh adm100
```
啟動Hadoop系統
```
starthdfs;startyarn
```
確認啟動狀態
```
hls
```