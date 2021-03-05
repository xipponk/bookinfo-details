# Bookinfo Details Service

Rating service has been developed on Ruby

## How to run with Docker

```bash
# Build Docker Image for details service
docker build -t details .

# Run MongoDB with initial data in database
docker run -d --name mongodb -p 27017:27017 -v $(pwd)/databases:/docker-entrypoint-initdb.d bitnami/mongodb:4.4.4-debian-10-r5

# Run detils service on port 8080
docker run -d --name details -p 8080:8080 --link mongodb:mongodb -e SERVICE_VERSION=v2 -e 'MONGO_DB_URL=mongodb://mongodb:27017/details' details
```

* Test with path `/details/1` and `/health`
