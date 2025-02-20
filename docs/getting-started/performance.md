# Performance Tips

## MariaDB ##

The [InnoDB buffer pool](https://mariadb.com/kb/en/innodb-buffer-pool/) serves as a cache for data and indexes.
It is a key component for optimizing MariaDB performance. Its size should be as large as possible to keep frequently
used data in memory and reduce disk I/O - typically the biggest bottleneck.

Our [docker-compose.yml examples](https://dl.photoprism.app/docker/) have a default buffer pool size between
128 MB and 256 MB, depending on the platform. You can change it using the `--innodb-buffer-pool-size` parameter
(`M` means Megabyte, `G` stands for Gigabyte). If your server has enough memory, we recommend increasing the size to 1 GB:

```yaml
services:
  mariadb:
    command: mysqld --innodb-buffer-pool-size=1G ...
```

## Storage ##

Local Solid-State Drives (SSDs) are [best for databases](https://mariadb.com/de/resources/blog/how-to-tune-mariadb-write-performance/)
of any kind:

- Database performance extremely benefits from high throughput which HDDs can't provide
- SSDs have more predictable performance and can handle more concurrent requests
- Due to the HDD seek time, HDDs only support 5% of the reads per second of SSDs
- The cost savings from using slow hard disks are minimal

Switching to SSDs makes a big difference, especially for write operations and when the read cache is not
big enough or can't be used.

Never store database files on an unreliable device such as a USB flash drive, an SD card, or a shared network folder.

## Server CPU ##

Last but not least, performance can be limited by your server CPU. While consumer NAS devices get faster
with each generation, their hardware is optimized for low power consumption.

[Benchmarks](https://www.google.com/search?q=cpu+benchmarks) prove that even 8-year-old standard desktop
CPUs are often many times faster. If you've tried everything else, then only moving your instance to a more
powerful server may help.
