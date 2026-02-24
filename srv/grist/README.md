## S3 setup

The Grist bucket has to be created manually:
```
root@grist:/srv/grist# docker exec -it versitygw /bin/ash
versitygw admin create-user -a grist -s REDACTED -r user
versitygw admin create-bucket -o grist --bucket grist
```

Enable versioning for the bucket:

```bash
docker compose run --rm -it s3cmd --configure
docker compose run --rm --remove-orphans s3cmd setversioning s3://grist enable
```