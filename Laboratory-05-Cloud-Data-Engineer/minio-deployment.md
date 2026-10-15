# MinIO Deployment Documentation

## 1. Overview
MinIO is an S3-compatible object storage server. In this activity, Docker is used to run MinIO and access its web console.

## 2. Docker Deployment Command

```bash
docker run -d -p 9000:9000 -p 9001:9001 --name minio-server \
-e "MINIO_ROOT_USER=cloudadmin" \
-e "MINIO_ROOT_PASSWORD=CloudNova2026!" \
minio/minio server /data --console-address ":9001"
```

## 3. Port Configuration
- Port 9000: MinIO API.
- Port 9001: MinIO Web Console.

The web console is accessed through port 9001 using the port-forwarding feature in the KillerCoda Playground.

## 4. Bucket Configuration
- Bucket name: `client-photos`

The bucket is intended to store sample photos and other uploaded objects for the client application.

## 5. Environment Variables
- `MINIO_ROOT_USER`: Sets the administrator username to `cloudadmin`.
- `MINIO_ROOT_PASSWORD`: Sets the administrator password used to sign in to the MinIO console.

The `-e` flag passes environment variables into the Docker container so MinIO can use the configured credentials.

## 6. Verification
After running the command, verify that the container is running and access the MinIO Web Console through port 9001. Create the `client-photos` bucket and upload a sample file.

## 7. Evidence
Screenshots of the running container and the uploaded object will be saved in the `screenshots` folder after completing those steps.
