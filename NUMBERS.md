## Caching
- **Key Metrics:** ~1 millisecond latency, 100k+ operations/second, Memory-bound (up to 1TB)
- **Scale Triggers:** Hit rate < 80%, Latency > 1ms, Memory usage > 80%, Cache churn/thrashing

## Databases
- **Key Metrics:** Up to 50k transactions/second, Sub-5ms read latency (cached), 64 TiB+ storage capacity
- **Scale Triggers:** Write throughput > 10k TPS, Read latency > 5ms uncached, Geographic distribution needs

## App Servers
- **Key Metrics:** 100k+ concurrent connections, 8-64 cores @ 2-4 GHz, 64-512GB RAM standard, up to 2TB
- **Scale Triggers:** CPU > 70% utilization, Response latency > SLA, Connections near 100k/instance, Memory > 80%

## Message Queues
- **Key Metrics:** Up to 1 million msgs/sec per broker, Sub-5ms end-to-end latency, Up to 50TB storage
- **Scale Triggers:** Throughput near 800k msgs/sec, Partition count ~200k per cluster, Growing consumer lag
