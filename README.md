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

##### 3.  Enjoy your Hadoop Cluster
By default, running the command below will launch a Hadoop cluster with 3 nodes (1 master and 2 slaves):
```
./macOS/start-cluster.sh
```
If you want to customize the number of slave nodes, specify the total number of nodes (master + slaves) as an argument.
For example, to start a cluster with 1 master and 5 slaves (6 nodes total):
```sh
./linux/start-cluster.sh 6
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
