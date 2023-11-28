# redis

### install on Ubuntu

```bash
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

sudo apt-get update
sudo apt-get install redis
```

### RDB == snapshotting

```bash
save 3600 1 1800 10 300 10000
```
* After 3600 seconds (an hour) if at least 1 change was performed
* After 1800 seconds (a half hour) if least 10 changes were performed
* After 300 seconds (5 minutes) if least 10000 changes were performed

### limit clients and connections

```bash
maxclients 10000
```

```bash
sysctl -w net.core.somaxconn=65536
add `net.core.somaxconn=65536` to the /etc/sysctl.conf
```

### How to Choose Eviction Policies on Redis Database Clusters

[link](https://docs.digitalocean.com/products/databases/redis/how-to/choose-eviction-policies/)

```bash
maxmemory-policy allkeys-lru
```

### benchmark and latency

```bash
redis-benchmark -c 100 -n 200000 -q

PING_INLINE: 38424.59 requests per second, p50=1.215 msec
PING_MBULK: 36186.00 requests per second, p50=1.231 msec
SET: 35771.78 requests per second, p50=1.271 msec
GET: 37921.88 requests per second, p50=1.199 msec
INCR: 23250.41 requests per second, p50=1.399 msec
LPUSH: 30075.19 requests per second, p50=1.399 msec
RPUSH: 28571.43 requests per second, p50=1.439 msec
LPOP: 24645.72 requests per second, p50=1.423 msec
RPOP: 17167.38 requests per second, p50=2.295 msec
SADD: 27382.26 requests per second, p50=1.343 msec
HSET: 21296.99 requests per second, p50=1.655 msec
SPOP: 15957.87 requests per second, p50=1.823 msec
ZADD: 27483.85 requests per second, p50=1.367 msec
ZPOPMIN: 31715.82 requests per second, p50=1.271 msec
LPUSH (needed to benchmark LRANGE): 36503.01 requests per second, p50=1.263 msec
LRANGE_100 (first 100 elements): 14705.88 requests per second, p50=2.815 msec
LRANGE_300 (first 300 elements): 6651.37 requests per second, p50=7.175 msec
LRANGE_500 (first 500 elements): 5724.26 requests per second, p50=8.751 msec
LRANGE_600 (first 600 elements): 4676.17 requests per second, p50=10.407 msec
MSET (10 keys): 21609.94 requests per second, p50=1.943 msec
```

```bash
root@fhmu2ifoclal93og9tuj:~# redis-cli --intrinsic-latency 100
Max latency so far: 1 microseconds.
Max latency so far: 12 microseconds.
Max latency so far: 20 microseconds.
Max latency so far: 23 microseconds.
Max latency so far: 27 microseconds.
Max latency so far: 28 microseconds.
Max latency so far: 45 microseconds.
Max latency so far: 83 microseconds.
Max latency so far: 628 microseconds.
Max latency so far: 4182 microseconds.
Max latency so far: 8421 microseconds.
Max latency so far: 12010 microseconds.
Max latency so far: 18453 microseconds.
Max latency so far: 20779 microseconds.
Max latency so far: 27690 microseconds.
Max latency so far: 28921 microseconds.
Max latency so far: 82701 microseconds.

1057912900 total runs (avg latency: 0.0945 microseconds / 94.53 nanoseconds per run).
Worst run took 874905x longer than the average latency.
```

## english

`I'm struggling to find documentation on this beyond what's available through the tool's own help document.`
