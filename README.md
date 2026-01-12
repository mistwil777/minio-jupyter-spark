# 🚀 MinIO + PySpark Docker Playground

I couldn’t find any working MinIO + PySpark combo, so I made this **Docker playground!**

Working as of **December 2025**.

> ⚠️ Don’t forget to change the MinIO username/password in docker-compose.yml before starting.
> 

---

## 📂 Project Structure

```
.
├── minio_data        # Persistent storage for MinIO
├── notebooks         # Your Jupyter notebooks
├── spark             # Dockerfile for PySpark environment
└── docker-compose.yml

```

---

## 🏃 Quick Start

1️⃣ Update MinIO credentials in `docker-compose.yml`:

```yaml
environment:
  MINIO_ROOT_USER: <your_username>
  MINIO_ROOT_PASSWORD: <your_password>

```

2️⃣ Run Docker Compose:

```bash
docker-compose up -d

```

3️⃣ Access your tools:

- MinIO Console: [http://localhost:9001](http://localhost:9001/) 🗄️
- PySpark Jupyter Lab: [http://localhost:8888](http://localhost:8888/) 📝
- Spark UI: [http://localhost:4040](http://localhost:4040/) 🔥

---

## 🛠️ Dockerfile Highlights (spark/Dockerfile)

- Installs AWS SDK & Hadoop AWS to let PySpark talk to MinIO
- Uses the 2025-11-25 `quay.io/jupyter/pyspark-notebook` as base

---

## 🚀 Launch you first SparkSession in Jupyter !

```python
from pyspark.sql import SparkSession
spark = SparkSession.builder \
  .master("local[*]") \
  .appName("TP Bronze Silver Gold") \
    .config("spark.hadoop.fs.s3a.aws.credentials.provider", 
            "org.apache.hadoop.fs.s3a.SimpleAWSCredentialsProvider") \
  .config("spark.jars.packages", "org.apache.hadoop:hadoop-aws:3.3.4") \
  .config("spark.hadoop.fs.s3a.endpoint", "http://minio:9000") \
  .config("spark.hadoop.fs.s3a.access.key", "minioadmin") \
  .config("spark.hadoop.fs.s3a.secret.key", "minioadmin") \
  .config("spark.hadoop.fs.s3a.impl", "org.apache.hadoop.fs.s3a.S3AFileSystem") \
  .config("spark.hadoop.fs.s3a.path.style.access", "true") \
  .config("fs.s3a.threads.keepalivetime", "60000")\
  .config("fs.s3a.connection.establish.timeout", "60000")\
  .config("fs.s3a.connection.timeout", "60000")\
  .config("spark.hadoop.fs.s3a.v2", "false")\
  .config("fs.s3a.multipart.purge.age", "60000")\
  .getOrCreate()
```

## 🎉 License

This project is licensed under the **MIT License** – totally free to use, tweak, and share.
