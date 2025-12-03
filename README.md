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
- Uses the latest `quay.io/jupyter/pyspark-notebook` as base

---

## 🎉 License

This project is licensed under the **MIT License** – totally free to use, tweak, and share.
