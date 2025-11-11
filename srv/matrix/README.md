# Connectivity
ZenArmor, OPNsense's Unbound block lists, and Cloudflare Secure Gateway all have too many false positives for Synapse to work properly. Even when they correctly flag a domain as suspicious, it still causes federation issues and not really achieving anything security wise. As such, the Matrix stack needs to be on a VLAN without ZenArmor, and the OS needs to be setup with its own Unbound forwarding to `1.1.1.2` instead of the usual setup.

# crun
Add crun to `/etc/docker/daemon.json`:

```
        "crun": {
            "path": "/usr/sbin/crun"
        }
```

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
