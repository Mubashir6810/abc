# SE446 – Milestone 2: Spark ML Pipeline

**Group 10**

---

## Team Members

| Name             | Student ID |
| ---------------- | ---------- |
| Alanoud Almeniya | 231385     |
| Lina Dardeer     | 231709     |
| Masa Abara       | 231837     |
| Noura Altuwaijri | 231222     |

---

## Executive Summary

This project analyzes the Chicago Crimes dataset using  Apache Spark. IN milestone 1 MapReduce was used for batch processing, while Spark enabled faster in-memory computation and machine learning modeling. The results show that Spark is more efficient, easier to use, and supports advanced analytics.

---

##  M1 vs M2 Comparison (Tasks 1–4)

### Task 1: Crime Type Analysis

| Rank | Crime Type          | MapReduce (M1) | Spark (M2) 
| ---- | ------------------- | -------------- | ---------- 
| 1    | THEFT               | 2054           | 2054       
| 2    | BATTERY             | 1728           | 1728      
| 3    | CRIMINAL DAMAGE     | 1062           | 1062       
| 4    | MOTOR VEHICLE THEFT | 948            | 948        
| 5    | ASSAULT             | 878            | 878        


---

###  Task 2: Location Hotspots

| Rank | Location    | MapReduce (M1) | Spark (M2) 
| ---- | ----------- | -------------- | ---------- 
| 1    | STREET      | 2737           | 2737       
| 2    | APARTMENT   | 1909           | 1909       
| 3    | RESIDENCE   | 1358           | 1358       
| 4    | SIDEWALK    | 536            | 536        
| 5    | PARKING LOT | 362            | 362        

---

###  Task 3: Crime Trend Over Years

| Year | MapReduce (M1) | Spark (M2) |
| ---- | -------------- | ---------- |
| 2001 | 4              | 4          |
| 2005 | 19             | 19         |
| 2010 | 5              | 5          |
| 2015 | 28             | 28         |
| 2017 | 49             | 49         |


---

###  Task 4: Arrest Rate Analysis
**Arrest rate in M1**
false 8717 
true  1283

| Metric      | MapReduce (M1) | Spark (M2) |
| ----------- | -------------- | ---------- |
| Arrest Rate | ~0.1283        | 0.1283     |

Arrest rate is ~12.83% in both implementations.

---

##  Performance Comparison

| Feature         | MapReduce  | Spark     |
| --------------- | ---------- | --------- |
| Speed           | Slow       | Fast      |

**Conclusion:** Spark is faster, simpler, and more powerful.

---

##  ML Results Summary

### Best Model: Random Forest

| Metric    | Value  |
| --------- | ------ |
| AUC-ROC   | 0.7526 |
| Accuracy  | 0.8964 |
| F1 Score  | 0.8675 |
| Precision | 0.8914 |
| Recall    | 0.8964 |

**Interpretation:**

* Random Forest performed best due to handling non-linear patterns
* `crime_index` was the most important feature
* Logistic Regression performed worse due to linear assumptions

---

##  Deployment Evidence

### Task 9: Local Execution

<img src="output/task%209.png" width="600">

###  Task 10: Cluster Execution -- Client Mode

<img src="output/task%2010.png" width="600">

###  Task 11: Cluster Execution -- spark-submit

<img src="output/task%2011.png" width="600">

---

##  Member Contributions

| Member           | Tasks      |
| ---------------- | ---------- |
| Alanoud Almeniya | Tasks 1–2  |
| Lina Dardeer     | Tasks 3–4  |
| Masa Abara       | Tasks 5–7  |
| Noura Altuwaijri | Tasks 8–11 |

---

##  Spark-Submit Terminal Output

```
naltuwajiri@master-node:~$ nano m2_spark_ml.py
naltuwajiri@master-node:~$ spark-submit  --master yarn  --deploy-mode client  --num-executors 2  --executor-memory 1g  --executor-cores 1  --conf spark.pyspark.python=python3  --conf spark.executorEnv.PYTHONPATH=/home/naltuwajiri/.local/lib/python3.10/site-packages  --conf spark.yarn.appMasterEnv.PYTHONPATH=/home/naltuwajiri/.local/lib/python3.10/site-packages  m2_spark_ml.py
26/05/01 05:14:50 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
26/05/01 05:14:52 INFO SparkContext: Running Spark version 3.5.4
26/05/01 05:14:52 INFO SparkContext: OS info Linux, 5.15.0-170-generic, amd64
26/05/01 05:14:52 INFO SparkContext: Java version 11.0.30
26/05/01 05:14:52 INFO ResourceUtils: ==============================================================
26/05/01 05:14:52 INFO ResourceUtils: No custom resources configured for spark.driver.
26/05/01 05:14:52 INFO ResourceUtils: ==============================================================
26/05/01 05:14:52 INFO SparkContext: Submitted application: M2 Spark ML
26/05/01 05:14:52 INFO ResourceProfile: Default ResourceProfile created, executor resources: Map(cores -> name: cores, amount: 1, script: , vendor: , memory -> name: memory, amount: 1024, script: , vendor: , offHeap -> name: offHeap, amount: 0, script: , vendor: ), task resources: Map(cpus -> name: cpus, amount: 1.0)
26/05/01 05:14:52 INFO ResourceProfile: Limiting resource is cpus at 1 tasks per executor
26/05/01 05:14:52 INFO ResourceProfileManager: Added ResourceProfile id: 0
26/05/01 05:14:52 INFO SecurityManager: Changing view acls to: naltuwajiri
26/05/01 05:14:52 INFO SecurityManager: Changing modify acls to: naltuwajiri
26/05/01 05:14:52 INFO SecurityManager: Changing view acls groups to:
26/05/01 05:14:52 INFO SecurityManager: Changing modify acls groups to:
26/05/01 05:14:52 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users with view permissions: naltuwajiri; groups with view permissions: EMPTY; users with modify permissions: naltuwajiri; groups with modify permissions: EMPTY
26/05/01 05:14:53 INFO Utils: Successfully started service 'sparkDriver' on port 43833.
26/05/01 05:14:53 INFO SparkEnv: Registering MapOutputTracker
26/05/01 05:14:53 INFO SparkEnv: Registering BlockManagerMaster
26/05/01 05:14:53 INFO BlockManagerMasterEndpoint: Using org.apache.spark.storage.DefaultTopologyMapper for getting topology information
26/05/01 05:14:53 INFO BlockManagerMasterEndpoint: BlockManagerMasterEndpoint up
26/05/01 05:14:53 INFO SparkEnv: Registering BlockManagerMasterHeartbeat
26/05/01 05:14:53 INFO DiskBlockManager: Created local directory at /tmp/blockmgr-eda1acba-f6fd-422d-8844-d67d0792ff8f
26/05/01 05:14:53 INFO MemoryStore: MemoryStore started with capacity 127.2 MiB
26/05/01 05:14:54 INFO SparkEnv: Registering OutputCommitCoordinator
26/05/01 05:14:54 INFO JettyUtils: Start Jetty 0.0.0.0:4040 for SparkUI
26/05/01 05:14:54 INFO Utils: Successfully started service 'SparkUI' on port 4040.
26/05/01 05:14:54 INFO SparkContext: Added JAR file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/commons-pool2-2.12.0.jar at spark://master-node:43833/jars/commons-pool2-2.12.0.jar with timestamp 1777612492574
26/05/01 05:14:54 INFO SparkContext: Added JAR file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/kafka-clients-3.9.0.jar at spark://master-node:43833/jars/kafka-clients-3.9.0.jar with timestamp 1777612492574
26/05/01 05:14:54 INFO SparkContext: Added JAR file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/spark-sql-kafka-0-10_2.12-3.5.4.jar at spark://master-node:43833/jars/spark-sql-kafka-0-10_2.12-3.5.4.jar with timestamp 1777612492574
26/05/01 05:14:54 INFO SparkContext: Added JAR file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/spark-token-provider-kafka-0-10_2.12-3.5.4.jar at spark://master-node:43833/jars/spark-token-provider-kafka-0-10_2.12-3.5.4.jar with timestamp 1777612492574
26/05/01 05:14:55 INFO DefaultNoHARMFailoverProxyProvider: Connecting to ResourceManager at master-node/134.209.172.50:8032
26/05/01 05:14:56 INFO Configuration: resource-types.xml not found
26/05/01 05:14:56 INFO ResourceUtils: Unable to find 'resource-types.xml'.
26/05/01 05:14:56 INFO Client: Verifying our application has not requested more than the maximum memory capability of the cluster (1536 MB per container)
26/05/01 05:14:56 INFO Client: Will allocate AM container, with 640 MB memory including 384 MB overhead
26/05/01 05:14:56 INFO Client: Setting up container launch context for our AM
26/05/01 05:14:56 INFO Client: Setting up the launch environment for our AM container
26/05/01 05:14:56 INFO Client: Preparing resources for our AM container
26/05/01 05:14:56 INFO Client: Uploading resource file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/commons-pool2-2.12.0.jar -> hdfs://master-node:9000/user/naltuwajiri/.sparkStaging/application_1771402826595_0303/commons-pool2-2.12.0.jar
26/05/01 05:14:57 INFO Client: Uploading resource file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/kafka-clients-3.9.0.jar -> hdfs://master-node:9000/user/naltuwajiri/.sparkStaging/application_1771402826595_0303/kafka-clients-3.9.0.jar
26/05/01 05:14:58 INFO Client: Uploading resource file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/spark-sql-kafka-0-10_2.12-3.5.4.jar -> hdfs://master-node:9000/user/naltuwajiri/.sparkStaging/application_1771402826595_0303/spark-sql-kafka-0-10_2.12-3.5.4.jar
26/05/01 05:14:58 INFO Client: Uploading resource file:/opt/spark-3.5.4-bin-hadoop3/jars/kafka/spark-token-provider-kafka-0-10_2.12-3.5.4.jar -> hdfs://master-node:9000/user/naltuwajiri/.sparkStaging/application_1771402826595_0303/spark-token-provider-kafka-0-10_2.12-3.5.4.jar
26/05/01 05:14:59 INFO Client: Uploading resource file:/opt/spark-3.5.4-bin-hadoop3/python/lib/pyspark.zip -> hdfs://master-node:9000/user/naltuwajiri/.sparkStaging/application_1771402826595_0303/pyspark.zip
26/05/01 05:14:59 INFO Client: Uploading resource file:/opt/spark-3.5.4-bin-hadoop3/python/lib/py4j-0.10.9.7-src.zip -> hdfs://master-node:9000/user/naltuwajiri/.sparkStaging/application_1771402826595_0303/py4j-0.10.9.7-src.zip
26/05/01 05:15:00 INFO Client: Uploading resource file:/tmp/spark-52d769b0-971b-45f3-95c1-88316f86ffde/__spark_conf__14724547555176516121.zip -> hdfs://master-node:9000/user/naltuwajiri/.sparkStaging/application_1771402826595_0303/__spark_conf__.zip
26/05/01 05:15:02 INFO SecurityManager: Changing view acls to: naltuwajiri
26/05/01 05:15:02 INFO SecurityManager: Changing modify acls to: naltuwajiri
26/05/01 05:15:02 INFO SecurityManager: Changing view acls groups to:
26/05/01 05:15:02 INFO SecurityManager: Changing modify acls groups to:
26/05/01 05:15:02 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users with view permissions: naltuwajiri; groups with view permissions: EMPTY; users with modify permissions: naltuwajiri; groups with modify permissions: EMPTY
26/05/01 05:15:02 INFO Client: Submitting application application_1771402826595_0303 to ResourceManager
26/05/01 05:15:02 INFO YarnClientImpl: Submitted application application_1771402826595_0303
26/05/01 05:15:03 INFO Client: Application report for application_1771402826595_0303 (state: ACCEPTED)
26/05/01 05:15:03 INFO Client:
         client token: N/A
         diagnostics: AM container is launched, waiting for AM container to Register with RM
         ApplicationMaster host: N/A
         ApplicationMaster RPC port: -1
         queue: root.default
         start time: 1777612502182
         final status: UNDEFINED
         tracking URL: http://master-node:8088/proxy/application_1771402826595_0303/
         user: naltuwajiri
26/05/01 05:15:15 INFO Client: Application report for application_1771402826595_0303 (state: RUNNING)
26/05/01 05:15:15 INFO Client:
         client token: N/A
         diagnostics: N/A
         ApplicationMaster host: 146.190.147.119
         ApplicationMaster RPC port: -1
         queue: root.default
         start time: 1777612502182
         final status: UNDEFINED
         tracking URL: http://master-node:8088/proxy/application_1771402826595_0303/
         user: naltuwajiri
26/05/01 05:15:15 INFO YarnClientSchedulerBackend: Application application_1771402826595_0303 has started running.
26/05/01 05:15:15 INFO Utils: Successfully started service 'org.apache.spark.network.netty.NettyBlockTransferService' on port 35479.
26/05/01 05:15:15 INFO NettyBlockTransferService: Server created on master-node:35479
26/05/01 05:15:15 INFO BlockManager: Using org.apache.spark.storage.RandomBlockReplicationPolicy for block replication policy
26/05/01 05:15:15 INFO BlockManagerMaster: Registering BlockManager BlockManagerId(driver, master-node, 35479, None)
26/05/01 05:15:15 INFO BlockManagerMasterEndpoint: Registering block manager master-node:35479 with 127.2 MiB RAM, BlockManagerId(driver, master-node, 35479, None)
26/05/01 05:15:15 INFO BlockManagerMaster: Registered BlockManager BlockManagerId(driver, master-node, 35479, None)
26/05/01 05:15:15 INFO BlockManager: Initialized BlockManager: BlockManagerId(driver, master-node, 35479, None)
26/05/01 05:15:15 INFO SingleEventLogFileWriter: Logging events to hdfs:/spark-logs/application_1771402826595_0303.inprogress
26/05/01 05:15:16 INFO YarnClientSchedulerBackend: Add WebUI Filter. org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter, Map(PROXY_HOSTS -> master-node, PROXY_URI_BASES -> http://master-node:8088/proxy/application_1771402826595_0303), /proxy/application_1771402826595_0303
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /jobs: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /jobs/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /jobs/job: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /jobs/job/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /stages: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /stages/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /stages/stage: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /stages/stage/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /stages/pool: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /stages/pool/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /storage: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /storage/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /storage/rdd: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /storage/rdd/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /environment: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /environment/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /executors: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /executors/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /executors/threadDump: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /executors/threadDump/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /executors/heapHistogram: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /executors/heapHistogram/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /static: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /api: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /jobs/job/kill: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /stages/stage/kill: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:16 INFO ServerInfo: Adding filter to /metrics/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:17 INFO YarnSchedulerBackend$YarnSchedulerEndpoint: ApplicationMaster registered as NettyRpcEndpointRef(spark-client://YarnAM)
26/05/01 05:15:24 INFO YarnClientSchedulerBackend: SchedulerBackend is ready for scheduling beginning after waiting maxRegisteredResourcesWaitingTime: 30000000000(ns)
Spark Session Started
26/05/01 05:15:25 INFO SharedState: Setting hive.metastore.warehouse.dir ('null') to the value of spark.sql.warehouse.dir.
26/05/01 05:15:25 INFO SharedState: Warehouse path is 'hdfs://master-node:9000/user/hive/warehouse'.
26/05/01 05:15:25 INFO ServerInfo: Adding filter to /SQL: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:25 INFO ServerInfo: Adding filter to /SQL/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:25 INFO ServerInfo: Adding filter to /SQL/execution: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:25 INFO ServerInfo: Adding filter to /SQL/execution/json: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:25 INFO ServerInfo: Adding filter to /static/sql: org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter
26/05/01 05:15:27 INFO InMemoryFileIndex: It took 147 ms to list leaf files for 1 paths.
26/05/01 05:15:27 INFO InMemoryFileIndex: It took 21 ms to list leaf files for 1 paths.
26/05/01 05:15:33 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:15:33 INFO FileSourceStrategy: Post-Scan Filters: (length(trim(value#0, None)) > 0)
26/05/01 05:15:33 INFO YarnSchedulerBackend$YarnDriverEndpoint: Registered executor NettyRpcEndpointRef(spark-client://Executor) (164.92.103.148:51604) with ID 1,  ResourceProfileId 0
26/05/01 05:15:33 INFO BlockManagerMasterEndpoint: Registering block manager worker-node-1:34163 with 413.9 MiB RAM, BlockManagerId(1, worker-node-1, 34163, None)
26/05/01 05:15:34 INFO CodeGenerator: Code generated in 709.251108 ms
26/05/01 05:15:34 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 317.2 KiB, free 126.9 MiB)
26/05/01 05:15:35 INFO MemoryStore: Block broadcast_0_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.8 MiB)
26/05/01 05:15:35 INFO BlockManagerInfo: Added broadcast_0_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:15:35 INFO SparkContext: Created broadcast 0 from csv at NativeMethodAccessorImpl.java:0
26/05/01 05:15:35 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:15:35 INFO SparkContext: Starting job: csv at NativeMethodAccessorImpl.java:0
26/05/01 05:15:35 INFO DAGScheduler: Got job 0 (csv at NativeMethodAccessorImpl.java:0) with 1 output partitions
26/05/01 05:15:35 INFO DAGScheduler: Final stage: ResultStage 0 (csv at NativeMethodAccessorImpl.java:0)
26/05/01 05:15:35 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:15:35 INFO DAGScheduler: Missing parents: List()
26/05/01 05:15:35 INFO DAGScheduler: Submitting ResultStage 0 (MapPartitionsRDD[3] at csv at NativeMethodAccessorImpl.java:0), which has no missing parents
26/05/01 05:15:36 INFO MemoryStore: Block broadcast_1 stored as values in memory (estimated size 13.5 KiB, free 126.8 MiB)
26/05/01 05:15:36 INFO MemoryStore: Block broadcast_1_piece0 stored as bytes in memory (estimated size 6.4 KiB, free 126.8 MiB)
26/05/01 05:15:36 INFO BlockManagerInfo: Added broadcast_1_piece0 in memory on master-node:35479 (size: 6.4 KiB, free: 127.1 MiB)
26/05/01 05:15:36 INFO SparkContext: Created broadcast 1 from broadcast at DAGScheduler.scala:1585
26/05/01 05:15:36 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 0 (MapPartitionsRDD[3] at csv at NativeMethodAccessorImpl.java:0) (first 15 tasks are for partitions Vector(0))
26/05/01 05:15:36 INFO YarnScheduler: Adding task set 0.0 with 1 tasks resource profile 0
26/05/01 05:15:36 INFO TaskSetManager: Starting task 0.0 in stage 0.0 (TID 0) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10135 bytes)
26/05/01 05:15:37 INFO BlockManagerInfo: Added broadcast_1_piece0 in memory on worker-node-1:34163 (size: 6.4 KiB, free: 413.9 MiB)
26/05/01 05:15:42 INFO BlockManagerInfo: Added broadcast_0_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:15:45 INFO TaskSetManager: Finished task 0.0 in stage 0.0 (TID 0) in 8917 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:15:45 INFO YarnScheduler: Removed TaskSet 0.0, whose tasks have all completed, from pool
26/05/01 05:15:45 INFO DAGScheduler: ResultStage 0 (csv at NativeMethodAccessorImpl.java:0) finished in 9.266 s
26/05/01 05:15:45 INFO DAGScheduler: Job 0 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:15:45 INFO YarnScheduler: Killing all running tasks in stage 0: Stage finished
26/05/01 05:15:45 INFO DAGScheduler: Job 0 finished: csv at NativeMethodAccessorImpl.java:0, took 9.472780 s
26/05/01 05:15:45 INFO CodeGenerator: Code generated in 33.247251 ms
26/05/01 05:15:45 INFO BlockManagerInfo: Removed broadcast_1_piece0 on master-node:35479 in memory (size: 6.4 KiB, free: 127.1 MiB)
26/05/01 05:15:45 INFO BlockManagerInfo: Removed broadcast_1_piece0 on worker-node-1:34163 in memory (size: 6.4 KiB, free: 413.9 MiB)
26/05/01 05:15:45 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:15:45 INFO FileSourceStrategy: Post-Scan Filters:
26/05/01 05:15:45 INFO MemoryStore: Block broadcast_2 stored as values in memory (estimated size 317.2 KiB, free 126.5 MiB)
26/05/01 05:15:45 INFO MemoryStore: Block broadcast_2_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.5 MiB)
26/05/01 05:15:45 INFO BlockManagerInfo: Added broadcast_2_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:15:45 INFO SparkContext: Created broadcast 2 from csv at NativeMethodAccessorImpl.java:0
26/05/01 05:15:45 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:15:45 INFO SparkContext: Starting job: csv at NativeMethodAccessorImpl.java:0
26/05/01 05:15:45 INFO DAGScheduler: Got job 1 (csv at NativeMethodAccessorImpl.java:0) with 1 output partitions
26/05/01 05:15:45 INFO DAGScheduler: Final stage: ResultStage 1 (csv at NativeMethodAccessorImpl.java:0)
26/05/01 05:15:45 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:15:45 INFO DAGScheduler: Missing parents: List()
26/05/01 05:15:45 INFO DAGScheduler: Submitting ResultStage 1 (MapPartitionsRDD[9] at csv at NativeMethodAccessorImpl.java:0), which has no missing parents
26/05/01 05:15:46 INFO MemoryStore: Block broadcast_3 stored as values in memory (estimated size 30.4 KiB, free 126.4 MiB)
26/05/01 05:15:46 INFO MemoryStore: Block broadcast_3_piece0 stored as bytes in memory (estimated size 13.7 KiB, free 126.4 MiB)
26/05/01 05:15:46 INFO BlockManagerInfo: Added broadcast_3_piece0 in memory on master-node:35479 (size: 13.7 KiB, free: 127.1 MiB)
26/05/01 05:15:46 INFO SparkContext: Created broadcast 3 from broadcast at DAGScheduler.scala:1585
26/05/01 05:15:46 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 1 (MapPartitionsRDD[9] at csv at NativeMethodAccessorImpl.java:0) (first 15 tasks are for partitions Vector(0))
26/05/01 05:15:46 INFO YarnScheduler: Adding task set 1.0 with 1 tasks resource profile 0
26/05/01 05:15:46 INFO TaskSetManager: Starting task 0.0 in stage 1.0 (TID 1) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10135 bytes)
26/05/01 05:15:46 INFO BlockManagerInfo: Removed broadcast_0_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:15:46 INFO BlockManagerInfo: Removed broadcast_0_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:15:46 INFO BlockManagerInfo: Added broadcast_3_piece0 in memory on worker-node-1:34163 (size: 13.7 KiB, free: 413.9 MiB)
26/05/01 05:15:53 INFO BlockManagerInfo: Added broadcast_2_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:15:54 INFO TaskSetManager: Finished task 0.0 in stage 1.0 (TID 1) in 8615 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:15:54 INFO YarnScheduler: Removed TaskSet 1.0, whose tasks have all completed, from pool
26/05/01 05:15:54 INFO DAGScheduler: ResultStage 1 (csv at NativeMethodAccessorImpl.java:0) finished in 8.715 s
26/05/01 05:15:54 INFO DAGScheduler: Job 1 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:15:54 INFO YarnScheduler: Killing all running tasks in stage 1: Stage finished
26/05/01 05:15:54 INFO DAGScheduler: Job 1 finished: csv at NativeMethodAccessorImpl.java:0, took 8.747352 s
26/05/01 05:15:54 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:15:54 INFO FileSourceStrategy: Post-Scan Filters:
26/05/01 05:15:55 INFO BlockManagerInfo: Removed broadcast_3_piece0 on master-node:35479 in memory (size: 13.7 KiB, free: 127.1 MiB)
26/05/01 05:15:55 INFO BlockManagerInfo: Removed broadcast_3_piece0 on worker-node-1:34163 in memory (size: 13.7 KiB, free: 413.9 MiB)
26/05/01 05:15:55 INFO CodeGenerator: Code generated in 55.700725 ms
26/05/01 05:15:55 INFO MemoryStore: Block broadcast_4 stored as values in memory (estimated size 317.1 KiB, free 126.5 MiB)
26/05/01 05:15:55 INFO MemoryStore: Block broadcast_4_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.5 MiB)
26/05/01 05:15:55 INFO BlockManagerInfo: Added broadcast_4_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:15:55 INFO SparkContext: Created broadcast 4 from count at NativeMethodAccessorImpl.java:0
26/05/01 05:15:55 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:15:55 INFO DAGScheduler: Registering RDD 13 (count at NativeMethodAccessorImpl.java:0) as input to shuffle 0
26/05/01 05:15:55 INFO DAGScheduler: Got map stage job 2 (count at NativeMethodAccessorImpl.java:0) with 1 output partitions
26/05/01 05:15:55 INFO DAGScheduler: Final stage: ShuffleMapStage 2 (count at NativeMethodAccessorImpl.java:0)
26/05/01 05:15:55 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:15:55 INFO DAGScheduler: Missing parents: List()
26/05/01 05:15:55 INFO DAGScheduler: Submitting ShuffleMapStage 2 (MapPartitionsRDD[13] at count at NativeMethodAccessorImpl.java:0), which has no missing parents
26/05/01 05:15:55 INFO BlockManagerInfo: Removed broadcast_2_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:15:55 INFO MemoryStore: Block broadcast_5 stored as values in memory (estimated size 18.7 KiB, free 126.8 MiB)
26/05/01 05:15:55 INFO MemoryStore: Block broadcast_5_piece0 stored as bytes in memory (estimated size 9.2 KiB, free 126.8 MiB)
26/05/01 05:15:55 INFO BlockManagerInfo: Added broadcast_5_piece0 in memory on master-node:35479 (size: 9.2 KiB, free: 127.1 MiB)
26/05/01 05:15:55 INFO SparkContext: Created broadcast 5 from broadcast at DAGScheduler.scala:1585
26/05/01 05:15:55 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 2 (MapPartitionsRDD[13] at count at NativeMethodAccessorImpl.java:0) (first 15 tasks are for partitions Vector(0))
26/05/01 05:15:55 INFO YarnScheduler: Adding task set 2.0 with 1 tasks resource profile 0
26/05/01 05:15:55 INFO TaskSetManager: Starting task 0.0 in stage 2.0 (TID 2) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:15:55 INFO BlockManagerInfo: Removed broadcast_2_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:15:55 INFO BlockManagerInfo: Added broadcast_5_piece0 in memory on worker-node-1:34163 (size: 9.2 KiB, free: 413.9 MiB)
26/05/01 05:15:56 INFO BlockManagerInfo: Added broadcast_4_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:15:57 INFO TaskSetManager: Finished task 0.0 in stage 2.0 (TID 2) in 1753 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:15:57 INFO YarnScheduler: Removed TaskSet 2.0, whose tasks have all completed, from pool
26/05/01 05:15:57 INFO DAGScheduler: ShuffleMapStage 2 (count at NativeMethodAccessorImpl.java:0) finished in 1.900 s
26/05/01 05:15:57 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:15:57 INFO DAGScheduler: running: Set()
26/05/01 05:15:57 INFO DAGScheduler: waiting: Set()
26/05/01 05:15:57 INFO DAGScheduler: failed: Set()
26/05/01 05:15:57 INFO BlockManagerInfo: Removed broadcast_5_piece0 on master-node:35479 in memory (size: 9.2 KiB, free: 127.1 MiB)
26/05/01 05:15:57 INFO CodeGenerator: Code generated in 81.572952 ms
26/05/01 05:15:57 INFO BlockManagerInfo: Removed broadcast_5_piece0 on worker-node-1:34163 in memory (size: 9.2 KiB, free: 413.9 MiB)
26/05/01 05:15:57 INFO SparkContext: Starting job: count at NativeMethodAccessorImpl.java:0
26/05/01 05:15:57 INFO DAGScheduler: Got job 3 (count at NativeMethodAccessorImpl.java:0) with 1 output partitions
26/05/01 05:15:57 INFO DAGScheduler: Final stage: ResultStage 4 (count at NativeMethodAccessorImpl.java:0)
26/05/01 05:15:57 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 3)
26/05/01 05:15:57 INFO DAGScheduler: Missing parents: List()
26/05/01 05:15:57 INFO DAGScheduler: Submitting ResultStage 4 (MapPartitionsRDD[16] at count at NativeMethodAccessorImpl.java:0), which has no missing parents
26/05/01 05:15:57 INFO MemoryStore: Block broadcast_6 stored as values in memory (estimated size 12.5 KiB, free 126.8 MiB)
26/05/01 05:15:57 INFO MemoryStore: Block broadcast_6_piece0 stored as bytes in memory (estimated size 5.9 KiB, free 126.8 MiB)
26/05/01 05:15:57 INFO BlockManagerInfo: Added broadcast_6_piece0 in memory on master-node:35479 (size: 5.9 KiB, free: 127.1 MiB)
26/05/01 05:15:57 INFO SparkContext: Created broadcast 6 from broadcast at DAGScheduler.scala:1585
26/05/01 05:15:57 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 4 (MapPartitionsRDD[16] at count at NativeMethodAccessorImpl.java:0) (first 15 tasks are for partitions Vector(0))
26/05/01 05:15:57 INFO YarnScheduler: Adding task set 4.0 with 1 tasks resource profile 0
26/05/01 05:15:57 INFO TaskSetManager: Starting task 0.0 in stage 4.0 (TID 3) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9518 bytes)
26/05/01 05:15:58 INFO BlockManagerInfo: Added broadcast_6_piece0 in memory on worker-node-1:34163 (size: 5.9 KiB, free: 413.9 MiB)
26/05/01 05:15:58 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 0 to 164.92.103.148:51604
26/05/01 05:15:58 INFO TaskSetManager: Finished task 0.0 in stage 4.0 (TID 3) in 1013 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:15:58 INFO YarnScheduler: Removed TaskSet 4.0, whose tasks have all completed, from pool
26/05/01 05:15:58 INFO DAGScheduler: ResultStage 4 (count at NativeMethodAccessorImpl.java:0) finished in 1.059 s
26/05/01 05:15:58 INFO DAGScheduler: Job 3 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:15:58 INFO YarnScheduler: Killing all running tasks in stage 4: Stage finished
26/05/01 05:15:58 INFO DAGScheduler: Job 3 finished: count at NativeMethodAccessorImpl.java:0, took 1.083458 s
Total Rows: 10000
26/05/01 05:15:59 INFO BlockManagerInfo: Removed broadcast_6_piece0 on master-node:35479 in memory (size: 5.9 KiB, free: 127.1 MiB)
26/05/01 05:15:59 INFO BlockManagerInfo: Removed broadcast_6_piece0 on worker-node-1:34163 in memory (size: 5.9 KiB, free: 413.9 MiB)
Feature Engineering Done
Training Model...
26/05/01 05:15:59 INFO BlockManagerInfo: Removed broadcast_4_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.2 MiB)
26/05/01 05:15:59 INFO BlockManagerInfo: Removed broadcast_4_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:15:59 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:15:59 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:15:59 WARN SparkStringUtils: Truncated the string representation of a plan since it was too large. This behavior can be adjusted by setting 'spark.sql.debug.maxToStringFields'.
26/05/01 05:16:00 INFO CodeGenerator: Code generated in 219.140092 ms
26/05/01 05:16:00 INFO MemoryStore: Block broadcast_7 stored as values in memory (estimated size 317.1 KiB, free 126.9 MiB)
26/05/01 05:16:00 INFO MemoryStore: Block broadcast_7_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.8 MiB)
26/05/01 05:16:00 INFO BlockManagerInfo: Added broadcast_7_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:16:00 INFO SparkContext: Created broadcast 7 from collect at StringIndexer.scala:204
26/05/01 05:16:00 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:00 INFO DAGScheduler: Registering RDD 21 (collect at StringIndexer.scala:204) as input to shuffle 1
26/05/01 05:16:00 INFO DAGScheduler: Got map stage job 4 (collect at StringIndexer.scala:204) with 1 output partitions
26/05/01 05:16:00 INFO DAGScheduler: Final stage: ShuffleMapStage 5 (collect at StringIndexer.scala:204)
26/05/01 05:16:00 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:16:00 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:00 INFO DAGScheduler: Submitting ShuffleMapStage 5 (MapPartitionsRDD[21] at collect at StringIndexer.scala:204), which has no missing parents
26/05/01 05:16:00 INFO MemoryStore: Block broadcast_8 stored as values in memory (estimated size 53.7 KiB, free 126.8 MiB)
26/05/01 05:16:00 INFO MemoryStore: Block broadcast_8_piece0 stored as bytes in memory (estimated size 22.6 KiB, free 126.8 MiB)
26/05/01 05:16:00 INFO BlockManagerInfo: Added broadcast_8_piece0 in memory on master-node:35479 (size: 22.6 KiB, free: 127.1 MiB)
26/05/01 05:16:00 INFO SparkContext: Created broadcast 8 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:00 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 5 (MapPartitionsRDD[21] at collect at StringIndexer.scala:204) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:00 INFO YarnScheduler: Adding task set 5.0 with 1 tasks resource profile 0
26/05/01 05:16:00 INFO TaskSetManager: Starting task 0.0 in stage 5.0 (TID 4) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:01 INFO BlockManagerInfo: Added broadcast_8_piece0 in memory on worker-node-1:34163 (size: 22.6 KiB, free: 413.9 MiB)
26/05/01 05:16:03 INFO BlockManagerInfo: Added broadcast_7_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:05 INFO TaskSetManager: Finished task 0.0 in stage 5.0 (TID 4) in 5091 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:05 INFO YarnScheduler: Removed TaskSet 5.0, whose tasks have all completed, from pool
26/05/01 05:16:05 INFO DAGScheduler: ShuffleMapStage 5 (collect at StringIndexer.scala:204) finished in 5.273 s
26/05/01 05:16:05 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:05 INFO DAGScheduler: running: Set()
26/05/01 05:16:05 INFO DAGScheduler: waiting: Set()
26/05/01 05:16:05 INFO DAGScheduler: failed: Set()
26/05/01 05:16:05 INFO SparkContext: Starting job: collect at StringIndexer.scala:204
26/05/01 05:16:05 INFO DAGScheduler: Got job 5 (collect at StringIndexer.scala:204) with 1 output partitions
26/05/01 05:16:05 INFO DAGScheduler: Final stage: ResultStage 7 (collect at StringIndexer.scala:204)
26/05/01 05:16:05 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 6)
26/05/01 05:16:05 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:05 INFO DAGScheduler: Submitting ResultStage 7 (MapPartitionsRDD[24] at collect at StringIndexer.scala:204), which has no missing parents
26/05/01 05:16:05 INFO MemoryStore: Block broadcast_9 stored as values in memory (estimated size 49.9 KiB, free 126.7 MiB)
26/05/01 05:16:05 INFO MemoryStore: Block broadcast_9_piece0 stored as bytes in memory (estimated size 21.6 KiB, free 126.7 MiB)
26/05/01 05:16:05 INFO BlockManagerInfo: Added broadcast_9_piece0 in memory on master-node:35479 (size: 21.6 KiB, free: 127.1 MiB)
26/05/01 05:16:05 INFO SparkContext: Created broadcast 9 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:05 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 7 (MapPartitionsRDD[24] at collect at StringIndexer.scala:204) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:05 INFO YarnScheduler: Adding task set 7.0 with 1 tasks resource profile 0
26/05/01 05:16:05 INFO TaskSetManager: Starting task 0.0 in stage 7.0 (TID 5) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9518 bytes)
26/05/01 05:16:05 INFO BlockManagerInfo: Removed broadcast_8_piece0 on master-node:35479 in memory (size: 22.6 KiB, free: 127.1 MiB)
26/05/01 05:16:06 INFO BlockManagerInfo: Removed broadcast_8_piece0 on worker-node-1:34163 in memory (size: 22.6 KiB, free: 413.9 MiB)
26/05/01 05:16:06 INFO BlockManagerInfo: Added broadcast_9_piece0 in memory on worker-node-1:34163 (size: 21.6 KiB, free: 413.8 MiB)
26/05/01 05:16:06 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 1 to 164.92.103.148:51604
26/05/01 05:16:07 INFO TaskSetManager: Finished task 0.0 in stage 7.0 (TID 5) in 1075 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:07 INFO DAGScheduler: ResultStage 7 (collect at StringIndexer.scala:204) finished in 1.120 s
26/05/01 05:16:07 INFO DAGScheduler: Job 5 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:07 INFO YarnScheduler: Removed TaskSet 7.0, whose tasks have all completed, from pool
26/05/01 05:16:07 INFO YarnScheduler: Killing all running tasks in stage 7: Stage finished
26/05/01 05:16:07 INFO DAGScheduler: Job 5 finished: collect at StringIndexer.scala:204, took 1.140271 s
26/05/01 05:16:07 INFO CodeGenerator: Code generated in 55.305021 ms
26/05/01 05:16:07 INFO BlockManagerInfo: Removed broadcast_9_piece0 on master-node:35479 in memory (size: 21.6 KiB, free: 127.1 MiB)
26/05/01 05:16:07 INFO BlockManagerInfo: Removed broadcast_9_piece0 on worker-node-1:34163 in memory (size: 21.6 KiB, free: 413.9 MiB)
26/05/01 05:16:08 INFO Instrumentation: [3ebd16f5] Stage class: RandomForestClassifier
26/05/01 05:16:08 INFO Instrumentation: [3ebd16f5] Stage uid: RandomForestClassifier_dcaac4d1aaf1
26/05/01 05:16:08 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:08 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:08 INFO BlockManagerInfo: Removed broadcast_7_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.2 MiB)
26/05/01 05:16:08 INFO BlockManagerInfo: Removed broadcast_7_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:16:08 INFO CodeGenerator: Code generated in 281.918932 ms
26/05/01 05:16:08 INFO MemoryStore: Block broadcast_10 stored as values in memory (estimated size 317.1 KiB, free 126.9 MiB)
26/05/01 05:16:08 INFO MemoryStore: Block broadcast_10_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.8 MiB)
26/05/01 05:16:08 INFO BlockManagerInfo: Added broadcast_10_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:16:08 INFO SparkContext: Created broadcast 10 from rdd at Instrumentation.scala:62
26/05/01 05:16:08 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:09 INFO Instrumentation: [3ebd16f5] training: numPartitions=1 storageLevel=StorageLevel(1 replicas)
26/05/01 05:16:09 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:09 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:09 INFO CodeGenerator: Code generated in 102.647491 ms
26/05/01 05:16:09 INFO MemoryStore: Block broadcast_11 stored as values in memory (estimated size 317.1 KiB, free 126.5 MiB)
26/05/01 05:16:09 INFO MemoryStore: Block broadcast_11_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.5 MiB)
26/05/01 05:16:09 INFO BlockManagerInfo: Added broadcast_11_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.1 MiB)
26/05/01 05:16:09 INFO SparkContext: Created broadcast 11 from take at DatasetUtils.scala:193
26/05/01 05:16:09 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:09 INFO DAGScheduler: Registering RDD 34 (take at DatasetUtils.scala:193) as input to shuffle 2
26/05/01 05:16:09 INFO DAGScheduler: Got map stage job 6 (take at DatasetUtils.scala:193) with 1 output partitions
26/05/01 05:16:09 INFO DAGScheduler: Final stage: ShuffleMapStage 8 (take at DatasetUtils.scala:193)
26/05/01 05:16:09 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:16:09 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:09 INFO DAGScheduler: Submitting ShuffleMapStage 8 (MapPartitionsRDD[34] at take at DatasetUtils.scala:193), which has no missing parents
26/05/01 05:16:09 INFO MemoryStore: Block broadcast_12 stored as values in memory (estimated size 62.3 KiB, free 126.4 MiB)
26/05/01 05:16:09 INFO MemoryStore: Block broadcast_12_piece0 stored as bytes in memory (estimated size 25.4 KiB, free 126.4 MiB)
26/05/01 05:16:09 INFO BlockManagerInfo: Added broadcast_12_piece0 in memory on master-node:35479 (size: 25.4 KiB, free: 127.1 MiB)
26/05/01 05:16:09 INFO SparkContext: Created broadcast 12 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:09 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 8 (MapPartitionsRDD[34] at take at DatasetUtils.scala:193) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:09 INFO YarnScheduler: Adding task set 8.0 with 1 tasks resource profile 0
26/05/01 05:16:09 INFO TaskSetManager: Starting task 0.0 in stage 8.0 (TID 6) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:10 INFO BlockManagerInfo: Added broadcast_12_piece0 in memory on worker-node-1:34163 (size: 25.4 KiB, free: 413.9 MiB)
26/05/01 05:16:11 INFO BlockManagerInfo: Added broadcast_11_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:12 INFO TaskSetManager: Finished task 0.0 in stage 8.0 (TID 6) in 2616 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:12 INFO YarnScheduler: Removed TaskSet 8.0, whose tasks have all completed, from pool
26/05/01 05:16:12 INFO DAGScheduler: ShuffleMapStage 8 (take at DatasetUtils.scala:193) finished in 2.646 s
26/05/01 05:16:12 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:12 INFO DAGScheduler: running: Set()
26/05/01 05:16:12 INFO DAGScheduler: waiting: Set()
26/05/01 05:16:12 INFO DAGScheduler: failed: Set()
26/05/01 05:16:12 INFO CodeGenerator: Code generated in 78.934982 ms
26/05/01 05:16:12 INFO BlockManagerInfo: Removed broadcast_12_piece0 on master-node:35479 in memory (size: 25.4 KiB, free: 127.1 MiB)
26/05/01 05:16:12 INFO SparkContext: Starting job: take at DatasetUtils.scala:193
26/05/01 05:16:12 INFO DAGScheduler: Got job 7 (take at DatasetUtils.scala:193) with 1 output partitions
26/05/01 05:16:12 INFO DAGScheduler: Final stage: ResultStage 10 (take at DatasetUtils.scala:193)
26/05/01 05:16:12 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 9)
26/05/01 05:16:12 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:12 INFO DAGScheduler: Submitting ResultStage 10 (MapPartitionsRDD[37] at take at DatasetUtils.scala:193), which has no missing parents
26/05/01 05:16:12 INFO MemoryStore: Block broadcast_13 stored as values in memory (estimated size 13.3 KiB, free 126.5 MiB)
26/05/01 05:16:12 INFO MemoryStore: Block broadcast_13_piece0 stored as bytes in memory (estimated size 6.2 KiB, free 126.4 MiB)
26/05/01 05:16:12 INFO BlockManagerInfo: Added broadcast_13_piece0 in memory on master-node:35479 (size: 6.2 KiB, free: 127.1 MiB)
26/05/01 05:16:12 INFO SparkContext: Created broadcast 13 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:12 INFO BlockManagerInfo: Removed broadcast_12_piece0 on worker-node-1:34163 in memory (size: 25.4 KiB, free: 413.9 MiB)
26/05/01 05:16:12 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 10 (MapPartitionsRDD[37] at take at DatasetUtils.scala:193) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:12 INFO YarnScheduler: Adding task set 10.0 with 1 tasks resource profile 0
26/05/01 05:16:12 INFO TaskSetManager: Starting task 0.0 in stage 10.0 (TID 7) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9518 bytes)
26/05/01 05:16:13 INFO BlockManagerInfo: Added broadcast_13_piece0 in memory on worker-node-1:34163 (size: 6.2 KiB, free: 413.9 MiB)
26/05/01 05:16:13 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 2 to 164.92.103.148:51604
26/05/01 05:16:13 INFO TaskSetManager: Finished task 0.0 in stage 10.0 (TID 7) in 698 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:13 INFO DAGScheduler: ResultStage 10 (take at DatasetUtils.scala:193) finished in 0.750 s
26/05/01 05:16:13 INFO DAGScheduler: Job 7 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:13 INFO YarnScheduler: Removed TaskSet 10.0, whose tasks have all completed, from pool
26/05/01 05:16:13 INFO YarnScheduler: Killing all running tasks in stage 10: Stage finished
26/05/01 05:16:13 INFO DAGScheduler: Job 7 finished: take at DatasetUtils.scala:193, took 0.785139 s
26/05/01 05:16:13 INFO CodeGenerator: Code generated in 42.242533 ms
26/05/01 05:16:13 INFO DatasetUtils: org.apache.spark.ml.util.DatasetUtils$ inferred 2 classes for labelCol=label since numClasses was not specified in the column metadata.
26/05/01 05:16:13 INFO BlockManagerInfo: Removed broadcast_13_piece0 on master-node:35479 in memory (size: 6.2 KiB, free: 127.1 MiB)
26/05/01 05:16:13 INFO BlockManagerInfo: Removed broadcast_13_piece0 on worker-node-1:34163 in memory (size: 6.2 KiB, free: 413.9 MiB)
26/05/01 05:16:14 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:14 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:14 INFO CodeGenerator: Code generated in 217.56775 ms
26/05/01 05:16:14 INFO MemoryStore: Block broadcast_14 stored as values in memory (estimated size 317.1 KiB, free 126.2 MiB)
26/05/01 05:16:14 INFO MemoryStore: Block broadcast_14_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.1 MiB)
26/05/01 05:16:14 INFO BlockManagerInfo: Added broadcast_14_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:14 INFO SparkContext: Created broadcast 14 from rdd at RandomForestClassifier.scala:155
26/05/01 05:16:14 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:14 INFO Instrumentation: [3ebd16f5] {"labelCol":"label","featuresCol":"features","numTrees":10,"maxDepth":5}
26/05/01 05:16:14 INFO SparkContext: Starting job: take at DecisionTreeMetadata.scala:119
26/05/01 05:16:14 INFO DAGScheduler: Got job 8 (take at DecisionTreeMetadata.scala:119) with 1 output partitions
26/05/01 05:16:14 INFO DAGScheduler: Final stage: ResultStage 11 (take at DecisionTreeMetadata.scala:119)
26/05/01 05:16:14 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:16:14 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:14 INFO DAGScheduler: Submitting ResultStage 11 (MapPartitionsRDD[46] at map at DecisionTreeMetadata.scala:119), which has no missing parents
26/05/01 05:16:14 INFO MemoryStore: Block broadcast_15 stored as values in memory (estimated size 100.0 KiB, free 126.0 MiB)
26/05/01 05:16:14 INFO MemoryStore: Block broadcast_15_piece0 stored as bytes in memory (estimated size 39.1 KiB, free 126.0 MiB)
26/05/01 05:16:14 INFO BlockManagerInfo: Added broadcast_15_piece0 in memory on master-node:35479 (size: 39.1 KiB, free: 127.0 MiB)
26/05/01 05:16:14 INFO SparkContext: Created broadcast 15 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:14 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 11 (MapPartitionsRDD[46] at map at DecisionTreeMetadata.scala:119) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:14 INFO YarnScheduler: Adding task set 11.0 with 1 tasks resource profile 0
26/05/01 05:16:14 INFO TaskSetManager: Starting task 0.0 in stage 11.0 (TID 8) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10135 bytes)
26/05/01 05:16:15 INFO BlockManagerInfo: Added broadcast_15_piece0 in memory on worker-node-1:34163 (size: 39.1 KiB, free: 413.8 MiB)
26/05/01 05:16:16 INFO BlockManagerInfo: Added broadcast_14_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:17 INFO TaskSetManager: Finished task 0.0 in stage 11.0 (TID 8) in 2989 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:17 INFO YarnScheduler: Removed TaskSet 11.0, whose tasks have all completed, from pool
26/05/01 05:16:17 INFO DAGScheduler: ResultStage 11 (take at DecisionTreeMetadata.scala:119) finished in 3.021 s
26/05/01 05:16:17 INFO DAGScheduler: Job 8 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:17 INFO YarnScheduler: Killing all running tasks in stage 11: Stage finished
26/05/01 05:16:17 INFO DAGScheduler: Job 8 finished: take at DecisionTreeMetadata.scala:119, took 3.031425 s
26/05/01 05:16:17 INFO SparkContext: Starting job: aggregate at DecisionTreeMetadata.scala:125
26/05/01 05:16:17 INFO DAGScheduler: Got job 9 (aggregate at DecisionTreeMetadata.scala:125) with 1 output partitions
26/05/01 05:16:17 INFO DAGScheduler: Final stage: ResultStage 12 (aggregate at DecisionTreeMetadata.scala:125)
26/05/01 05:16:17 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:16:17 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:17 INFO DAGScheduler: Submitting ResultStage 12 (MapPartitionsRDD[45] at retag at RandomForest.scala:274), which has no missing parents
26/05/01 05:16:17 INFO MemoryStore: Block broadcast_16 stored as values in memory (estimated size 100.0 KiB, free 125.9 MiB)
26/05/01 05:16:17 INFO MemoryStore: Block broadcast_16_piece0 stored as bytes in memory (estimated size 39.3 KiB, free 125.8 MiB)
26/05/01 05:16:17 INFO BlockManagerInfo: Added broadcast_16_piece0 in memory on master-node:35479 (size: 39.3 KiB, free: 127.0 MiB)
26/05/01 05:16:17 INFO SparkContext: Created broadcast 16 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:17 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 12 (MapPartitionsRDD[45] at retag at RandomForest.scala:274) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:17 INFO YarnScheduler: Adding task set 12.0 with 1 tasks resource profile 0
26/05/01 05:16:17 INFO TaskSetManager: Starting task 0.0 in stage 12.0 (TID 9) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10135 bytes)
26/05/01 05:16:17 INFO BlockManagerInfo: Removed broadcast_15_piece0 on master-node:35479 in memory (size: 39.1 KiB, free: 127.0 MiB)
26/05/01 05:16:17 INFO BlockManagerInfo: Removed broadcast_15_piece0 on worker-node-1:34163 in memory (size: 39.1 KiB, free: 413.8 MiB)
26/05/01 05:16:18 INFO BlockManagerInfo: Added broadcast_16_piece0 in memory on worker-node-1:34163 (size: 39.3 KiB, free: 413.8 MiB)
26/05/01 05:16:19 INFO TaskSetManager: Finished task 0.0 in stage 12.0 (TID 9) in 1629 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:19 INFO YarnScheduler: Removed TaskSet 12.0, whose tasks have all completed, from pool
26/05/01 05:16:19 INFO DAGScheduler: ResultStage 12 (aggregate at DecisionTreeMetadata.scala:125) finished in 1.681 s
26/05/01 05:16:19 INFO DAGScheduler: Job 9 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:19 INFO YarnScheduler: Killing all running tasks in stage 12: Stage finished
26/05/01 05:16:19 INFO DAGScheduler: Job 9 finished: aggregate at DecisionTreeMetadata.scala:125, took 1.689377 s
26/05/01 05:16:19 INFO SparkContext: Starting job: collectAsMap at RandomForest.scala:1054
26/05/01 05:16:19 INFO DAGScheduler: Registering RDD 48 (flatMap at RandomForest.scala:1039) as input to shuffle 3
26/05/01 05:16:19 INFO DAGScheduler: Got job 10 (collectAsMap at RandomForest.scala:1054) with 1 output partitions
26/05/01 05:16:19 INFO DAGScheduler: Final stage: ResultStage 14 (collectAsMap at RandomForest.scala:1054)
26/05/01 05:16:19 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 13)
26/05/01 05:16:19 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 13)
26/05/01 05:16:19 INFO DAGScheduler: Submitting ShuffleMapStage 13 (MapPartitionsRDD[48] at flatMap at RandomForest.scala:1039), which has no missing parents
26/05/01 05:16:19 INFO MemoryStore: Block broadcast_17 stored as values in memory (estimated size 103.0 KiB, free 125.9 MiB)
26/05/01 05:16:19 INFO BlockManagerInfo: Removed broadcast_16_piece0 on master-node:35479 in memory (size: 39.3 KiB, free: 127.0 MiB)
26/05/01 05:16:19 INFO MemoryStore: Block broadcast_17_piece0 stored as bytes in memory (estimated size 40.3 KiB, free 126.0 MiB)
26/05/01 05:16:19 INFO BlockManagerInfo: Added broadcast_17_piece0 in memory on master-node:35479 (size: 40.3 KiB, free: 127.0 MiB)
26/05/01 05:16:19 INFO SparkContext: Created broadcast 17 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:19 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 13 (MapPartitionsRDD[48] at flatMap at RandomForest.scala:1039) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:19 INFO YarnScheduler: Adding task set 13.0 with 1 tasks resource profile 0
26/05/01 05:16:19 INFO TaskSetManager: Starting task 0.0 in stage 13.0 (TID 10) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:19 INFO BlockManagerInfo: Removed broadcast_16_piece0 on worker-node-1:34163 in memory (size: 39.3 KiB, free: 413.8 MiB)
26/05/01 05:16:20 INFO BlockManagerInfo: Added broadcast_17_piece0 in memory on worker-node-1:34163 (size: 40.3 KiB, free: 413.8 MiB)
26/05/01 05:16:21 INFO TaskSetManager: Finished task 0.0 in stage 13.0 (TID 10) in 1508 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:21 INFO YarnScheduler: Removed TaskSet 13.0, whose tasks have all completed, from pool
26/05/01 05:16:21 INFO DAGScheduler: ShuffleMapStage 13 (flatMap at RandomForest.scala:1039) finished in 1.568 s
26/05/01 05:16:21 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:21 INFO DAGScheduler: running: Set()
26/05/01 05:16:21 INFO DAGScheduler: waiting: Set(ResultStage 14)
26/05/01 05:16:21 INFO DAGScheduler: failed: Set()
26/05/01 05:16:21 INFO DAGScheduler: Submitting ResultStage 14 (MapPartitionsRDD[50] at map at RandomForest.scala:1054), which has no missing parents
26/05/01 05:16:21 INFO MemoryStore: Block broadcast_18 stored as values in memory (estimated size 8.9 KiB, free 126.0 MiB)
26/05/01 05:16:21 INFO MemoryStore: Block broadcast_18_piece0 stored as bytes in memory (estimated size 4.3 KiB, free 125.9 MiB)
26/05/01 05:16:21 INFO BlockManagerInfo: Added broadcast_18_piece0 in memory on master-node:35479 (size: 4.3 KiB, free: 127.0 MiB)
26/05/01 05:16:21 INFO SparkContext: Created broadcast 18 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:21 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 14 (MapPartitionsRDD[50] at map at RandomForest.scala:1054) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:21 INFO YarnScheduler: Adding task set 14.0 with 1 tasks resource profile 0
26/05/01 05:16:21 INFO TaskSetManager: Starting task 0.0 in stage 14.0 (TID 11) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:21 INFO BlockManagerInfo: Removed broadcast_11_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:21 INFO BlockManagerInfo: Removed broadcast_11_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:21 INFO BlockManagerInfo: Added broadcast_18_piece0 in memory on worker-node-1:34163 (size: 4.3 KiB, free: 413.8 MiB)
26/05/01 05:16:21 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 3 to 164.92.103.148:51604
26/05/01 05:16:21 INFO TaskSetManager: Finished task 0.0 in stage 14.0 (TID 11) in 600 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:21 INFO DAGScheduler: ResultStage 14 (collectAsMap at RandomForest.scala:1054) finished in 0.659 s
26/05/01 05:16:21 INFO DAGScheduler: Job 10 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:21 INFO YarnScheduler: Removed TaskSet 14.0, whose tasks have all completed, from pool
26/05/01 05:16:21 INFO YarnScheduler: Killing all running tasks in stage 14: Stage finished
26/05/01 05:16:21 INFO DAGScheduler: Job 10 finished: collectAsMap at RandomForest.scala:1054, took 2.259440 s
26/05/01 05:16:21 INFO MemoryStore: Block broadcast_19 stored as values in memory (estimated size 784.0 B, free 126.3 MiB)
26/05/01 05:16:21 INFO MemoryStore: Block broadcast_19_piece0 stored as bytes in memory (estimated size 219.0 B, free 126.3 MiB)
26/05/01 05:16:21 INFO BlockManagerInfo: Added broadcast_19_piece0 in memory on master-node:35479 (size: 219.0 B, free: 127.0 MiB)
26/05/01 05:16:21 INFO SparkContext: Created broadcast 19 from broadcast at RandomForest.scala:293
26/05/01 05:16:21 INFO Instrumentation: [3ebd16f5] {"numFeatures":3}
26/05/01 05:16:21 INFO Instrumentation: [3ebd16f5] {"numClasses":2}
26/05/01 05:16:21 INFO Instrumentation: [3ebd16f5] {"numExamples":8079}
26/05/01 05:16:21 INFO Instrumentation: [3ebd16f5] {"sumOfWeights":8079.0}
26/05/01 05:16:21 INFO MemoryStore: Block broadcast_20 stored as values in memory (estimated size 1080.0 B, free 126.3 MiB)
26/05/01 05:16:21 INFO MemoryStore: Block broadcast_20_piece0 stored as bytes in memory (estimated size 146.0 B, free 126.3 MiB)
26/05/01 05:16:21 INFO BlockManagerInfo: Added broadcast_20_piece0 in memory on master-node:35479 (size: 146.0 B, free: 127.0 MiB)
26/05/01 05:16:21 INFO SparkContext: Created broadcast 20 from broadcast at RandomForest.scala:622
26/05/01 05:16:22 INFO SparkContext: Starting job: collectAsMap at RandomForest.scala:663
26/05/01 05:16:22 INFO DAGScheduler: Registering RDD 53 (mapPartitions at RandomForest.scala:644) as input to shuffle 4
26/05/01 05:16:22 INFO DAGScheduler: Got job 11 (collectAsMap at RandomForest.scala:663) with 1 output partitions
26/05/01 05:16:22 INFO DAGScheduler: Final stage: ResultStage 16 (collectAsMap at RandomForest.scala:663)
26/05/01 05:16:22 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 15)
26/05/01 05:16:22 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 15)
26/05/01 05:16:22 INFO DAGScheduler: Submitting ShuffleMapStage 15 (MapPartitionsRDD[53] at mapPartitions at RandomForest.scala:644), which has no missing parents
26/05/01 05:16:22 INFO MemoryStore: Block broadcast_21 stored as values in memory (estimated size 105.2 KiB, free 126.2 MiB)
26/05/01 05:16:22 INFO MemoryStore: Block broadcast_21_piece0 stored as bytes in memory (estimated size 41.7 KiB, free 126.2 MiB)
26/05/01 05:16:22 INFO BlockManagerInfo: Added broadcast_21_piece0 in memory on master-node:35479 (size: 41.7 KiB, free: 127.0 MiB)
26/05/01 05:16:22 INFO SparkContext: Created broadcast 21 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:22 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 15 (MapPartitionsRDD[53] at mapPartitions at RandomForest.scala:644) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:22 INFO YarnScheduler: Adding task set 15.0 with 1 tasks resource profile 0
26/05/01 05:16:22 INFO TaskSetManager: Starting task 0.0 in stage 15.0 (TID 12) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:22 INFO BlockManagerInfo: Removed broadcast_18_piece0 on master-node:35479 in memory (size: 4.3 KiB, free: 127.0 MiB)
26/05/01 05:16:22 INFO BlockManagerInfo: Removed broadcast_18_piece0 on worker-node-1:34163 in memory (size: 4.3 KiB, free: 413.8 MiB)
26/05/01 05:16:22 INFO BlockManagerInfo: Removed broadcast_17_piece0 on master-node:35479 in memory (size: 40.3 KiB, free: 127.0 MiB)
26/05/01 05:16:22 INFO BlockManagerInfo: Removed broadcast_17_piece0 on worker-node-1:34163 in memory (size: 40.3 KiB, free: 413.9 MiB)
26/05/01 05:16:22 INFO BlockManagerInfo: Added broadcast_21_piece0 in memory on worker-node-1:34163 (size: 41.7 KiB, free: 413.8 MiB)
26/05/01 05:16:24 INFO BlockManagerInfo: Added rdd_52_0 in memory on worker-node-1:34163 (size: 1219.1 KiB, free: 412.6 MiB)
26/05/01 05:16:24 INFO BlockManagerInfo: Added broadcast_20_piece0 in memory on worker-node-1:34163 (size: 146.0 B, free: 412.6 MiB)
26/05/01 05:16:24 INFO BlockManagerInfo: Added broadcast_19_piece0 in memory on worker-node-1:34163 (size: 219.0 B, free: 412.6 MiB)
26/05/01 05:16:24 INFO TaskSetManager: Finished task 0.0 in stage 15.0 (TID 12) in 2769 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:24 INFO YarnScheduler: Removed TaskSet 15.0, whose tasks have all completed, from pool
26/05/01 05:16:24 INFO DAGScheduler: ShuffleMapStage 15 (mapPartitions at RandomForest.scala:644) finished in 2.813 s
26/05/01 05:16:24 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:24 INFO DAGScheduler: running: Set()
26/05/01 05:16:24 INFO DAGScheduler: waiting: Set(ResultStage 16)
26/05/01 05:16:24 INFO DAGScheduler: failed: Set()
26/05/01 05:16:24 INFO DAGScheduler: Submitting ResultStage 16 (MapPartitionsRDD[55] at map at RandomForest.scala:663), which has no missing parents
26/05/01 05:16:24 INFO MemoryStore: Block broadcast_22 stored as values in memory (estimated size 7.7 KiB, free 126.3 MiB)
26/05/01 05:16:24 INFO MemoryStore: Block broadcast_22_piece0 stored as bytes in memory (estimated size 4.1 KiB, free 126.3 MiB)
26/05/01 05:16:24 INFO BlockManagerInfo: Added broadcast_22_piece0 in memory on master-node:35479 (size: 4.1 KiB, free: 127.0 MiB)
26/05/01 05:16:24 INFO SparkContext: Created broadcast 22 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:24 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 16 (MapPartitionsRDD[55] at map at RandomForest.scala:663) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:24 INFO YarnScheduler: Adding task set 16.0 with 1 tasks resource profile 0
26/05/01 05:16:24 INFO TaskSetManager: Starting task 0.0 in stage 16.0 (TID 13) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:25 INFO BlockManagerInfo: Added broadcast_22_piece0 in memory on worker-node-1:34163 (size: 4.1 KiB, free: 412.6 MiB)
26/05/01 05:16:25 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 4 to 164.92.103.148:51604
26/05/01 05:16:25 INFO BlockManagerInfo: Removed broadcast_21_piece0 on master-node:35479 in memory (size: 41.7 KiB, free: 127.1 MiB)
26/05/01 05:16:25 INFO TaskSetManager: Finished task 0.0 in stage 16.0 (TID 13) in 801 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:25 INFO YarnScheduler: Removed TaskSet 16.0, whose tasks have all completed, from pool
26/05/01 05:16:25 INFO DAGScheduler: ResultStage 16 (collectAsMap at RandomForest.scala:663) finished in 0.817 s
26/05/01 05:16:25 INFO DAGScheduler: Job 11 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:25 INFO YarnScheduler: Killing all running tasks in stage 16: Stage finished
26/05/01 05:16:25 INFO DAGScheduler: Job 11 finished: collectAsMap at RandomForest.scala:663, took 3.652582 s
26/05/01 05:16:25 INFO TorrentBroadcast: Destroying Broadcast(20) (from destroy at RandomForest.scala:674)
26/05/01 05:16:25 INFO BlockManagerInfo: Removed broadcast_20_piece0 on master-node:35479 in memory (size: 146.0 B, free: 127.1 MiB)
26/05/01 05:16:25 INFO MemoryStore: Block broadcast_23 stored as values in memory (estimated size 2.0 KiB, free 126.5 MiB)
26/05/01 05:16:25 INFO MemoryStore: Block broadcast_23_piece0 stored as bytes in memory (estimated size 211.0 B, free 126.5 MiB)
26/05/01 05:16:25 INFO BlockManagerInfo: Added broadcast_23_piece0 in memory on master-node:35479 (size: 211.0 B, free: 127.1 MiB)
26/05/01 05:16:25 INFO SparkContext: Created broadcast 23 from broadcast at RandomForest.scala:622
26/05/01 05:16:25 INFO BlockManagerInfo: Removed broadcast_21_piece0 on worker-node-1:34163 in memory (size: 41.7 KiB, free: 412.7 MiB)
26/05/01 05:16:25 INFO BlockManagerInfo: Removed broadcast_20_piece0 on worker-node-1:34163 in memory (size: 146.0 B, free: 412.7 MiB)
26/05/01 05:16:25 INFO SparkContext: Starting job: collectAsMap at RandomForest.scala:663
26/05/01 05:16:25 INFO DAGScheduler: Registering RDD 56 (mapPartitions at RandomForest.scala:644) as input to shuffle 5
26/05/01 05:16:25 INFO DAGScheduler: Got job 12 (collectAsMap at RandomForest.scala:663) with 1 output partitions
26/05/01 05:16:25 INFO DAGScheduler: Final stage: ResultStage 18 (collectAsMap at RandomForest.scala:663)
26/05/01 05:16:25 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 17)
26/05/01 05:16:25 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 17)
26/05/01 05:16:25 INFO DAGScheduler: Submitting ShuffleMapStage 17 (MapPartitionsRDD[56] at mapPartitions at RandomForest.scala:644), which has no missing parents
26/05/01 05:16:25 INFO MemoryStore: Block broadcast_24 stored as values in memory (estimated size 110.7 KiB, free 126.3 MiB)
26/05/01 05:16:25 INFO MemoryStore: Block broadcast_24_piece0 stored as bytes in memory (estimated size 43.9 KiB, free 126.3 MiB)
26/05/01 05:16:25 INFO BlockManagerInfo: Added broadcast_24_piece0 in memory on master-node:35479 (size: 43.9 KiB, free: 127.0 MiB)
26/05/01 05:16:25 INFO SparkContext: Created broadcast 24 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:25 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 17 (MapPartitionsRDD[56] at mapPartitions at RandomForest.scala:644) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:25 INFO YarnScheduler: Adding task set 17.0 with 1 tasks resource profile 0
26/05/01 05:16:25 INFO TaskSetManager: Starting task 0.0 in stage 17.0 (TID 14) (worker-node-1, executor 1, partition 0, PROCESS_LOCAL, 10124 bytes)
26/05/01 05:16:26 INFO BlockManagerInfo: Added broadcast_24_piece0 in memory on worker-node-1:34163 (size: 43.9 KiB, free: 412.6 MiB)
26/05/01 05:16:26 INFO BlockManagerInfo: Added broadcast_23_piece0 in memory on worker-node-1:34163 (size: 211.0 B, free: 412.6 MiB)
26/05/01 05:16:26 INFO TaskSetManager: Finished task 0.0 in stage 17.0 (TID 14) in 1002 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:26 INFO YarnScheduler: Removed TaskSet 17.0, whose tasks have all completed, from pool
26/05/01 05:16:26 INFO DAGScheduler: ShuffleMapStage 17 (mapPartitions at RandomForest.scala:644) finished in 1.025 s
26/05/01 05:16:26 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:26 INFO DAGScheduler: running: Set()
26/05/01 05:16:26 INFO DAGScheduler: waiting: Set(ResultStage 18)
26/05/01 05:16:26 INFO DAGScheduler: failed: Set()
26/05/01 05:16:26 INFO DAGScheduler: Submitting ResultStage 18 (MapPartitionsRDD[58] at map at RandomForest.scala:663), which has no missing parents
26/05/01 05:16:26 INFO MemoryStore: Block broadcast_25 stored as values in memory (estimated size 9.6 KiB, free 126.3 MiB)
26/05/01 05:16:26 INFO MemoryStore: Block broadcast_25_piece0 stored as bytes in memory (estimated size 4.9 KiB, free 126.3 MiB)
26/05/01 05:16:26 INFO BlockManagerInfo: Added broadcast_25_piece0 in memory on master-node:35479 (size: 4.9 KiB, free: 127.0 MiB)
26/05/01 05:16:26 INFO SparkContext: Created broadcast 25 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:26 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 18 (MapPartitionsRDD[58] at map at RandomForest.scala:663) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:26 INFO YarnScheduler: Adding task set 18.0 with 1 tasks resource profile 0
26/05/01 05:16:26 INFO TaskSetManager: Starting task 0.0 in stage 18.0 (TID 15) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:27 INFO BlockManagerInfo: Added broadcast_25_piece0 in memory on worker-node-1:34163 (size: 4.9 KiB, free: 412.6 MiB)
26/05/01 05:16:27 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 5 to 164.92.103.148:51604
26/05/01 05:16:27 INFO TaskSetManager: Finished task 0.0 in stage 18.0 (TID 15) in 563 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:27 INFO DAGScheduler: ResultStage 18 (collectAsMap at RandomForest.scala:663) finished in 0.579 s
26/05/01 05:16:27 INFO DAGScheduler: Job 12 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:27 INFO YarnScheduler: Removed TaskSet 18.0, whose tasks have all completed, from pool
26/05/01 05:16:27 INFO YarnScheduler: Killing all running tasks in stage 18: Stage finished
26/05/01 05:16:27 INFO DAGScheduler: Job 12 finished: collectAsMap at RandomForest.scala:663, took 1.626827 s
26/05/01 05:16:27 INFO TorrentBroadcast: Destroying Broadcast(23) (from destroy at RandomForest.scala:674)
26/05/01 05:16:27 INFO MemoryStore: Block broadcast_26 stored as values in memory (estimated size 4.5 KiB, free 126.3 MiB)
26/05/01 05:16:27 INFO BlockManagerInfo: Removed broadcast_23_piece0 on master-node:35479 in memory (size: 211.0 B, free: 127.0 MiB)
26/05/01 05:16:27 INFO MemoryStore: Block broadcast_26_piece0 stored as bytes in memory (estimated size 320.0 B, free 126.3 MiB)
26/05/01 05:16:27 INFO BlockManagerInfo: Added broadcast_26_piece0 in memory on master-node:35479 (size: 320.0 B, free: 127.0 MiB)
26/05/01 05:16:27 INFO SparkContext: Created broadcast 26 from broadcast at RandomForest.scala:622
26/05/01 05:16:27 INFO BlockManagerInfo: Removed broadcast_23_piece0 on worker-node-1:34163 in memory (size: 211.0 B, free: 412.6 MiB)
26/05/01 05:16:27 INFO BlockManagerInfo: Removed broadcast_22_piece0 on master-node:35479 in memory (size: 4.1 KiB, free: 127.0 MiB)
26/05/01 05:16:27 INFO SparkContext: Starting job: collectAsMap at RandomForest.scala:663
26/05/01 05:16:27 INFO DAGScheduler: Registering RDD 59 (mapPartitions at RandomForest.scala:644) as input to shuffle 6
26/05/01 05:16:27 INFO DAGScheduler: Got job 13 (collectAsMap at RandomForest.scala:663) with 1 output partitions
26/05/01 05:16:27 INFO DAGScheduler: Final stage: ResultStage 20 (collectAsMap at RandomForest.scala:663)
26/05/01 05:16:27 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 19)
26/05/01 05:16:27 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 19)
26/05/01 05:16:27 INFO DAGScheduler: Submitting ShuffleMapStage 19 (MapPartitionsRDD[59] at mapPartitions at RandomForest.scala:644), which has no missing parents
26/05/01 05:16:27 INFO BlockManagerInfo: Removed broadcast_22_piece0 on worker-node-1:34163 in memory (size: 4.1 KiB, free: 412.6 MiB)
26/05/01 05:16:27 INFO MemoryStore: Block broadcast_27 stored as values in memory (estimated size 119.3 KiB, free 126.2 MiB)
26/05/01 05:16:27 INFO MemoryStore: Block broadcast_27_piece0 stored as bytes in memory (estimated size 46.6 KiB, free 126.1 MiB)
26/05/01 05:16:27 INFO BlockManagerInfo: Added broadcast_27_piece0 in memory on master-node:35479 (size: 46.6 KiB, free: 127.0 MiB)
26/05/01 05:16:27 INFO SparkContext: Created broadcast 27 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:27 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 19 (MapPartitionsRDD[59] at mapPartitions at RandomForest.scala:644) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:27 INFO YarnScheduler: Adding task set 19.0 with 1 tasks resource profile 0
26/05/01 05:16:27 INFO TaskSetManager: Starting task 0.0 in stage 19.0 (TID 16) (worker-node-1, executor 1, partition 0, PROCESS_LOCAL, 10124 bytes)
26/05/01 05:16:27 INFO BlockManagerInfo: Removed broadcast_24_piece0 on master-node:35479 in memory (size: 43.9 KiB, free: 127.0 MiB)
26/05/01 05:16:27 INFO BlockManagerInfo: Removed broadcast_24_piece0 on worker-node-1:34163 in memory (size: 43.9 KiB, free: 412.7 MiB)
26/05/01 05:16:27 INFO BlockManagerInfo: Removed broadcast_25_piece0 on master-node:35479 in memory (size: 4.9 KiB, free: 127.0 MiB)
26/05/01 05:16:28 INFO BlockManagerInfo: Removed broadcast_25_piece0 on worker-node-1:34163 in memory (size: 4.9 KiB, free: 412.7 MiB)
26/05/01 05:16:28 INFO BlockManagerInfo: Added broadcast_27_piece0 in memory on worker-node-1:34163 (size: 46.6 KiB, free: 412.6 MiB)
26/05/01 05:16:28 INFO BlockManagerInfo: Added broadcast_26_piece0 in memory on worker-node-1:34163 (size: 320.0 B, free: 412.6 MiB)
26/05/01 05:16:28 INFO TaskSetManager: Finished task 0.0 in stage 19.0 (TID 16) in 1075 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:28 INFO YarnScheduler: Removed TaskSet 19.0, whose tasks have all completed, from pool
26/05/01 05:16:28 INFO DAGScheduler: ShuffleMapStage 19 (mapPartitions at RandomForest.scala:644) finished in 1.107 s
26/05/01 05:16:28 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:28 INFO DAGScheduler: running: Set()
26/05/01 05:16:28 INFO DAGScheduler: waiting: Set(ResultStage 20)
26/05/01 05:16:28 INFO DAGScheduler: failed: Set()
26/05/01 05:16:28 INFO DAGScheduler: Submitting ResultStage 20 (MapPartitionsRDD[61] at map at RandomForest.scala:663), which has no missing parents
26/05/01 05:16:28 INFO MemoryStore: Block broadcast_28 stored as values in memory (estimated size 11.4 KiB, free 126.3 MiB)
26/05/01 05:16:28 INFO MemoryStore: Block broadcast_28_piece0 stored as bytes in memory (estimated size 5.5 KiB, free 126.3 MiB)
26/05/01 05:16:28 INFO BlockManagerInfo: Added broadcast_28_piece0 in memory on master-node:35479 (size: 5.5 KiB, free: 127.0 MiB)
26/05/01 05:16:28 INFO SparkContext: Created broadcast 28 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:28 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 20 (MapPartitionsRDD[61] at map at RandomForest.scala:663) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:28 INFO YarnScheduler: Adding task set 20.0 with 1 tasks resource profile 0
26/05/01 05:16:28 INFO TaskSetManager: Starting task 0.0 in stage 20.0 (TID 17) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:28 INFO BlockManagerInfo: Added broadcast_28_piece0 in memory on worker-node-1:34163 (size: 5.5 KiB, free: 412.6 MiB)
26/05/01 05:16:29 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 6 to 164.92.103.148:51604
26/05/01 05:16:29 INFO TaskSetManager: Finished task 0.0 in stage 20.0 (TID 17) in 569 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:29 INFO DAGScheduler: ResultStage 20 (collectAsMap at RandomForest.scala:663) finished in 0.583 s
26/05/01 05:16:29 INFO DAGScheduler: Job 13 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:29 INFO YarnScheduler: Removed TaskSet 20.0, whose tasks have all completed, from pool
26/05/01 05:16:29 INFO YarnScheduler: Killing all running tasks in stage 20: Stage finished
26/05/01 05:16:29 INFO DAGScheduler: Job 13 finished: collectAsMap at RandomForest.scala:663, took 1.717636 s
26/05/01 05:16:29 INFO TorrentBroadcast: Destroying Broadcast(26) (from destroy at RandomForest.scala:674)
26/05/01 05:16:29 INFO MemoryStore: Block broadcast_29 stored as values in memory (estimated size 8.7 KiB, free 126.3 MiB)
26/05/01 05:16:29 INFO BlockManagerInfo: Removed broadcast_26_piece0 on master-node:35479 in memory (size: 320.0 B, free: 127.0 MiB)
26/05/01 05:16:29 INFO MemoryStore: Block broadcast_29_piece0 stored as bytes in memory (estimated size 646.0 B, free 126.3 MiB)
26/05/01 05:16:29 INFO BlockManagerInfo: Added broadcast_29_piece0 in memory on master-node:35479 (size: 646.0 B, free: 127.0 MiB)
26/05/01 05:16:29 INFO SparkContext: Created broadcast 29 from broadcast at RandomForest.scala:622
26/05/01 05:16:29 INFO BlockManagerInfo: Removed broadcast_26_piece0 on worker-node-1:34163 in memory (size: 320.0 B, free: 412.6 MiB)
26/05/01 05:16:29 INFO SparkContext: Starting job: collectAsMap at RandomForest.scala:663
26/05/01 05:16:29 INFO DAGScheduler: Registering RDD 62 (mapPartitions at RandomForest.scala:644) as input to shuffle 7
26/05/01 05:16:29 INFO DAGScheduler: Got job 14 (collectAsMap at RandomForest.scala:663) with 1 output partitions
26/05/01 05:16:29 INFO DAGScheduler: Final stage: ResultStage 22 (collectAsMap at RandomForest.scala:663)
26/05/01 05:16:29 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 21)
26/05/01 05:16:29 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 21)
26/05/01 05:16:29 INFO DAGScheduler: Submitting ShuffleMapStage 21 (MapPartitionsRDD[62] at mapPartitions at RandomForest.scala:644), which has no missing parents
26/05/01 05:16:29 INFO MemoryStore: Block broadcast_30 stored as values in memory (estimated size 135.3 KiB, free 126.1 MiB)
26/05/01 05:16:29 INFO MemoryStore: Block broadcast_30_piece0 stored as bytes in memory (estimated size 52.5 KiB, free 126.1 MiB)
26/05/01 05:16:29 INFO BlockManagerInfo: Added broadcast_30_piece0 in memory on master-node:35479 (size: 52.5 KiB, free: 127.0 MiB)
26/05/01 05:16:29 INFO SparkContext: Created broadcast 30 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:29 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 21 (MapPartitionsRDD[62] at mapPartitions at RandomForest.scala:644) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:29 INFO YarnScheduler: Adding task set 21.0 with 1 tasks resource profile 0
26/05/01 05:16:29 INFO TaskSetManager: Starting task 0.0 in stage 21.0 (TID 18) (worker-node-1, executor 1, partition 0, PROCESS_LOCAL, 10124 bytes)
26/05/01 05:16:29 INFO BlockManagerInfo: Removed broadcast_27_piece0 on master-node:35479 in memory (size: 46.6 KiB, free: 127.0 MiB)
26/05/01 05:16:29 INFO BlockManagerInfo: Removed broadcast_27_piece0 on worker-node-1:34163 in memory (size: 46.6 KiB, free: 412.7 MiB)
26/05/01 05:16:29 INFO BlockManagerInfo: Removed broadcast_28_piece0 on master-node:35479 in memory (size: 5.5 KiB, free: 127.0 MiB)
26/05/01 05:16:29 INFO BlockManagerInfo: Removed broadcast_28_piece0 on worker-node-1:34163 in memory (size: 5.5 KiB, free: 412.7 MiB)
26/05/01 05:16:29 INFO BlockManagerInfo: Added broadcast_30_piece0 in memory on worker-node-1:34163 (size: 52.5 KiB, free: 412.6 MiB)
26/05/01 05:16:30 INFO BlockManagerInfo: Added broadcast_29_piece0 in memory on worker-node-1:34163 (size: 646.0 B, free: 412.6 MiB)
26/05/01 05:16:30 INFO TaskSetManager: Finished task 0.0 in stage 21.0 (TID 18) in 1067 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:30 INFO YarnScheduler: Removed TaskSet 21.0, whose tasks have all completed, from pool
26/05/01 05:16:30 INFO DAGScheduler: ShuffleMapStage 21 (mapPartitions at RandomForest.scala:644) finished in 1.097 s
26/05/01 05:16:30 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:30 INFO DAGScheduler: running: Set()
26/05/01 05:16:30 INFO DAGScheduler: waiting: Set(ResultStage 22)
26/05/01 05:16:30 INFO DAGScheduler: failed: Set()
26/05/01 05:16:30 INFO DAGScheduler: Submitting ResultStage 22 (MapPartitionsRDD[64] at map at RandomForest.scala:663), which has no missing parents
26/05/01 05:16:30 INFO MemoryStore: Block broadcast_31 stored as values in memory (estimated size 14.7 KiB, free 126.3 MiB)
26/05/01 05:16:30 INFO MemoryStore: Block broadcast_31_piece0 stored as bytes in memory (estimated size 6.5 KiB, free 126.3 MiB)
26/05/01 05:16:30 INFO BlockManagerInfo: Added broadcast_31_piece0 in memory on master-node:35479 (size: 6.5 KiB, free: 127.0 MiB)
26/05/01 05:16:30 INFO SparkContext: Created broadcast 31 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:30 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 22 (MapPartitionsRDD[64] at map at RandomForest.scala:663) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:30 INFO YarnScheduler: Adding task set 22.0 with 1 tasks resource profile 0
26/05/01 05:16:30 INFO TaskSetManager: Starting task 0.0 in stage 22.0 (TID 19) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:30 INFO BlockManagerInfo: Added broadcast_31_piece0 in memory on worker-node-1:34163 (size: 6.5 KiB, free: 412.6 MiB)
26/05/01 05:16:30 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 7 to 164.92.103.148:51604
26/05/01 05:16:31 INFO TaskSetManager: Finished task 0.0 in stage 22.0 (TID 19) in 765 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:31 INFO DAGScheduler: ResultStage 22 (collectAsMap at RandomForest.scala:663) finished in 0.839 s
26/05/01 05:16:31 INFO DAGScheduler: Job 14 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:31 INFO YarnScheduler: Removed TaskSet 22.0, whose tasks have all completed, from pool
26/05/01 05:16:31 INFO YarnScheduler: Killing all running tasks in stage 22: Stage finished
26/05/01 05:16:31 INFO DAGScheduler: Job 14 finished: collectAsMap at RandomForest.scala:663, took 1.959952 s
26/05/01 05:16:31 INFO TorrentBroadcast: Destroying Broadcast(29) (from destroy at RandomForest.scala:674)
26/05/01 05:16:31 INFO BlockManagerInfo: Removed broadcast_29_piece0 on master-node:35479 in memory (size: 646.0 B, free: 127.0 MiB)
26/05/01 05:16:31 INFO MemoryStore: Block broadcast_32 stored as values in memory (estimated size 14.6 KiB, free 126.2 MiB)
26/05/01 05:16:31 INFO MemoryStore: Block broadcast_32_piece0 stored as bytes in memory (estimated size 970.0 B, free 126.2 MiB)
26/05/01 05:16:31 INFO BlockManagerInfo: Added broadcast_32_piece0 in memory on master-node:35479 (size: 970.0 B, free: 127.0 MiB)
26/05/01 05:16:31 INFO BlockManagerInfo: Removed broadcast_30_piece0 on master-node:35479 in memory (size: 52.5 KiB, free: 127.1 MiB)
26/05/01 05:16:31 INFO SparkContext: Created broadcast 32 from broadcast at RandomForest.scala:622
26/05/01 05:16:31 INFO BlockManagerInfo: Removed broadcast_29_piece0 on worker-node-1:34163 in memory (size: 646.0 B, free: 412.6 MiB)
26/05/01 05:16:31 INFO SparkContext: Starting job: collectAsMap at RandomForest.scala:663
26/05/01 05:16:31 INFO DAGScheduler: Registering RDD 65 (mapPartitions at RandomForest.scala:644) as input to shuffle 8
26/05/01 05:16:31 INFO DAGScheduler: Got job 15 (collectAsMap at RandomForest.scala:663) with 1 output partitions
26/05/01 05:16:31 INFO DAGScheduler: Final stage: ResultStage 24 (collectAsMap at RandomForest.scala:663)
26/05/01 05:16:31 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 23)
26/05/01 05:16:31 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 23)
26/05/01 05:16:31 INFO DAGScheduler: Submitting ShuffleMapStage 23 (MapPartitionsRDD[65] at mapPartitions at RandomForest.scala:644), which has no missing parents
26/05/01 05:16:31 INFO MemoryStore: Block broadcast_33 stored as values in memory (estimated size 159.5 KiB, free 126.3 MiB)
26/05/01 05:16:31 INFO BlockManagerInfo: Removed broadcast_30_piece0 on worker-node-1:34163 in memory (size: 52.5 KiB, free: 412.7 MiB)
26/05/01 05:16:31 INFO MemoryStore: Block broadcast_33_piece0 stored as bytes in memory (estimated size 60.5 KiB, free 126.2 MiB)
26/05/01 05:16:31 INFO BlockManagerInfo: Added broadcast_33_piece0 in memory on master-node:35479 (size: 60.5 KiB, free: 127.0 MiB)
26/05/01 05:16:31 INFO SparkContext: Created broadcast 33 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:31 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 23 (MapPartitionsRDD[65] at mapPartitions at RandomForest.scala:644) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:31 INFO YarnScheduler: Adding task set 23.0 with 1 tasks resource profile 0
26/05/01 05:16:31 INFO TaskSetManager: Starting task 0.0 in stage 23.0 (TID 20) (worker-node-1, executor 1, partition 0, PROCESS_LOCAL, 10124 bytes)
26/05/01 05:16:31 INFO BlockManagerInfo: Removed broadcast_31_piece0 on master-node:35479 in memory (size: 6.5 KiB, free: 127.0 MiB)
26/05/01 05:16:31 INFO BlockManagerInfo: Removed broadcast_31_piece0 on worker-node-1:34163 in memory (size: 6.5 KiB, free: 412.7 MiB)
26/05/01 05:16:31 INFO BlockManagerInfo: Added broadcast_33_piece0 in memory on worker-node-1:34163 (size: 60.5 KiB, free: 412.6 MiB)
26/05/01 05:16:32 INFO BlockManagerInfo: Added broadcast_32_piece0 in memory on worker-node-1:34163 (size: 970.0 B, free: 412.6 MiB)
26/05/01 05:16:32 INFO TaskSetManager: Finished task 0.0 in stage 23.0 (TID 20) in 1054 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:32 INFO YarnScheduler: Removed TaskSet 23.0, whose tasks have all completed, from pool
26/05/01 05:16:32 INFO DAGScheduler: ShuffleMapStage 23 (mapPartitions at RandomForest.scala:644) finished in 1.092 s
26/05/01 05:16:32 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:32 INFO DAGScheduler: running: Set()
26/05/01 05:16:32 INFO DAGScheduler: waiting: Set(ResultStage 24)
26/05/01 05:16:32 INFO DAGScheduler: failed: Set()
26/05/01 05:16:32 INFO DAGScheduler: Submitting ResultStage 24 (MapPartitionsRDD[67] at map at RandomForest.scala:663), which has no missing parents
26/05/01 05:16:32 INFO MemoryStore: Block broadcast_34 stored as values in memory (estimated size 19.5 KiB, free 126.2 MiB)
26/05/01 05:16:32 INFO MemoryStore: Block broadcast_34_piece0 stored as bytes in memory (estimated size 7.9 KiB, free 126.2 MiB)
26/05/01 05:16:32 INFO BlockManagerInfo: Added broadcast_34_piece0 in memory on master-node:35479 (size: 7.9 KiB, free: 127.0 MiB)
26/05/01 05:16:32 INFO SparkContext: Created broadcast 34 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:32 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 24 (MapPartitionsRDD[67] at map at RandomForest.scala:663) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:32 INFO YarnScheduler: Adding task set 24.0 with 1 tasks resource profile 0
26/05/01 05:16:32 INFO TaskSetManager: Starting task 0.0 in stage 24.0 (TID 21) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:32 INFO BlockManagerInfo: Added broadcast_34_piece0 in memory on worker-node-1:34163 (size: 7.9 KiB, free: 412.6 MiB)
26/05/01 05:16:32 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 8 to 164.92.103.148:51604
26/05/01 05:16:33 INFO TaskSetManager: Finished task 0.0 in stage 24.0 (TID 21) in 668 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:33 INFO YarnScheduler: Removed TaskSet 24.0, whose tasks have all completed, from pool
26/05/01 05:16:33 INFO DAGScheduler: ResultStage 24 (collectAsMap at RandomForest.scala:663) finished in 0.702 s
26/05/01 05:16:33 INFO DAGScheduler: Job 15 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:33 INFO YarnScheduler: Killing all running tasks in stage 24: Stage finished
26/05/01 05:16:33 INFO DAGScheduler: Job 15 finished: collectAsMap at RandomForest.scala:663, took 1.816464 s
26/05/01 05:16:33 INFO TorrentBroadcast: Destroying Broadcast(32) (from destroy at RandomForest.scala:674)
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_32_piece0 on master-node:35479 in memory (size: 970.0 B, free: 127.0 MiB)
26/05/01 05:16:33 INFO RandomForest: Internal timing for DecisionTree:
26/05/01 05:16:33 INFO RandomForest:   init: 0.004986382
  total: 11.293755771
  findBestSplits: 11.259558715
  chooseSplits: 11.222725821
26/05/01 05:16:33 INFO MapPartitionsRDD: Removing RDD 52 from persistence list
26/05/01 05:16:33 INFO BlockManager: Removing RDD 52
26/05/01 05:16:33 INFO TorrentBroadcast: Destroying Broadcast(19) (from destroy at RandomForest.scala:305)
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_19_piece0 on master-node:35479 in memory (size: 219.0 B, free: 127.0 MiB)
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_32_piece0 on worker-node-1:34163 in memory (size: 970.0 B, free: 413.8 MiB)
26/05/01 05:16:33 INFO Instrumentation: [3ebd16f5] {"numClasses":2}
26/05/01 05:16:33 INFO Instrumentation: [3ebd16f5] {"numFeatures":3}
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_19_piece0 on worker-node-1:34163 in memory (size: 219.0 B, free: 413.8 MiB)
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_33_piece0 on master-node:35479 in memory (size: 60.5 KiB, free: 127.1 MiB)
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_33_piece0 on worker-node-1:34163 in memory (size: 60.5 KiB, free: 413.9 MiB)
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_34_piece0 on master-node:35479 in memory (size: 7.9 KiB, free: 127.1 MiB)
26/05/01 05:16:33 INFO BlockManagerInfo: Removed broadcast_34_piece0 on worker-node-1:34163 in memory (size: 7.9 KiB, free: 413.9 MiB)
26/05/01 05:16:34 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:34 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:34 INFO CodeGenerator: Code generated in 69.315854 ms
26/05/01 05:16:34 INFO MemoryStore: Block broadcast_35 stored as values in memory (estimated size 317.1 KiB, free 126.2 MiB)
26/05/01 05:16:34 INFO MemoryStore: Block broadcast_35_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 126.1 MiB)
26/05/01 05:16:34 INFO BlockManagerInfo: Added broadcast_35_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:34 INFO SparkContext: Created broadcast 35 from rdd at ClassificationSummary.scala:58
26/05/01 05:16:34 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:34 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:34 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:34 INFO CodeGenerator: Code generated in 78.294238 ms
26/05/01 05:16:34 INFO MemoryStore: Block broadcast_36 stored as values in memory (estimated size 317.1 KiB, free 125.8 MiB)
26/05/01 05:16:34 INFO MemoryStore: Block broadcast_36_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 125.7 MiB)
26/05/01 05:16:34 INFO BlockManagerInfo: Added broadcast_36_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:34 INFO SparkContext: Created broadcast 36 from rdd at ClassificationSummary.scala:191
26/05/01 05:16:34 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:34 INFO Instrumentation: [3ebd16f5] training finished
Training Time: 35.14866781234741 seconds
26/05/01 05:16:35 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:35 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:35 INFO CodeGenerator: Code generated in 104.745745 ms
26/05/01 05:16:35 INFO MemoryStore: Block broadcast_37 stored as values in memory (estimated size 317.1 KiB, free 125.4 MiB)
26/05/01 05:16:35 INFO MemoryStore: Block broadcast_37_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 125.4 MiB)
26/05/01 05:16:35 INFO BlockManagerInfo: Added broadcast_37_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 126.9 MiB)
26/05/01 05:16:35 INFO SparkContext: Created broadcast 37 from rdd at BinaryClassificationEvaluator.scala:131
26/05/01 05:16:35 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:35 INFO SparkContext: Starting job: count at BinaryClassificationMetrics.scala:200
26/05/01 05:16:35 INFO DAGScheduler: Registering RDD 90 (map at BinaryClassificationMetrics.scala:51) as input to shuffle 10
26/05/01 05:16:35 INFO DAGScheduler: Registering RDD 91 (combineByKey at BinaryClassificationMetrics.scala:191) as input to shuffle 9
26/05/01 05:16:35 INFO DAGScheduler: Got job 16 (count at BinaryClassificationMetrics.scala:200) with 1 output partitions
26/05/01 05:16:35 INFO DAGScheduler: Final stage: ResultStage 27 (count at BinaryClassificationMetrics.scala:200)
26/05/01 05:16:35 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 26)
26/05/01 05:16:35 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 26)
26/05/01 05:16:35 INFO DAGScheduler: Submitting ShuffleMapStage 25 (MapPartitionsRDD[90] at map at BinaryClassificationMetrics.scala:51), which has no missing parents
26/05/01 05:16:35 INFO MemoryStore: Block broadcast_38 stored as values in memory (estimated size 146.7 KiB, free 125.2 MiB)
26/05/01 05:16:35 INFO MemoryStore: Block broadcast_38_piece0 stored as bytes in memory (estimated size 59.4 KiB, free 125.2 MiB)
26/05/01 05:16:35 INFO BlockManagerInfo: Added broadcast_38_piece0 in memory on master-node:35479 (size: 59.4 KiB, free: 126.9 MiB)
26/05/01 05:16:35 INFO SparkContext: Created broadcast 38 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:35 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 25 (MapPartitionsRDD[90] at map at BinaryClassificationMetrics.scala:51) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:35 INFO YarnScheduler: Adding task set 25.0 with 1 tasks resource profile 0
26/05/01 05:16:35 INFO TaskSetManager: Starting task 0.0 in stage 25.0 (TID 22) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:35 INFO BlockManagerInfo: Added broadcast_38_piece0 in memory on worker-node-1:34163 (size: 59.4 KiB, free: 413.8 MiB)
26/05/01 05:16:36 INFO BlockManagerInfo: Added broadcast_37_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:37 INFO TaskSetManager: Finished task 0.0 in stage 25.0 (TID 22) in 2149 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:37 INFO DAGScheduler: ShuffleMapStage 25 (map at BinaryClassificationMetrics.scala:51) finished in 2.174 s
26/05/01 05:16:37 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:37 INFO DAGScheduler: running: Set()
26/05/01 05:16:37 INFO DAGScheduler: waiting: Set(ResultStage 27, ShuffleMapStage 26)
26/05/01 05:16:37 INFO DAGScheduler: failed: Set()
26/05/01 05:16:37 INFO DAGScheduler: Submitting ShuffleMapStage 26 (ShuffledRDD[91] at combineByKey at BinaryClassificationMetrics.scala:191), which has no missing parents
26/05/01 05:16:37 INFO YarnScheduler: Removed TaskSet 25.0, whose tasks have all completed, from pool
26/05/01 05:16:37 INFO MemoryStore: Block broadcast_39 stored as values in memory (estimated size 5.7 KiB, free 125.2 MiB)
26/05/01 05:16:37 INFO MemoryStore: Block broadcast_39_piece0 stored as bytes in memory (estimated size 3.2 KiB, free 125.2 MiB)
26/05/01 05:16:37 INFO BlockManagerInfo: Added broadcast_39_piece0 in memory on master-node:35479 (size: 3.2 KiB, free: 126.9 MiB)
26/05/01 05:16:37 INFO SparkContext: Created broadcast 39 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:37 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 26 (ShuffledRDD[91] at combineByKey at BinaryClassificationMetrics.scala:191) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:37 INFO YarnScheduler: Adding task set 26.0 with 1 tasks resource profile 0
26/05/01 05:16:37 INFO TaskSetManager: Starting task 0.0 in stage 26.0 (TID 23) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9325 bytes)
26/05/01 05:16:37 INFO BlockManager: Removing RDD 52
26/05/01 05:16:37 INFO BlockManagerInfo: Removed broadcast_10_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 126.9 MiB)
26/05/01 05:16:37 INFO BlockManagerInfo: Added broadcast_39_piece0 in memory on worker-node-1:34163 (size: 3.2 KiB, free: 413.8 MiB)
26/05/01 05:16:37 INFO BlockManagerInfo: Removed broadcast_14_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:38 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 10 to 164.92.103.148:51604
26/05/01 05:16:38 INFO BlockManagerInfo: Removed broadcast_14_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:38 INFO TaskSetManager: Finished task 0.0 in stage 26.0 (TID 23) in 529 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:38 INFO YarnScheduler: Removed TaskSet 26.0, whose tasks have all completed, from pool
26/05/01 05:16:38 INFO DAGScheduler: ShuffleMapStage 26 (combineByKey at BinaryClassificationMetrics.scala:191) finished in 0.569 s
26/05/01 05:16:38 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:38 INFO DAGScheduler: running: Set()
26/05/01 05:16:38 INFO DAGScheduler: waiting: Set(ResultStage 27)
26/05/01 05:16:38 INFO DAGScheduler: failed: Set()
26/05/01 05:16:38 INFO DAGScheduler: Submitting ResultStage 27 (ShuffledRDD[92] at sortByKey at BinaryClassificationMetrics.scala:192), which has no missing parents
26/05/01 05:16:38 INFO MemoryStore: Block broadcast_40 stored as values in memory (estimated size 5.3 KiB, free 125.9 MiB)
26/05/01 05:16:38 INFO MemoryStore: Block broadcast_40_piece0 stored as bytes in memory (estimated size 3.1 KiB, free 125.9 MiB)
26/05/01 05:16:38 INFO BlockManagerInfo: Added broadcast_40_piece0 in memory on master-node:35479 (size: 3.1 KiB, free: 127.0 MiB)
26/05/01 05:16:38 INFO SparkContext: Created broadcast 40 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:38 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 27 (ShuffledRDD[92] at sortByKey at BinaryClassificationMetrics.scala:192) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:38 INFO YarnScheduler: Adding task set 27.0 with 1 tasks resource profile 0
26/05/01 05:16:38 INFO TaskSetManager: Starting task 0.0 in stage 27.0 (TID 24) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:38 INFO BlockManagerInfo: Added broadcast_40_piece0 in memory on worker-node-1:34163 (size: 3.1 KiB, free: 413.8 MiB)
26/05/01 05:16:38 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 9 to 164.92.103.148:51604
26/05/01 05:16:38 INFO TaskSetManager: Finished task 0.0 in stage 27.0 (TID 24) in 552 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:38 INFO YarnScheduler: Removed TaskSet 27.0, whose tasks have all completed, from pool
26/05/01 05:16:38 INFO DAGScheduler: ResultStage 27 (count at BinaryClassificationMetrics.scala:200) finished in 0.568 s
26/05/01 05:16:38 INFO DAGScheduler: Job 16 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:38 INFO YarnScheduler: Killing all running tasks in stage 27: Stage finished
26/05/01 05:16:38 INFO DAGScheduler: Job 16 finished: count at BinaryClassificationMetrics.scala:200, took 3.331392 s
26/05/01 05:16:38 INFO BinaryClassificationMetrics: Curve is too small (135) for 1000 bins to be useful
26/05/01 05:16:38 INFO SparkContext: Starting job: collect at BinaryClassificationMetrics.scala:240
26/05/01 05:16:38 INFO DAGScheduler: Got job 17 (collect at BinaryClassificationMetrics.scala:240) with 1 output partitions
26/05/01 05:16:38 INFO DAGScheduler: Final stage: ResultStage 30 (collect at BinaryClassificationMetrics.scala:240)
26/05/01 05:16:38 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 29)
26/05/01 05:16:38 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:38 INFO DAGScheduler: Submitting ResultStage 30 (MapPartitionsRDD[94] at mapPartitions at BinaryClassificationMetrics.scala:240), which has no missing parents
26/05/01 05:16:38 INFO MemoryStore: Block broadcast_41 stored as values in memory (estimated size 6.7 KiB, free 125.9 MiB)
26/05/01 05:16:38 INFO MemoryStore: Block broadcast_41_piece0 stored as bytes in memory (estimated size 3.7 KiB, free 125.9 MiB)
26/05/01 05:16:38 INFO BlockManagerInfo: Added broadcast_41_piece0 in memory on master-node:35479 (size: 3.7 KiB, free: 127.0 MiB)
26/05/01 05:16:38 INFO SparkContext: Created broadcast 41 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:38 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 30 (MapPartitionsRDD[94] at mapPartitions at BinaryClassificationMetrics.scala:240) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:38 INFO YarnScheduler: Adding task set 30.0 with 1 tasks resource profile 0
26/05/01 05:16:38 INFO TaskSetManager: Starting task 0.0 in stage 30.0 (TID 25) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:39 INFO BlockManagerInfo: Added broadcast_41_piece0 in memory on worker-node-1:34163 (size: 3.7 KiB, free: 413.8 MiB)
26/05/01 05:16:39 INFO TaskSetManager: Finished task 0.0 in stage 30.0 (TID 25) in 424 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:39 INFO YarnScheduler: Removed TaskSet 30.0, whose tasks have all completed, from pool
26/05/01 05:16:39 INFO DAGScheduler: ResultStage 30 (collect at BinaryClassificationMetrics.scala:240) finished in 0.435 s
26/05/01 05:16:39 INFO DAGScheduler: Job 17 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:39 INFO YarnScheduler: Killing all running tasks in stage 30: Stage finished
26/05/01 05:16:39 INFO DAGScheduler: Job 17 finished: collect at BinaryClassificationMetrics.scala:240, took 0.442714 s
26/05/01 05:16:39 INFO BinaryClassificationMetrics: Total counts: {numPos: 239.0, numNeg: 1682.0}
26/05/01 05:16:39 INFO SparkContext: Starting job: collect at AreaUnderCurve.scala:44
26/05/01 05:16:39 INFO DAGScheduler: Got job 18 (collect at AreaUnderCurve.scala:44) with 1 output partitions
26/05/01 05:16:39 INFO DAGScheduler: Final stage: ResultStage 33 (collect at AreaUnderCurve.scala:44)
26/05/01 05:16:39 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 32)
26/05/01 05:16:39 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:39 INFO DAGScheduler: Submitting ResultStage 33 (MapPartitionsRDD[99] at mapPartitions at AreaUnderCurve.scala:44), which has no missing parents
26/05/01 05:16:39 INFO MemoryStore: Block broadcast_42 stored as values in memory (estimated size 8.3 KiB, free 125.9 MiB)
26/05/01 05:16:39 INFO MemoryStore: Block broadcast_42_piece0 stored as bytes in memory (estimated size 4.1 KiB, free 125.9 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Added broadcast_42_piece0 in memory on master-node:35479 (size: 4.1 KiB, free: 127.0 MiB)
26/05/01 05:16:39 INFO SparkContext: Created broadcast 42 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:39 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 33 (MapPartitionsRDD[99] at mapPartitions at AreaUnderCurve.scala:44) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:39 INFO YarnScheduler: Adding task set 33.0 with 1 tasks resource profile 0
26/05/01 05:16:39 INFO TaskSetManager: Starting task 0.0 in stage 33.0 (TID 26) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_39_piece0 on master-node:35479 in memory (size: 3.2 KiB, free: 127.0 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_39_piece0 on worker-node-1:34163 in memory (size: 3.2 KiB, free: 413.8 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_40_piece0 on master-node:35479 in memory (size: 3.1 KiB, free: 127.0 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_40_piece0 on worker-node-1:34163 in memory (size: 3.1 KiB, free: 413.8 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Added broadcast_42_piece0 in memory on worker-node-1:34163 (size: 4.1 KiB, free: 413.8 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_41_piece0 on master-node:35479 in memory (size: 3.7 KiB, free: 127.0 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_41_piece0 on worker-node-1:34163 in memory (size: 3.7 KiB, free: 413.8 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_38_piece0 on master-node:35479 in memory (size: 59.4 KiB, free: 127.0 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Added rdd_95_0 in memory on worker-node-1:34163 (size: 11.1 KiB, free: 413.8 MiB)
26/05/01 05:16:39 INFO BlockManagerInfo: Removed broadcast_38_piece0 on worker-node-1:34163 in memory (size: 59.4 KiB, free: 413.9 MiB)
26/05/01 05:16:39 INFO TaskSetManager: Finished task 0.0 in stage 33.0 (TID 26) in 636 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:39 INFO YarnScheduler: Removed TaskSet 33.0, whose tasks have all completed, from pool
26/05/01 05:16:39 INFO DAGScheduler: ResultStage 33 (collect at AreaUnderCurve.scala:44) finished in 0.648 s
26/05/01 05:16:39 INFO DAGScheduler: Job 18 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:39 INFO YarnScheduler: Killing all running tasks in stage 33: Stage finished
26/05/01 05:16:39 INFO DAGScheduler: Job 18 finished: collect at AreaUnderCurve.scala:44, took 0.659595 s
26/05/01 05:16:39 INFO MapPartitionsRDD: Removing RDD 95 from persistence list
26/05/01 05:16:39 INFO BlockManager: Removing RDD 95
26/05/01 05:16:39 INFO BlockManager: Removing RDD 95
26/05/01 05:16:39 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:39 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:40 INFO BlockManagerInfo: Removed broadcast_42_piece0 on master-node:35479 in memory (size: 4.1 KiB, free: 127.0 MiB)
26/05/01 05:16:40 INFO CodeGenerator: Code generated in 68.954415 ms
26/05/01 05:16:40 INFO MemoryStore: Block broadcast_43 stored as values in memory (estimated size 317.1 KiB, free 125.8 MiB)
26/05/01 05:16:40 INFO BlockManagerInfo: Removed broadcast_42_piece0 on worker-node-1:34163 in memory (size: 4.1 KiB, free: 413.9 MiB)
26/05/01 05:16:40 INFO MemoryStore: Block broadcast_43_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 125.7 MiB)
26/05/01 05:16:40 INFO BlockManagerInfo: Added broadcast_43_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:40 INFO SparkContext: Created broadcast 43 from rdd at MulticlassClassificationEvaluator.scala:191
26/05/01 05:16:40 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:40 INFO SparkContext: Starting job: collectAsMap at MulticlassMetrics.scala:61
26/05/01 05:16:40 INFO DAGScheduler: Registering RDD 107 (map at MulticlassMetrics.scala:52) as input to shuffle 11
26/05/01 05:16:40 INFO DAGScheduler: Got job 19 (collectAsMap at MulticlassMetrics.scala:61) with 1 output partitions
26/05/01 05:16:40 INFO DAGScheduler: Final stage: ResultStage 35 (collectAsMap at MulticlassMetrics.scala:61)
26/05/01 05:16:40 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 34)
26/05/01 05:16:40 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 34)
26/05/01 05:16:40 INFO DAGScheduler: Submitting ShuffleMapStage 34 (MapPartitionsRDD[107] at map at MulticlassMetrics.scala:52), which has no missing parents
26/05/01 05:16:40 INFO MemoryStore: Block broadcast_44 stored as values in memory (estimated size 158.5 KiB, free 125.6 MiB)
26/05/01 05:16:40 INFO MemoryStore: Block broadcast_44_piece0 stored as bytes in memory (estimated size 62.5 KiB, free 125.5 MiB)
26/05/01 05:16:40 INFO BlockManagerInfo: Added broadcast_44_piece0 in memory on master-node:35479 (size: 62.5 KiB, free: 126.9 MiB)
26/05/01 05:16:40 INFO SparkContext: Created broadcast 44 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:40 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 34 (MapPartitionsRDD[107] at map at MulticlassMetrics.scala:52) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:40 INFO YarnScheduler: Adding task set 34.0 with 1 tasks resource profile 0
26/05/01 05:16:40 INFO TaskSetManager: Starting task 0.0 in stage 34.0 (TID 27) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:40 INFO BlockManagerInfo: Added broadcast_44_piece0 in memory on worker-node-1:34163 (size: 62.5 KiB, free: 413.8 MiB)
26/05/01 05:16:41 INFO BlockManagerInfo: Added broadcast_43_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:41 INFO TaskSetManager: Finished task 0.0 in stage 34.0 (TID 27) in 1688 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:41 INFO YarnScheduler: Removed TaskSet 34.0, whose tasks have all completed, from pool
26/05/01 05:16:41 INFO DAGScheduler: ShuffleMapStage 34 (map at MulticlassMetrics.scala:52) finished in 1.710 s
26/05/01 05:16:41 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:41 INFO DAGScheduler: running: Set()
26/05/01 05:16:41 INFO DAGScheduler: waiting: Set(ResultStage 35)
26/05/01 05:16:41 INFO DAGScheduler: failed: Set()
26/05/01 05:16:41 INFO DAGScheduler: Submitting ResultStage 35 (ShuffledRDD[108] at reduceByKey at MulticlassMetrics.scala:61), which has no missing parents
26/05/01 05:16:41 INFO MemoryStore: Block broadcast_45 stored as values in memory (estimated size 5.3 KiB, free 125.5 MiB)
26/05/01 05:16:41 INFO MemoryStore: Block broadcast_45_piece0 stored as bytes in memory (estimated size 3.1 KiB, free 125.5 MiB)
26/05/01 05:16:41 INFO BlockManagerInfo: Added broadcast_45_piece0 in memory on master-node:35479 (size: 3.1 KiB, free: 126.9 MiB)
26/05/01 05:16:41 INFO SparkContext: Created broadcast 45 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:41 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 35 (ShuffledRDD[108] at reduceByKey at MulticlassMetrics.scala:61) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:41 INFO YarnScheduler: Adding task set 35.0 with 1 tasks resource profile 0
26/05/01 05:16:41 INFO TaskSetManager: Starting task 0.0 in stage 35.0 (TID 28) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:42 INFO BlockManagerInfo: Removed broadcast_37_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:42 INFO BlockManagerInfo: Removed broadcast_37_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:42 INFO BlockManagerInfo: Added broadcast_45_piece0 in memory on worker-node-1:34163 (size: 3.1 KiB, free: 413.8 MiB)
26/05/01 05:16:42 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 11 to 164.92.103.148:51604
26/05/01 05:16:42 INFO TaskSetManager: Finished task 0.0 in stage 35.0 (TID 28) in 462 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:42 INFO YarnScheduler: Removed TaskSet 35.0, whose tasks have all completed, from pool
26/05/01 05:16:42 INFO DAGScheduler: ResultStage 35 (collectAsMap at MulticlassMetrics.scala:61) finished in 0.487 s
26/05/01 05:16:42 INFO DAGScheduler: Job 19 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:42 INFO YarnScheduler: Killing all running tasks in stage 35: Stage finished
26/05/01 05:16:42 INFO DAGScheduler: Job 19 finished: collectAsMap at MulticlassMetrics.scala:61, took 2.208288 s
26/05/01 05:16:42 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:42 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:42 INFO MemoryStore: Block broadcast_46 stored as values in memory (estimated size 317.1 KiB, free 125.6 MiB)
26/05/01 05:16:42 INFO MemoryStore: Block broadcast_46_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 125.5 MiB)
26/05/01 05:16:42 INFO BlockManagerInfo: Added broadcast_46_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 126.9 MiB)
26/05/01 05:16:42 INFO SparkContext: Created broadcast 46 from rdd at MulticlassClassificationEvaluator.scala:191
26/05/01 05:16:42 INFO BlockManagerInfo: Removed broadcast_44_piece0 on master-node:35479 in memory (size: 62.5 KiB, free: 127.0 MiB)
26/05/01 05:16:42 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:42 INFO BlockManagerInfo: Removed broadcast_44_piece0 on worker-node-1:34163 in memory (size: 62.5 KiB, free: 413.9 MiB)
26/05/01 05:16:42 INFO SparkContext: Starting job: collectAsMap at MulticlassMetrics.scala:61
26/05/01 05:16:42 INFO DAGScheduler: Registering RDD 116 (map at MulticlassMetrics.scala:52) as input to shuffle 12
26/05/01 05:16:42 INFO DAGScheduler: Got job 20 (collectAsMap at MulticlassMetrics.scala:61) with 1 output partitions
26/05/01 05:16:42 INFO DAGScheduler: Final stage: ResultStage 37 (collectAsMap at MulticlassMetrics.scala:61)
26/05/01 05:16:42 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 36)
26/05/01 05:16:42 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 36)
26/05/01 05:16:42 INFO DAGScheduler: Submitting ShuffleMapStage 36 (MapPartitionsRDD[116] at map at MulticlassMetrics.scala:52), which has no missing parents
26/05/01 05:16:42 INFO MemoryStore: Block broadcast_47 stored as values in memory (estimated size 158.5 KiB, free 125.6 MiB)
26/05/01 05:16:42 INFO MemoryStore: Block broadcast_47_piece0 stored as bytes in memory (estimated size 62.5 KiB, free 125.5 MiB)
26/05/01 05:16:42 INFO BlockManagerInfo: Added broadcast_47_piece0 in memory on master-node:35479 (size: 62.5 KiB, free: 126.9 MiB)
26/05/01 05:16:42 INFO SparkContext: Created broadcast 47 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:42 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 36 (MapPartitionsRDD[116] at map at MulticlassMetrics.scala:52) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:42 INFO YarnScheduler: Adding task set 36.0 with 1 tasks resource profile 0
26/05/01 05:16:42 INFO TaskSetManager: Starting task 0.0 in stage 36.0 (TID 29) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:42 INFO BlockManagerInfo: Removed broadcast_45_piece0 on master-node:35479 in memory (size: 3.1 KiB, free: 126.9 MiB)
26/05/01 05:16:42 INFO BlockManagerInfo: Removed broadcast_45_piece0 on worker-node-1:34163 in memory (size: 3.1 KiB, free: 413.9 MiB)
26/05/01 05:16:42 INFO BlockManagerInfo: Removed broadcast_43_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:43 INFO BlockManagerInfo: Removed broadcast_43_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.9 MiB)
26/05/01 05:16:43 INFO BlockManagerInfo: Added broadcast_47_piece0 in memory on worker-node-1:34163 (size: 62.5 KiB, free: 413.9 MiB)
26/05/01 05:16:43 INFO BlockManagerInfo: Added broadcast_46_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:44 INFO TaskSetManager: Finished task 0.0 in stage 36.0 (TID 29) in 1395 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:44 INFO YarnScheduler: Removed TaskSet 36.0, whose tasks have all completed, from pool
26/05/01 05:16:44 INFO DAGScheduler: ShuffleMapStage 36 (map at MulticlassMetrics.scala:52) finished in 1.424 s
26/05/01 05:16:44 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:44 INFO DAGScheduler: running: Set()
26/05/01 05:16:44 INFO DAGScheduler: waiting: Set(ResultStage 37)
26/05/01 05:16:44 INFO DAGScheduler: failed: Set()
26/05/01 05:16:44 INFO DAGScheduler: Submitting ResultStage 37 (ShuffledRDD[117] at reduceByKey at MulticlassMetrics.scala:61), which has no missing parents
26/05/01 05:16:44 INFO MemoryStore: Block broadcast_48 stored as values in memory (estimated size 5.3 KiB, free 125.9 MiB)
26/05/01 05:16:44 INFO MemoryStore: Block broadcast_48_piece0 stored as bytes in memory (estimated size 3.1 KiB, free 125.9 MiB)
26/05/01 05:16:44 INFO BlockManagerInfo: Added broadcast_48_piece0 in memory on master-node:35479 (size: 3.1 KiB, free: 127.0 MiB)
26/05/01 05:16:44 INFO SparkContext: Created broadcast 48 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:44 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 37 (ShuffledRDD[117] at reduceByKey at MulticlassMetrics.scala:61) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:44 INFO YarnScheduler: Adding task set 37.0 with 1 tasks resource profile 0
26/05/01 05:16:44 INFO TaskSetManager: Starting task 0.0 in stage 37.0 (TID 30) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:44 INFO BlockManagerInfo: Added broadcast_48_piece0 in memory on worker-node-1:34163 (size: 3.1 KiB, free: 413.8 MiB)
26/05/01 05:16:44 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 12 to 164.92.103.148:51604
26/05/01 05:16:44 INFO TaskSetManager: Finished task 0.0 in stage 37.0 (TID 30) in 459 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:44 INFO YarnScheduler: Removed TaskSet 37.0, whose tasks have all completed, from pool
26/05/01 05:16:44 INFO DAGScheduler: ResultStage 37 (collectAsMap at MulticlassMetrics.scala:61) finished in 0.470 s
26/05/01 05:16:44 INFO DAGScheduler: Job 20 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:44 INFO YarnScheduler: Killing all running tasks in stage 37: Stage finished
26/05/01 05:16:44 INFO DAGScheduler: Job 20 finished: collectAsMap at MulticlassMetrics.scala:61, took 1.909954 s
26/05/01 05:16:44 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:44 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:44 INFO BlockManagerInfo: Removed broadcast_48_piece0 on master-node:35479 in memory (size: 3.1 KiB, free: 127.0 MiB)
26/05/01 05:16:44 INFO MemoryStore: Block broadcast_49 stored as values in memory (estimated size 317.1 KiB, free 125.6 MiB)
26/05/01 05:16:44 INFO MemoryStore: Block broadcast_49_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 125.5 MiB)
26/05/01 05:16:44 INFO BlockManagerInfo: Added broadcast_49_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 126.9 MiB)
26/05/01 05:16:44 INFO SparkContext: Created broadcast 49 from rdd at MulticlassClassificationEvaluator.scala:191
26/05/01 05:16:44 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:44 INFO BlockManagerInfo: Removed broadcast_48_piece0 on worker-node-1:34163 in memory (size: 3.1 KiB, free: 413.8 MiB)
26/05/01 05:16:44 INFO SparkContext: Starting job: collectAsMap at MulticlassMetrics.scala:61
26/05/01 05:16:44 INFO DAGScheduler: Registering RDD 125 (map at MulticlassMetrics.scala:52) as input to shuffle 13
26/05/01 05:16:44 INFO DAGScheduler: Got job 21 (collectAsMap at MulticlassMetrics.scala:61) with 1 output partitions
26/05/01 05:16:44 INFO DAGScheduler: Final stage: ResultStage 39 (collectAsMap at MulticlassMetrics.scala:61)
26/05/01 05:16:44 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 38)
26/05/01 05:16:44 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 38)
26/05/01 05:16:44 INFO DAGScheduler: Submitting ShuffleMapStage 38 (MapPartitionsRDD[125] at map at MulticlassMetrics.scala:52), which has no missing parents
26/05/01 05:16:44 INFO MemoryStore: Block broadcast_50 stored as values in memory (estimated size 158.5 KiB, free 125.4 MiB)
26/05/01 05:16:44 INFO MemoryStore: Block broadcast_50_piece0 stored as bytes in memory (estimated size 62.5 KiB, free 125.3 MiB)
26/05/01 05:16:44 INFO BlockManagerInfo: Added broadcast_50_piece0 in memory on master-node:35479 (size: 62.5 KiB, free: 126.9 MiB)
26/05/01 05:16:44 INFO SparkContext: Created broadcast 50 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:44 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 38 (MapPartitionsRDD[125] at map at MulticlassMetrics.scala:52) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:44 INFO YarnScheduler: Adding task set 38.0 with 1 tasks resource profile 0
26/05/01 05:16:44 INFO TaskSetManager: Starting task 0.0 in stage 38.0 (TID 31) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:44 INFO BlockManagerInfo: Removed broadcast_47_piece0 on master-node:35479 in memory (size: 62.5 KiB, free: 126.9 MiB)
26/05/01 05:16:45 INFO BlockManagerInfo: Removed broadcast_47_piece0 on worker-node-1:34163 in memory (size: 62.5 KiB, free: 413.9 MiB)
26/05/01 05:16:45 INFO BlockManagerInfo: Added broadcast_50_piece0 in memory on worker-node-1:34163 (size: 62.5 KiB, free: 413.8 MiB)
26/05/01 05:16:45 INFO BlockManagerInfo: Added broadcast_49_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:46 INFO TaskSetManager: Finished task 0.0 in stage 38.0 (TID 31) in 1373 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:46 INFO YarnScheduler: Removed TaskSet 38.0, whose tasks have all completed, from pool
26/05/01 05:16:46 INFO DAGScheduler: ShuffleMapStage 38 (map at MulticlassMetrics.scala:52) finished in 1.400 s
26/05/01 05:16:46 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:46 INFO DAGScheduler: running: Set()
26/05/01 05:16:46 INFO DAGScheduler: waiting: Set(ResultStage 39)
26/05/01 05:16:46 INFO DAGScheduler: failed: Set()
26/05/01 05:16:46 INFO DAGScheduler: Submitting ResultStage 39 (ShuffledRDD[126] at reduceByKey at MulticlassMetrics.scala:61), which has no missing parents
26/05/01 05:16:46 INFO MemoryStore: Block broadcast_51 stored as values in memory (estimated size 5.3 KiB, free 125.5 MiB)
26/05/01 05:16:46 INFO MemoryStore: Block broadcast_51_piece0 stored as bytes in memory (estimated size 3.1 KiB, free 125.5 MiB)
26/05/01 05:16:46 INFO BlockManagerInfo: Added broadcast_51_piece0 in memory on master-node:35479 (size: 3.1 KiB, free: 126.9 MiB)
26/05/01 05:16:46 INFO SparkContext: Created broadcast 51 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:46 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 39 (ShuffledRDD[126] at reduceByKey at MulticlassMetrics.scala:61) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:46 INFO YarnScheduler: Adding task set 39.0 with 1 tasks resource profile 0
26/05/01 05:16:46 INFO TaskSetManager: Starting task 0.0 in stage 39.0 (TID 32) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:46 INFO BlockManagerInfo: Added broadcast_51_piece0 in memory on worker-node-1:34163 (size: 3.1 KiB, free: 413.7 MiB)
26/05/01 05:16:46 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 13 to 164.92.103.148:51604
26/05/01 05:16:46 INFO TaskSetManager: Finished task 0.0 in stage 39.0 (TID 32) in 472 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:46 INFO YarnScheduler: Removed TaskSet 39.0, whose tasks have all completed, from pool
26/05/01 05:16:46 INFO DAGScheduler: ResultStage 39 (collectAsMap at MulticlassMetrics.scala:61) finished in 0.506 s
26/05/01 05:16:46 INFO DAGScheduler: Job 21 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:46 INFO YarnScheduler: Killing all running tasks in stage 39: Stage finished
26/05/01 05:16:46 INFO DAGScheduler: Job 21 finished: collectAsMap at MulticlassMetrics.scala:61, took 1.924650 s
26/05/01 05:16:46 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:46 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:46 INFO MemoryStore: Block broadcast_52 stored as values in memory (estimated size 317.1 KiB, free 125.2 MiB)
26/05/01 05:16:46 INFO MemoryStore: Block broadcast_52_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 125.1 MiB)
26/05/01 05:16:46 INFO BlockManagerInfo: Added broadcast_52_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 126.9 MiB)
26/05/01 05:16:46 INFO SparkContext: Created broadcast 52 from rdd at MulticlassClassificationEvaluator.scala:191
26/05/01 05:16:46 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:46 INFO BlockManagerInfo: Removed broadcast_51_piece0 on master-node:35479 in memory (size: 3.1 KiB, free: 126.9 MiB)
26/05/01 05:16:47 INFO BlockManagerInfo: Removed broadcast_51_piece0 on worker-node-1:34163 in memory (size: 3.1 KiB, free: 413.8 MiB)
26/05/01 05:16:47 INFO SparkContext: Starting job: collectAsMap at MulticlassMetrics.scala:61
26/05/01 05:16:47 INFO DAGScheduler: Registering RDD 134 (map at MulticlassMetrics.scala:52) as input to shuffle 14
26/05/01 05:16:47 INFO DAGScheduler: Got job 22 (collectAsMap at MulticlassMetrics.scala:61) with 1 output partitions
26/05/01 05:16:47 INFO DAGScheduler: Final stage: ResultStage 41 (collectAsMap at MulticlassMetrics.scala:61)
26/05/01 05:16:47 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 40)
26/05/01 05:16:47 INFO DAGScheduler: Missing parents: List(ShuffleMapStage 40)
26/05/01 05:16:47 INFO DAGScheduler: Submitting ShuffleMapStage 40 (MapPartitionsRDD[134] at map at MulticlassMetrics.scala:52), which has no missing parents
26/05/01 05:16:47 INFO MemoryStore: Block broadcast_53 stored as values in memory (estimated size 158.5 KiB, free 125.0 MiB)
26/05/01 05:16:47 INFO MemoryStore: Block broadcast_53_piece0 stored as bytes in memory (estimated size 62.5 KiB, free 124.9 MiB)
26/05/01 05:16:47 INFO BlockManagerInfo: Added broadcast_53_piece0 in memory on master-node:35479 (size: 62.5 KiB, free: 126.8 MiB)
26/05/01 05:16:47 INFO SparkContext: Created broadcast 53 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:47 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 40 (MapPartitionsRDD[134] at map at MulticlassMetrics.scala:52) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:47 INFO YarnScheduler: Adding task set 40.0 with 1 tasks resource profile 0
26/05/01 05:16:47 INFO TaskSetManager: Starting task 0.0 in stage 40.0 (TID 33) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:47 INFO BlockManagerInfo: Removed broadcast_49_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 126.9 MiB)
26/05/01 05:16:47 INFO BlockManagerInfo: Removed broadcast_49_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:47 INFO BlockManagerInfo: Removed broadcast_50_piece0 on master-node:35479 in memory (size: 62.5 KiB, free: 126.9 MiB)
26/05/01 05:16:47 INFO BlockManagerInfo: Removed broadcast_50_piece0 on worker-node-1:34163 in memory (size: 62.5 KiB, free: 413.9 MiB)
26/05/01 05:16:47 INFO BlockManagerInfo: Added broadcast_53_piece0 in memory on worker-node-1:34163 (size: 62.5 KiB, free: 413.8 MiB)
26/05/01 05:16:48 INFO BlockManagerInfo: Added broadcast_52_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:48 INFO TaskSetManager: Finished task 0.0 in stage 40.0 (TID 33) in 1532 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:48 INFO YarnScheduler: Removed TaskSet 40.0, whose tasks have all completed, from pool
26/05/01 05:16:48 INFO DAGScheduler: ShuffleMapStage 40 (map at MulticlassMetrics.scala:52) finished in 1.577 s
26/05/01 05:16:48 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:48 INFO DAGScheduler: running: Set()
26/05/01 05:16:48 INFO DAGScheduler: waiting: Set(ResultStage 41)
26/05/01 05:16:48 INFO DAGScheduler: failed: Set()
26/05/01 05:16:48 INFO DAGScheduler: Submitting ResultStage 41 (ShuffledRDD[135] at reduceByKey at MulticlassMetrics.scala:61), which has no missing parents
26/05/01 05:16:48 INFO MemoryStore: Block broadcast_54 stored as values in memory (estimated size 5.3 KiB, free 125.5 MiB)
26/05/01 05:16:48 INFO MemoryStore: Block broadcast_54_piece0 stored as bytes in memory (estimated size 3.1 KiB, free 125.5 MiB)
26/05/01 05:16:48 INFO BlockManagerInfo: Added broadcast_54_piece0 in memory on master-node:35479 (size: 3.1 KiB, free: 126.9 MiB)
26/05/01 05:16:48 INFO SparkContext: Created broadcast 54 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:48 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 41 (ShuffledRDD[135] at reduceByKey at MulticlassMetrics.scala:61) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:48 INFO YarnScheduler: Adding task set 41.0 with 1 tasks resource profile 0
26/05/01 05:16:48 INFO TaskSetManager: Starting task 0.0 in stage 41.0 (TID 34) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9336 bytes)
26/05/01 05:16:48 INFO BlockManagerInfo: Added broadcast_54_piece0 in memory on worker-node-1:34163 (size: 3.1 KiB, free: 413.7 MiB)
26/05/01 05:16:49 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 14 to 164.92.103.148:51604
26/05/01 05:16:49 INFO TaskSetManager: Finished task 0.0 in stage 41.0 (TID 34) in 505 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:49 INFO YarnScheduler: Removed TaskSet 41.0, whose tasks have all completed, from pool
26/05/01 05:16:49 INFO DAGScheduler: ResultStage 41 (collectAsMap at MulticlassMetrics.scala:61) finished in 0.530 s
26/05/01 05:16:49 INFO DAGScheduler: Job 22 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:49 INFO YarnScheduler: Killing all running tasks in stage 41: Stage finished
26/05/01 05:16:49 INFO DAGScheduler: Job 22 finished: collectAsMap at MulticlassMetrics.scala:61, took 2.128962 s

===== MODEL METRICS =====
AUC-ROC: 0.7526007592077572
Accuracy: 0.8964081207704321
F1 Score: 0.8674868332850887
Precision: 0.8913968074285104
Recall: 0.8964081207704321

===== CONFUSION MATRIX =====
26/05/01 05:16:49 INFO FileSourceStrategy: Pushed Filters:
26/05/01 05:16:49 INFO FileSourceStrategy: Post-Scan Filters: atleastnnonnulls(1, gettimestamp(Date#19, MM/dd/yyyy hh:mm:ss a, TimestampType, Some(Etc/UTC), false))
26/05/01 05:16:49 INFO BlockManagerInfo: Removed broadcast_52_piece0 on master-node:35479 in memory (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:49 INFO BlockManagerInfo: Removed broadcast_52_piece0 on worker-node-1:34163 in memory (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:49 INFO BlockManagerInfo: Removed broadcast_53_piece0 on master-node:35479 in memory (size: 62.5 KiB, free: 127.0 MiB)
26/05/01 05:16:49 INFO CodeGenerator: Code generated in 188.382793 ms
26/05/01 05:16:49 INFO MemoryStore: Block broadcast_55 stored as values in memory (estimated size 317.1 KiB, free 125.8 MiB)
26/05/01 05:16:49 INFO MemoryStore: Block broadcast_55_piece0 stored as bytes in memory (estimated size 57.6 KiB, free 125.7 MiB)
26/05/01 05:16:49 INFO BlockManagerInfo: Added broadcast_55_piece0 in memory on master-node:35479 (size: 57.6 KiB, free: 127.0 MiB)
26/05/01 05:16:49 INFO SparkContext: Created broadcast 55 from showString at NativeMethodAccessorImpl.java:0
26/05/01 05:16:49 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4194304 bytes, open cost is considered as scanning 4194304 bytes.
26/05/01 05:16:49 INFO BlockManagerInfo: Removed broadcast_53_piece0 on worker-node-1:34163 in memory (size: 62.5 KiB, free: 413.9 MiB)
26/05/01 05:16:49 INFO DAGScheduler: Registering RDD 139 (showString at NativeMethodAccessorImpl.java:0) as input to shuffle 15
26/05/01 05:16:49 INFO DAGScheduler: Got map stage job 23 (showString at NativeMethodAccessorImpl.java:0) with 1 output partitions
26/05/01 05:16:49 INFO DAGScheduler: Final stage: ShuffleMapStage 42 (showString at NativeMethodAccessorImpl.java:0)
26/05/01 05:16:49 INFO DAGScheduler: Parents of final stage: List()
26/05/01 05:16:49 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:49 INFO DAGScheduler: Submitting ShuffleMapStage 42 (MapPartitionsRDD[139] at showString at NativeMethodAccessorImpl.java:0), which has no missing parents
26/05/01 05:16:49 INFO MemoryStore: Block broadcast_56 stored as values in memory (estimated size 153.4 KiB, free 125.6 MiB)
26/05/01 05:16:49 INFO MemoryStore: Block broadcast_56_piece0 stored as bytes in memory (estimated size 63.1 KiB, free 125.5 MiB)
26/05/01 05:16:49 INFO BlockManagerInfo: Added broadcast_56_piece0 in memory on master-node:35479 (size: 63.1 KiB, free: 126.9 MiB)
26/05/01 05:16:49 INFO SparkContext: Created broadcast 56 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:49 INFO DAGScheduler: Submitting 1 missing tasks from ShuffleMapStage 42 (MapPartitionsRDD[139] at showString at NativeMethodAccessorImpl.java:0) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:49 INFO YarnScheduler: Adding task set 42.0 with 1 tasks resource profile 0
26/05/01 05:16:49 INFO TaskSetManager: Starting task 0.0 in stage 42.0 (TID 35) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 10124 bytes)
26/05/01 05:16:49 INFO BlockManagerInfo: Removed broadcast_54_piece0 on master-node:35479 in memory (size: 3.1 KiB, free: 126.9 MiB)
26/05/01 05:16:49 INFO BlockManagerInfo: Removed broadcast_54_piece0 on worker-node-1:34163 in memory (size: 3.1 KiB, free: 413.9 MiB)
26/05/01 05:16:50 INFO BlockManagerInfo: Added broadcast_56_piece0 in memory on worker-node-1:34163 (size: 63.1 KiB, free: 413.8 MiB)
26/05/01 05:16:51 INFO BlockManagerInfo: Added broadcast_55_piece0 in memory on worker-node-1:34163 (size: 57.6 KiB, free: 413.8 MiB)
26/05/01 05:16:52 INFO TaskSetManager: Finished task 0.0 in stage 42.0 (TID 35) in 2233 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:52 INFO YarnScheduler: Removed TaskSet 42.0, whose tasks have all completed, from pool
26/05/01 05:16:52 INFO DAGScheduler: ShuffleMapStage 42 (showString at NativeMethodAccessorImpl.java:0) finished in 2.253 s
26/05/01 05:16:52 INFO DAGScheduler: looking for newly runnable stages
26/05/01 05:16:52 INFO DAGScheduler: running: Set()
26/05/01 05:16:52 INFO DAGScheduler: waiting: Set()
26/05/01 05:16:52 INFO DAGScheduler: failed: Set()
26/05/01 05:16:52 INFO ShufflePartitionsUtil: For shuffle(15), advisory target size: 67108864, actual target size 1048576, minimum partition size: 1048576
26/05/01 05:16:52 INFO BlockManagerInfo: Removed broadcast_56_piece0 on master-node:35479 in memory (size: 63.1 KiB, free: 127.0 MiB)
26/05/01 05:16:52 INFO HashAggregateExec: spark.sql.codegen.aggregate.map.twolevel.enabled is set to true, but current version of codegened fast hashmap does not support this aggregate.
26/05/01 05:16:52 INFO BlockManagerInfo: Removed broadcast_56_piece0 on worker-node-1:34163 in memory (size: 63.1 KiB, free: 413.8 MiB)
26/05/01 05:16:52 INFO CodeGenerator: Code generated in 33.12183 ms
26/05/01 05:16:52 INFO SparkContext: Starting job: showString at NativeMethodAccessorImpl.java:0
26/05/01 05:16:52 INFO DAGScheduler: Got job 24 (showString at NativeMethodAccessorImpl.java:0) with 1 output partitions
26/05/01 05:16:52 INFO DAGScheduler: Final stage: ResultStage 44 (showString at NativeMethodAccessorImpl.java:0)
26/05/01 05:16:52 INFO DAGScheduler: Parents of final stage: List(ShuffleMapStage 43)
26/05/01 05:16:52 INFO DAGScheduler: Missing parents: List()
26/05/01 05:16:52 INFO DAGScheduler: Submitting ResultStage 44 (MapPartitionsRDD[142] at showString at NativeMethodAccessorImpl.java:0), which has no missing parents
26/05/01 05:16:52 INFO MemoryStore: Block broadcast_57 stored as values in memory (estimated size 139.3 KiB, free 125.6 MiB)
26/05/01 05:16:52 INFO MemoryStore: Block broadcast_57_piece0 stored as bytes in memory (estimated size 58.7 KiB, free 125.5 MiB)
26/05/01 05:16:52 INFO BlockManagerInfo: Added broadcast_57_piece0 in memory on master-node:35479 (size: 58.7 KiB, free: 126.9 MiB)
26/05/01 05:16:52 INFO SparkContext: Created broadcast 57 from broadcast at DAGScheduler.scala:1585
26/05/01 05:16:52 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 44 (MapPartitionsRDD[142] at showString at NativeMethodAccessorImpl.java:0) (first 15 tasks are for partitions Vector(0))
26/05/01 05:16:52 INFO YarnScheduler: Adding task set 44.0 with 1 tasks resource profile 0
26/05/01 05:16:52 INFO TaskSetManager: Starting task 0.0 in stage 44.0 (TID 36) (worker-node-1, executor 1, partition 0, NODE_LOCAL, 9518 bytes)
26/05/01 05:16:52 INFO BlockManagerInfo: Added broadcast_57_piece0 in memory on worker-node-1:34163 (size: 58.7 KiB, free: 413.8 MiB)
26/05/01 05:16:52 INFO MapOutputTrackerMasterEndpoint: Asked to send map output locations for shuffle 15 to 164.92.103.148:51604
26/05/01 05:16:53 INFO TaskSetManager: Finished task 0.0 in stage 44.0 (TID 36) in 810 ms on worker-node-1 (executor 1) (1/1)
26/05/01 05:16:53 INFO YarnScheduler: Removed TaskSet 44.0, whose tasks have all completed, from pool
26/05/01 05:16:53 INFO DAGScheduler: ResultStage 44 (showString at NativeMethodAccessorImpl.java:0) finished in 0.827 s
26/05/01 05:16:53 INFO DAGScheduler: Job 24 is finished. Cancelling potential speculative or zombie tasks for this job
26/05/01 05:16:53 INFO YarnScheduler: Killing all running tasks in stage 44: Stage finished
26/05/01 05:16:53 INFO DAGScheduler: Job 24 finished: showString at NativeMethodAccessorImpl.java:0, took 0.839430 s
26/05/01 05:16:53 INFO CodeGenerator: Code generated in 13.599358 ms
+-----+----------+-----+
|label|prediction|count|
+-----+----------+-----+
|    1|       0.0|  190|
|    0|       0.0| 1673|
|    1|       1.0|   49|
|    0|       1.0|    9|
+-----+----------+-----+

26/05/01 05:16:53 INFO SparkContext: SparkContext is stopping with exitCode 0.
26/05/01 05:16:53 INFO SparkUI: Stopped Spark web UI at http://master-node:4040
26/05/01 05:16:53 INFO YarnClientSchedulerBackend: Interrupting monitor thread
26/05/01 05:16:53 INFO YarnClientSchedulerBackend: Shutting down all executors
26/05/01 05:16:53 INFO YarnSchedulerBackend$YarnDriverEndpoint: Asking each executor to shut down
26/05/01 05:16:53 INFO YarnClientSchedulerBackend: YARN client scheduler backend Stopped
26/05/01 05:16:53 INFO MapOutputTrackerMasterEndpoint: MapOutputTrackerMasterEndpoint stopped!
26/05/01 05:16:53 INFO MemoryStore: MemoryStore cleared
26/05/01 05:16:53 INFO BlockManager: BlockManager stopped
26/05/01 05:16:53 INFO BlockManagerMaster: BlockManagerMaster stopped
26/05/01 05:16:53 INFO OutputCommitCoordinator$OutputCommitCoordinatorEndpoint: OutputCommitCoordinator stopped!
26/05/01 05:16:53 INFO SparkContext: Successfully stopped SparkContext
26/05/01 05:16:54 INFO ShutdownHookManager: Shutdown hook called
26/05/01 05:16:54 INFO ShutdownHookManager: Deleting directory /tmp/spark-52d769b0-971b-45f3-95c1-88316f86ffde
26/05/01 05:16:54 INFO ShutdownHookManager: Deleting directory /tmp/spark-52d769b0-971b-45f3-95c1-88316f86ffde/pyspark-d594546a-996c-408f-b59b-7907033190ff
26/05/01 05:16:54 INFO ShutdownHookManager: Deleting directory /tmp/spark-5f643fee-b92e-45b6-8bc8-c96e0282cd63
```

---


