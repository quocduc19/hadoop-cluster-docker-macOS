## Run Hadoop Cluster within Docker Containers

![alt tag](https://github.com/quocduc19/hadoop-cluster-docker-macOS/blob/main/hadoop-cluster-docker.png)


### 3 Nodes Hadoop Cluster

##### 1. clone github repository

```
git clone https://github.com/quocduc19/hadoop-cluster-docker-macOS
cd hadoop-cluster-docker-macOS
```

##### 2.  Build Docker Images (Optional)
> * If you don't have enough permissions, you may need to run the command as a superuser `sudo`.
```
./macOS/build-image.sh
```

##### 4. Verify the Installation

1️⃣ **Start the HDFS services:**  
```sh
start-dfs.sh
```
2️⃣ **Check active DataNodes:**
```sh
hdfs dfsadmin -report
```
