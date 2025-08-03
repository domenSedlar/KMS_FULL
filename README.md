# KMS_FULL

## How to run

**Populate the database**

```bash
docker compose up -d milvus-etcd milvus-minio milvus-standalone
cd KM-KnowledgeManager/kms_init

pip install -r requirements.txt
python3 init_db.py
```

**Run everything**
From project root run:

```bash
docker compose up -d
```
(-d isn't necessary, but it's cleaner)
## Services

### List

A list of services in docker compose, and what they do:
  - **etcd:** for KMs db
  - **minio:** for KMs db
  - **standalone:** for KMs db
  - **redis:** a redis queue that KM uses
  - **rqworker:** for KM (it loads data from redis to vec)
  - **data-api:** API for loading data into the vectordb
  - **query-api:** API for vector database searches
  - **front-api:** API on the KM, to which frontend can connect to
  - **rag-service:** API on RAG for Frontend
  - **frontend:** the website

Their ports are configured inside of the .env or .env.example files.

### Run only select services
```bash
docker compose up -d [service name 1] [service name 2]...
```
