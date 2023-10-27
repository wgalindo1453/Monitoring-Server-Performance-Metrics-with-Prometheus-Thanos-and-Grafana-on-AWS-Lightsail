![Your Top Image Here](LightSail.png)

# Monitoring Server Performance Metrics with Prometheus, Thanos, and Grafana on AWS Lightsail

## Introduction

This repository provides a detailed setup for monitoring performance metrics on a single AWS Lightsail instance. Instead of leveraging Prometheus and Thanos in a traditional multi-node cluster architecture, this setup utilizes both to monitor the performance metrics of the very Lightsail instance they're running on. With the addition of Grafana, this setup offers a comprehensive solution to collect, store, and visualize server metrics, especially when running performance benchmarks via cron jobs.

## Key Goals

1. **Self-Monitoring**: The AWS Lightsail instance monitors its own CPU, Disk, Memory, and Latency metrics. This is especially crucial given the cron jobs executing performance benchmarks.
2. **Simplified Architecture**: While Prometheus and Thanos are typically used in multi-node cluster architectures, this setup simplifies things, running both tools as individual services on a single instance.
3. **Long-term Storage with S3**: All collected metrics are stored in an S3 bucket, ensuring data durability and long-term availability.
4. **Data Visualization with Grafana**: Metrics can be queried and visualized in a user-friendly manner using Grafana, which is also set up as a service on the Lightsail instance.

## Architecture Overview

1. **Node Exporter**: Gathers the server's performance metrics.
2. **Prometheus**: Main monitoring tool, scraping metrics from NodeExporter.
3. **Thanos Sidecar**: Sits alongside Prometheus, forwarding metrics to the S3 bucket.
4. **Thanos Store**: Retrieves metrics from the S3 bucket, making them queryable.
5. **Thanos Query**: Merges data from Prometheus and Thanos Store to offer a unified query interface.
6. **S3 Bucket**: Acts as the long-term storage solution for all performance metrics.
7. **Grafana**: Fetches data from Thanos Query, enabling detailed dashboard visualizations.

## Setup Instructions

1. Create an AWS account and set up a Lightsail instance with Ubuntu. [Instructions](https://aws.amazon.com/blogs/opensource/improving-ha-and-long-term-storage-for-prometheus-using-thanos-on-eks-with-s3/)
2. Install and configure Prometheus on Ubuntu. [Instructions](https://www.cherryservers.com/blog/install-prometheus-ubuntu)
3. Refer to the official Thanos documentation for detailed setup and configurations. [Thanos Documentation](https://thanos.io/)

## Conclusion

This setup offers a unique approach to performance monitoring on a single AWS Lightsail instance, leveraging the power of Prometheus, Thanos, and Grafana. Whether you're running scheduled performance benchmarks or simply want a detailed view of your server's health, this solution provides a compact yet powerful monitoring stack.

![Your Bottom Image Here](path/to/bottom/grafana.png)
