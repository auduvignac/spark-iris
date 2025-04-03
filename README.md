# IRIS CLASSIFICATION – Spark App

This project performs classification on the Iris dataset using Apache Spark.


## Run App Locally

Ensure the script `run-app` is executable. Then run:

```bash
./run-app
```

> Make sure your local environment has Spark installed and configured.

---

## Run App on the LAMSADE Cluster

### Step 1 – Upload the Iris Data Folder to Your Cluster Workspace

From your local machine:
```bash
scp -P 5022 -i <your_key> -r data <your_username>@ssh.lamsade.dauphine.fr:~/workspace
```


### Step 2 – Copy Data to HDFS (on the remote server)

```bash
cd ~/workspace
hdfs dfs -mkdir -p data
hdfs dfs -put data/* data/
```


### Step 3 – Upload the Iris App JAR to Your Workspace

```bash
scp -P 5022 -i <your_key> iris_2.12-0.1.jar <your_username>@ssh.lamsade.dauphine.fr:~/workspace
```

### Step 4 – Run the Spark Application

```bash
cd ~/workspace

spark-submit \
    --deploy-mode client \
    --executor-cores 4 \
    --executor-memory 2G \
    --num-executors 1 \
    --class "MainApp" \
    iris_2.12-0.1.jar \
    data/Iris.csv \
    output
```

> 📁 `data/Iris.csv` is the HDFS path  
> 📁 `output` is the HDFS output folder (will be created if it doesn't exist)


## Notes

- You can monitor the job via the **Spark UI** by opening a tunnel:
```bash
ssh -p 5022 -i <your_key> <your_username>@ssh.lamsade.dauphine.fr -L 8080:vmhadoopmaster.cluster.lamsade.dauphine.fr:8080
```
Then open [http://localhost:8080](http://localhost:8080) in your browser.
