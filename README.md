# Spark App - Iris Data Classification

This project demonstrates Iris dataset classification with Apache Spark and provides a practical guide to running Spark applications on a cluster.

## Set up the App
- Clone or download this Git [repository](https://github.com/osekoo/spark-iris) to your local machine.  
Open your project with your favorite IDE (IntelliJ, VS Code, etc.)
Then, explore the main application file:
```
src/main/scala/MainApp.scala
```

## Run App Locally
First, package the application
```
sbt package
```

```bash
aurelien@LAPTOP-4SJMQBCP:~/workspace/cluster/spark-iris$ sbt package
[info] Updated file /home/aurelien/workspace/cluster/spark-iris/project/build.properties: set sbt.version to 1.10.7
[info] welcome to sbt 1.10.7 (Temurin Java 1.8.0_432)
[info] loading project definition from /home/aurelien/workspace/cluster/spark-iris/project
[info] loading settings for project spark-iris from build.sbt...
[info] set current project to iris (in build file:/home/aurelien/workspace/cluster/spark-iris/)
[info] compiling 1 Scala source to /home/aurelien/workspace/cluster/spark-iris/target/scala-2.12/classes ...
[success] Total time: 10 s, completed Apr 3, 2025 6:18:05 PM
```

Then, run the application:

For Windows user:
```bash
./run-app.bat
```

For Linux/MacOS
```bash
chmod +x ./run-app.sh
./run-app
```

> The application will run inside docker container.

```bash
aurelien@LAPTOP-4SJMQBCP:~/workspace/cluster/spark-iris$ ./run-app.sh
Stopping Spark cluster...
Error response from daemon: No such container: spark-submit
Error response from daemon: No such container: spark-worker
Error response from daemon: No such container: spark-master
Starting Spark cluster...
WARN[0000] /home/aurelien/workspace/cluster/spark-iris/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
[+] Running 4/4
 ✔ Network spark-iris_default  Created                                                                             0.1s
 ✔ Container spark-master      Started                                                                             1.5s
 ✔ Container spark-submit      Started                                                                             1.9s
 ✔ Container spark-worker      Started                                                                             1.9s
Waiting for Spark master to be ready...
Submitting Spark job...
dos2unix: converting file /app/spark-submit.sh to Unix format...
25/04/03 16:21:58 INFO SparkContext: Running Spark version 3.5.3
25/04/03 16:21:58 INFO SparkContext: OS info Linux, 5.15.167.4-microsoft-standard-WSL2, amd64
25/04/03 16:21:58 INFO SparkContext: Java version 1.8.0_432
25/04/03 16:21:58 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
25/04/03 16:21:58 INFO ResourceUtils: ==============================================================
25/04/03 16:21:58 INFO ResourceUtils: No custom resources configured for spark.driver.
25/04/03 16:21:58 INFO ResourceUtils: ==============================================================
25/04/03 16:21:58 INFO SparkContext: Submitted application: Iris Data Classification
25/04/03 16:21:58 INFO ResourceProfile: Default ResourceProfile created, executor resources: Map(cores -> name: cores, amount: 4, script: , vendor: , memory -> name: memory, amount: 2048, script: , vendor: , offHeap -> name: offHeap, amount: 0, script: , vendor: ), task resources: Map(cpus -> name: cpus, amount: 1.0)
25/04/03 16:21:58 INFO ResourceProfile: Limiting resource is cpus at 4 tasks per executor
25/04/03 16:21:58 INFO ResourceProfileManager: Added ResourceProfile id: 0
25/04/03 16:21:58 INFO SecurityManager: Changing view acls to: root
25/04/03 16:21:58 INFO SecurityManager: Changing modify acls to: root
25/04/03 16:21:58 INFO SecurityManager: Changing view acls groups to:
25/04/03 16:21:58 INFO SecurityManager: Changing modify acls groups to:
25/04/03 16:21:58 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users with view permissions: root; groups with view permissions: EMPTY; users with modify permissions: root; groups with modify permissions: EMPTY
25/04/03 16:21:59 INFO Utils: Successfully started service 'sparkDriver' on port 40759.
25/04/03 16:21:59 INFO SparkEnv: Registering MapOutputTracker
25/04/03 16:21:59 INFO SparkEnv: Registering BlockManagerMaster
25/04/03 16:21:59 INFO BlockManagerMasterEndpoint: Using org.apache.spark.storage.DefaultTopologyMapper for getting topology information
25/04/03 16:21:59 INFO BlockManagerMasterEndpoint: BlockManagerMasterEndpoint up
25/04/03 16:21:59 INFO SparkEnv: Registering BlockManagerMasterHeartbeat
25/04/03 16:21:59 INFO DiskBlockManager: Created local directory at /tmp/blockmgr-7982498f-b1ea-4df9-8aa1-f0e45d669cd6
25/04/03 16:21:59 INFO MemoryStore: MemoryStore started with capacity 366.3 MiB
25/04/03 16:21:59 INFO SparkEnv: Registering OutputCommitCoordinator
25/04/03 16:21:59 INFO JettyUtils: Start Jetty 0.0.0.0:4040 for SparkUI
25/04/03 16:21:59 INFO Utils: Successfully started service 'SparkUI' on port 4040.
25/04/03 16:21:59 INFO SparkContext: Added JAR file:/app/target/scala-2.12/iris_2.12-0.1.jar at spark://3fc14547e77f:40759/jars/iris_2.12-0.1.jar with timestamp 1743697318616
25/04/03 16:21:59 INFO StandaloneAppClient$ClientEndpoint: Connecting to master spark://spark-master:7077...
25/04/03 16:21:59 INFO TransportClientFactory: Successfully created connection to spark-master/172.18.0.2:7077 after 30 ms (0 ms spent in bootstraps)
25/04/03 16:22:00 INFO StandaloneSchedulerBackend: Connected to Spark cluster with app ID app-20250403162200-0000
25/04/03 16:22:00 INFO Utils: Successfully started service 'org.apache.spark.network.netty.NettyBlockTransferService' on port 38157.
25/04/03 16:22:00 INFO NettyBlockTransferService: Server created on 3fc14547e77f:38157
25/04/03 16:22:00 INFO BlockManager: Using org.apache.spark.storage.RandomBlockReplicationPolicy for block replication policy
25/04/03 16:22:00 INFO BlockManagerMaster: Registering BlockManager BlockManagerId(driver, 3fc14547e77f, 38157, None)
25/04/03 16:22:00 INFO BlockManagerMasterEndpoint: Registering block manager 3fc14547e77f:38157 with 366.3 MiB RAM, BlockManagerId(driver, 3fc14547e77f, 38157, None)
25/04/03 16:22:00 INFO BlockManagerMaster: Registered BlockManager BlockManagerId(driver, 3fc14547e77f, 38157, None)
25/04/03 16:22:00 INFO BlockManager: Initialized BlockManager: BlockManagerId(driver, 3fc14547e77f, 38157, None)
25/04/03 16:22:00 INFO StandaloneAppClient$ClientEndpoint: Executor added: app-20250403162200-0000/0 on worker-20250403162155-172.18.0.3-39107 (172.18.0.3:39107) with 4 core(s)
25/04/03 16:22:00 INFO StandaloneSchedulerBackend: Granted executor ID app-20250403162200-0000/0 on hostPort 172.18.0.3:39107 with 4 core(s), 2.0 GiB RAM
25/04/03 16:22:00 INFO StandaloneAppClient$ClientEndpoint: Executor added: app-20250403162200-0000/1 on worker-20250403162155-172.18.0.3-39107 (172.18.0.3:39107) with 4 core(s)
25/04/03 16:22:00 INFO StandaloneSchedulerBackend: Granted executor ID app-20250403162200-0000/1 on hostPort 172.18.0.3:39107 with 4 core(s), 2.0 GiB RAM
25/04/03 16:22:00 INFO StandaloneAppClient$ClientEndpoint: Executor added: app-20250403162200-0000/2 on worker-20250403162155-172.18.0.3-39107 (172.18.0.3:39107) with 4 core(s)
25/04/03 16:22:00 INFO StandaloneSchedulerBackend: Granted executor ID app-20250403162200-0000/2 on hostPort 172.18.0.3:39107 with 4 core(s), 2.0 GiB RAM
25/04/03 16:22:00 INFO StandaloneAppClient$ClientEndpoint: Executor updated: app-20250403162200-0000/2 is now RUNNING
25/04/03 16:22:00 INFO StandaloneAppClient$ClientEndpoint: Executor updated: app-20250403162200-0000/0 is now RUNNING
25/04/03 16:22:00 INFO StandaloneAppClient$ClientEndpoint: Executor updated: app-20250403162200-0000/1 is now RUNNING
25/04/03 16:22:00 INFO StandaloneSchedulerBackend: SchedulerBackend is ready for scheduling beginning after reached minRegisteredResourcesRatio: 0.0
+---+-------------+------------+-------------+------------+---------------+
|Id |SepalLengthCm|SepalWidthCm|PetalLengthCm|PetalWidthCm|Species        |
+---+-------------+------------+-------------+------------+---------------+
|106|7.6          |3.0         |6.6          |2.1         |Iris-virginica |
|17 |5.4          |3.9         |1.3          |0.4         |Iris-setosa    |
|110|7.2          |3.6         |6.1          |2.5         |Iris-virginica |
|123|7.7          |2.8         |6.7          |2.0         |Iris-virginica |
|91 |5.5          |2.6         |4.4          |1.2         |Iris-versicolor|
|129|6.4          |2.8         |5.6          |2.1         |Iris-virginica |
|80 |5.7          |2.6         |3.5          |1.0         |Iris-versicolor|
|142|6.9          |3.1         |5.1          |2.3         |Iris-virginica |
|59 |6.6          |2.9         |4.6          |1.3         |Iris-versicolor|
|89 |5.6          |3.0         |4.1          |1.3         |Iris-versicolor|
+---+-------------+------------+-------------+------------+---------------+
only showing top 10 rows

+--------------------------------------------------------------------------------+-----+
|features                                                                        |label|
+--------------------------------------------------------------------------------+-----+
|[0.9166666666666665,0.41666666666666663,0.9491525423728813,0.8333333333333334]  |2.0  |
|[0.30555555555555564,0.7916666666666665,0.05084745762711865,0.12500000000000003]|0.0  |
|[0.8055555555555556,0.6666666666666666,0.8644067796610169,1.0]                  |2.0  |
|[0.9444444444444444,0.3333333333333332,0.9661016949152542,0.7916666666666666]   |2.0  |
|[0.3333333333333333,0.25,0.576271186440678,0.4583333333333333]                  |1.0  |
|[0.5833333333333334,0.3333333333333332,0.7796610169491525,0.8333333333333334]   |2.0  |
|[0.38888888888888895,0.25,0.423728813559322,0.375]                              |1.0  |
|[0.7222222222222222,0.4583333333333333,0.6949152542372881,0.9166666666666666]   |2.0  |
|[0.6388888888888887,0.37499999999999994,0.6101694915254237,0.5]                 |1.0  |
|[0.361111111111111,0.41666666666666663,0.5254237288135593,0.5]                  |1.0  |
+--------------------------------------------------------------------------------+-----+
only showing top 10 rows

=====================================================
Accuracy: 0.9642857142857143
=====================================================
Saving model to output/iris_model
Spark job submitted.
```

## Run App on the LAMSADE Cluster

### Step 1 - Set up your SSH Key:
Request your personal SSH key (`your_key`) from the administrator.  
It will look something like:
```
id_123_<your_username>.key
```
If you encounter permission issue (SSH will reject your key if it is too visible to others):  
**On Linux/macOS**
```bash
chmod 600 <your_key>
```
**On Windows**
- Right-click on the key file → Properties → Security tab
- Remove access for `Users` or `Everyone`
- Make sure **only your user** has Full Control

### Step 2 – Upload the Iris Data Folder to Your Cluster Workspace
First, connect to the LAMSADE cluster:

```bash
ssh -p 5022 -i <your_key> <your_username>@ssh.lamsade.dauphine.fr
```

Then, create your workspace on remote machine
```bash
mkdir -p ~/workspace/data
```

Pay attention on the option : `-p` for `ssh` and `-P` for `scp`.

```bash
aurelien@LAPTOP-4SJMQBCP:~/workspace/cluster/spark-iris$ ssh -p 5022 -i ./key/id_ed25519_aduvignac-rosa.key aduvignac-rosa@ssh.lamsade.dauphine.fr
aurelien@LAPTOP-4SJMQBCP:~/workspace/cluster/spark-iris$ ssh -p 5022 -i ./key/id_ed25519_aduvignac-rosa.key aduvignac-rosa@ssh.lamsade.dauphine.fr
 _                             _
| | __ _ _ __ ___   __ _  __ _| |_ ___
| |/ _` | '_ ` _ \ / _` |/ _` | __/ _ \
| | (_| | | | | | | (_| | (_| | ||  __/
|_|\__,_|_| |_| |_|\__, |\__,_|\__\___|
                   |___/
Linux lamgate 6.1.0-28-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.119-1 (2024-11-22) x86_64
uptime :  19:22:00 up 98 days,  6:49, 12 users,  load average: 0.12, 0.07, 0.01
Memoire utilisée : 1199 Mo / 7940 Mo (15%)
Free /dev/sda1 Space : 13G / 18G
Free /home/lamsade/local Space : 16T / 25T
ens18 adress : 10.1.3.35
ens19 adress : 193.48.71.233
Max LAMSADE diskspace usage by :  flebronnec with 1079 Go  on Thu Apr  3 04:32:26 CEST 2025
Last login: Thu Apr  3 19:21:38 2025 from 88.185.198.243
The authenticity of host 'vmhadoopmaster (10.1.4.80)' can't be established.
ED25519 key fingerprint is SHA256:0xlNihqal4yGSCA4wh6+seYRBZ02TMB9Q29nNMBwTRo.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'vmhadoopmaster' (ED25519) to the list of known hosts.
                 _               _                                       _
__   ___ __ ___ | |__   __ _  __| | ___   ___  _ __  _ __ ___   __ _ ___| |_
\ \ / / '_ ` _ \| '_ \ / _` |/ _` |/ _ \ / _ \| '_ \| '_ ` _ \ / _` / __| __|
 \ V /| | | | | | | | | (_| | (_| | (_) | (_) | |_) | | | | | | (_| \__ \ |_
  \_/ |_| |_| |_|_| |_|\__,_|\__,_|\___/ \___/| .__/|_| |_| |_|\__,_|___/\__|
                                              |_|

  ___ _ __
 / _ \ '__|
|  __/ |
 \___|_|

Linux vmhadoopmaster 6.1.0-32-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.129-1 (2025-03-06) x86_64
uptime :  19:22:04 up 13 days, 21:11,  5 users,  load average: 2.19, 1.27, 0.71
Memoire utilisée : 6481 Mo / 64304 Mo (10%)
Free / Space : 35G / 50G
Free /opt Space : 822G / 984G
Free /opt/cephfs Space : 3.2T / 5.1T
ens18 adress : 10.40.178.80
ens19 adress : 10.1.4.80
hadoop env loaded
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa$ ls
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa$ mkdir workspace
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa$
```

Now, from your local machine:
```bash
scp -P 5022 -i <your_key> -r data <your_username>@ssh.lamsade.dauphine.fr:~/workspace
```

if `scp` command is not available, you can use `sftp`:

```bash
aurelien@LAPTOP-4SJMQBCP:~/workspace/cluster/spark-iris$ sftp -oPort=5022 -i ./key/id_ed25519_aduvignac-rosa.key aduvignac-rosa@ssh.lamsade.dauphine.fr
Connected to ssh.lamsade.dauphine.fr.
sftp> cd /opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace/
realpath /opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace/: No such file
sftp> ls
workspace
sftp> cd workspace/
sftp> ls
test.txt
sftp> rm -f test.txt
rm: Invalid flag -f
sftp> rm test.txt
Removing /home/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace/test.txt
sftp> put data.zip
Uploading data.zip to /home/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace/data.zip
data.zip                                                                              100% 1460   202.3KB/s   00:00
sftp> ls
data.zip
sftp> bye
```

### Step 3 – Copy Data to HDFS (on the remote server)
First, connect to the LAMSADE cluster:

```bash
ssh -p 5022 -i <your_key> <your_username>@ssh.lamsade.dauphine.fr
```
Then, upload the data to hdfs:
```bash
cd ~/workspace
hdfs dfs -mkdir -p /students/p6emiasd2025/<your_username>/data
hdfs dfs -put data/* /students/p6emiasd2025/<your_username>/data
```

After we connect using `ssh` and unzip the file:

```bash
aurelien@LAPTOP-4SJMQBCP:~/workspace/cluster/spark-iris$ ssh -p 5022 -i ./key/id_ed25519_aduvignac-rosa.key aduvignac-rosa@ssh.lamsade.dauphine.fr
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa$ cd workspace/
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace$ ls
data.zip
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace$ unzip data.zip
Archive:  data.zip
   creating: data/
  inflating: data/Iris.csv
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace$ rm data.zip
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace$ ls
data
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace$ hdfs dfs -mkdir -p /students/p6emiasd2025/aduvignac-rosa/data
aduvignac-rosa@vmhadoopmaster:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace$ hdfs dfs -put data/* /students/p6emiasd2025/aduvignac-rosa/data
```

### Step 4 – Upload the Iris App JAR to Your Workspace

```bash
scp -P 5022 -i <your_key> iris_2.12-0.1.jar <your_username>@ssh.lamsade.dauphine.fr:~/workspace
```

### Step 5 – Run the Spark Application
First, connect to the LAMSADE cluster:

```bash
ssh -p 5022 -i <your_key> <your_username>@ssh.lamsade.dauphine.fr
```

Then, run your Spark job from your workspace:
```bash
cd ~/workspace

spark-submit \
    --deploy-mode client \
    --executor-cores 4 \
    --executor-memory 2G \
    --num-executors 1 \
    --class "MainApp" \
    iris_2.12-0.1.jar \
    /students/p6emiasd2025/<your_username>/data/Iris.csv \
    /students/p6emiasd2025/<your_username>/output
```

> `/students/p6emiasd2025/<your_username>/data/Iris.csv` is the HDFS path  
> `/students/p6emiasd2025/<your_username>/output` is the HDFS output folder (will be created if it doesn't exist)

```bash
aduvignac-rosa@vmhadoopmaster:~/workspace$ spark-submit \
    --deploy-mode client \
    --executor-cores 4 \
    --executor-memory 2G \
    --num-executors 1 \
    --class "MainApp" \
    iris_2.12-0.1.jar \
    /students/p6emiasd2025/aduvignac-rosa/data/Iris.csv \
    /students/p6emiasd2025/aduvignac-rosa/output
25/04/03 20:23:38 INFO SparkContext: Running Spark version 3.5.1
25/04/03 20:23:39 INFO SparkContext: OS info Linux, 6.1.0-32-amd64, amd64
25/04/03 20:23:39 INFO SparkContext: Java version 1.8.0_372
25/04/03 20:23:39 INFO ResourceUtils: ==============================================================
25/04/03 20:23:39 INFO ResourceUtils: No custom resources configured for spark.driver.
25/04/03 20:23:39 INFO ResourceUtils: ==============================================================
25/04/03 20:23:39 INFO SparkContext: Submitted application: Iris Data Classification
25/04/03 20:23:39 INFO ResourceProfile: Default ResourceProfile created, executor resources: Map(cores -> name: cores, amount: 1, script: , vendor: , memory -> name: memory, amount: 1024, script: , vendor: , offHeap -> name: offHeap, amount: 0, script: , vendor: ), task resources: Map(cpus -> name: cpus, amount: 1.0)
25/04/03 20:23:39 INFO ResourceProfile: Limiting resource is cpu
25/04/03 20:23:39 INFO ResourceProfileManager: Added ResourceProfile id: 0
25/04/03 20:23:39 INFO SecurityManager: Changing view acls to: aduvignac-rosa
25/04/03 20:23:39 INFO SecurityManager: Changing modify acls to: aduvignac-rosa
25/04/03 20:23:39 INFO SecurityManager: Changing view acls groups to:
25/04/03 20:23:39 INFO SecurityManager: Changing modify acls groups to:
25/04/03 20:23:39 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users with view permissions: aduvignac-rosa; groups with view permissions: EMPTY; users with modify permissions: aduvignac-rosa; groups with modify permissions: EMPTY
25/04/03 20:23:39 INFO Utils: Successfully started service 'sparkDriver' on port 34391.
25/04/03 20:23:40 INFO SparkEnv: Registering MapOutputTracker
25/04/03 20:23:40 INFO SparkEnv: Registering BlockManagerMaster
25/04/03 20:23:40 INFO BlockManagerMasterEndpoint: Using org.apache.spark.storage.DefaultTopologyMapper for getting topology information
25/04/03 20:23:40 INFO BlockManagerMasterEndpoint: BlockManagerMasterEndpoint up
25/04/03 20:23:40 INFO SparkEnv: Registering BlockManagerMasterHeartbeat
25/04/03 20:23:40 INFO DiskBlockManager: Created local directory at /tmp/blockmgr-f11001f7-3387-4ccc-b199-c7e118671b35
25/04/03 20:23:40 INFO MemoryStore: MemoryStore started with capacity 366.3 MiB
25/04/03 20:23:40 INFO SparkEnv: Registering OutputCommitCoordinator
25/04/03 20:23:40 INFO JettyUtils: Start Jetty 0.0.0.0:4040 for SparkUI
25/04/03 20:23:40 INFO Utils: Successfully started service 'SparkUI' on port 4040.
25/04/03 20:23:40 INFO SparkContext: Added JAR file:/opt/cephfs/users/students/p6emiasd2025/aduvignac-rosa/workspace/iris_2.12-0.1.jar at spark://vmhadoopmaster.srv.lamsade.dauphine.fr:34391/jars/iris_2.12-0.1.jar with timestamp 1743704618971
25/04/03 20:23:41 INFO Executor: Starting executor ID driver on host vmhadoopmaster.srv.lamsade.dauphine.fr
25/04/03 20:23:41 INFO Executor: OS info Linux, 6.1.0-32-amd64, amd64
25/04/03 20:23:41 INFO Executor: Java version 1.8.0_372
25/04/03 20:23:41 INFO Executor: Starting executor with user classpath (userClassPathFirst = false): ''
25/04/03 20:23:41 INFO Executor: Created or updated repl class loader org.apache.spark.util.MutableURLClassLoader@7f7af971 for default.
25/04/03 20:23:41 INFO Executor: Fetching spark://vmhadoopmaster.srv.lamsade.dauphine.fr:34391/jars/iris_2.12-0.1.jar with timestamp 1743704618971
25/04/03 20:23:41 INFO TransportClientFactory: Successfully created connection to vmhadoopmaster.srv.lamsade.dauphine.fr/10.1.4.80:34391 after 62 ms (0 ms spent in bootstraps)
25/04/03 20:23:41 INFO Utils: Fetching spark://vmhadoopmaster.srv.lamsade.dauphine.fr:34391/jars/iris_2.12-0.1.jar to /tmp/spark-93a4b9b4-979b-4fa2-a234-46b6ff4e9b3b/userFiles-abd3f879-704e-49af-88fe-1b0e25f1b1d0/fetchFileTemp6199183236129293637.tmp
25/04/03 20:23:41 INFO Executor: Adding file:/tmp/spark-93a4b9b4-979b-4fa2-a234-46b6ff4e9b3b/userFiles-abd3f879-704e-49af-88fe-1b0e25f1b1d0/iris_2.12-0.1.jar to class loader default
25/04/03 20:23:41 INFO Utils: Successfully started service 'org.apache.spark.network.netty.NettyBlockTransferService' on port 36107.
25/04/03 20:23:41 INFO NettyBlockTransferService: Server created on vmhadoopmaster.srv.lamsade.dauphine.fr:36107
25/04/03 20:23:41 INFO BlockManager: Using org.apache.spark.storage.RandomBlockReplicationPolicy for block replication policy
25/04/03 20:23:41 INFO BlockManagerMaster: Registering BlockManager BlockManagerId(driver, vmhadoopmaster.srv.lamsade.dauphine.fr, 36107, None)
25/04/03 20:23:41 INFO BlockManagerMasterEndpoint: Registering block manager vmhadoopmaster.srv.lamsade.dauphine.fr:36107 with 366.3 MiB RAM, BlockManagerId(driver, vmhadoopmaster.srv.lamsade.dauphine.fr, 36107, None)
25/04/03 20:23:41 INFO BlockManagerMaster: Registered BlockManager BlockManagerId(driver, vmhadoopmaster.srv.lamsade.dauphine.fr, 36107, None)
25/04/03 20:23:41 INFO BlockManager: Initialized BlockManager: BlockManagerId(driver, vmhadoopmaster.srv.lamsade.dauphine.fr, 36107, None)
+---+-------------+------------+-------------+------------+---------------+
|Id |SepalLengthCm|SepalWidthCm|PetalLengthCm|PetalWidthCm|Species        |
+---+-------------+------------+-------------+------------+---------------+
|106|7.6          |3.0         |6.6          |2.1         |Iris-virginica |
|17 |5.4          |3.9         |1.3          |0.4         |Iris-setosa    |
|110|7.2          |3.6         |6.1          |2.5         |Iris-virginica |
|123|7.7          |2.8         |6.7          |2.0         |Iris-virginica |
|91 |5.5          |2.6         |4.4          |1.2         |Iris-versicolor|
|129|6.4          |2.8         |5.6          |2.1         |Iris-virginica |
|80 |5.7          |2.6         |3.5          |1.0         |Iris-versicolor|
|142|6.9          |3.1         |5.1          |2.3         |Iris-virginica |
|59 |6.6          |2.9         |4.6          |1.3         |Iris-versicolor|
|89 |5.6          |3.0         |4.1          |1.3         |Iris-versicolor|
+---+-------------+------------+-------------+------------+---------------+
only showing top 10 rows

+--------------------------------------------------------------------------------+-----+
|features                                                                        |label|
+--------------------------------------------------------------------------------+-----+
|[0.9166666666666665,0.41666666666666663,0.9491525423728813,0.8333333333333334]  |2.0  |
|[0.30555555555555564,0.7916666666666665,0.05084745762711865,0.12500000000000003]|0.0  |
|[0.8055555555555556,0.6666666666666666,0.8644067796610169,1.0]                  |2.0  |
|[0.9444444444444444,0.3333333333333332,0.9661016949152542,0.7916666666666666]   |2.0  |
|[0.3333333333333333,0.25,0.576271186440678,0.4583333333333333]                  |1.0  |
|[0.5833333333333334,0.3333333333333332,0.7796610169491525,0.8333333333333334]   |2.0  |
|[0.38888888888888895,0.25,0.423728813559322,0.375]                              |1.0  |
|[0.7222222222222222,0.4583333333333333,0.6949152542372881,0.9166666666666666]   |2.0  |
|[0.6388888888888887,0.37499999999999994,0.6101694915254237,0.5]                 |1.0  |
|[0.361111111111111,0.41666666666666663,0.5254237288135593,0.5]                  |1.0  |
+--------------------------------------------------------------------------------+-----+
only showing top 10 rows

=====================================================
Accuracy: 0.9642857142857143
=====================================================
Saving model to /students/p6emiasd2025/aduvignac-rosa/output/iris_model
```


## Notes

- You can monitor the job via the **Spark UI** by opening a tunnel:
```bash
ssh -p 5022 -i <your_key> <your_username>@ssh.lamsade.dauphine.fr -L 8080:vmhadoopmaster.cluster.lamsade.dauphine.fr:8080
```
Then open [http://localhost:8080](http://localhost:8080) in your browser.
