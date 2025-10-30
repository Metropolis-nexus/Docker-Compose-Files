# Postgres Optimizations

Adjust `synapse-postgres/postgres.conf` to include these optimizations:

```
# https://vadosware.io/post/everything-ive-seen-on-optimizing-postgres-on-zfs-on-linux/
# https://www.percona.com/sites/default/files/presentations/pg-Performance-Tuning.pdf

shared_buffers = 6GB
work_mem = 1GB
maintenance_work_mem = 1GB
effective_io_concurrency = 100
max_worker_processes = 12
max_parallel_workers = 12
max_parallel_workers_per_gather = 3
max_parallel_maintenance_workers = 3
```

If running directly on ZFS, also include these optimizations:

```
# https://vadosware.io/post/everything-ive-seen-on-optimizing-postgres-on-zfs-on-linux/

full_page_writes = off
wal_init_zero = off
wal_recycle = off
effective_cache_size = 32GB
```
