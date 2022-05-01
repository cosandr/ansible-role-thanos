# Ansible role for Thanos

Deploys [Thanos](https://thanos.io/) on a single Linux host.

## Variables

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `thanos_version` | latest | Set version, without "v" prefix |
| `thanos_user` | thanos | User to run thanos processes as, needs access to tsdb dir |
| `thanos_group` | thanos | Group to run thanos processes as |
| `thanos_log_level` | warn | Logging level |
| `thanos_binary_install_dir` | /usr/local/bin | Path where `thanos` is installed in |
| `thanos_conf_dir` | /etc/thanos | Path where configs are written |
| `thanos_work_dir` | /var/lib/thanos | Path where compact and store keep temporary files, should be relatively large |
| `thanos_objstore_config` | `{{ thanos_conf_dir }}/bucket_config.yml` | Path where bucket config is written |
| `thanos_s3_config` | {} | See [Thanos documentation](https://thanos.io/tip/thanos/storage.md/) |
| `sidecar_services` | [] | List of services required by sidecar service |
| `sidecar_http_address` | 127.0.0.1:19191 | Sidecar HTTP listen address |
| `sidecar_grpc_address` | 127.0.0.1:10901 | Sidecar gRPC listen address |
| `sidecar_prom_url` | http://localhost:9090 | Prometheus URL |
| `sidecar_tsdb_path` | /var/lib/prometheus | Prometheus TSDB path, must be RW for the thanos user |
| `store_services` | [] | List of services required by store service |
| `store_http_address` | 127.0.0.1:19192 | Store HTTP listen address |
| `store_grpc_address` | 127.0.0.1:10902 | Store gRPC listen address |
| `compact_services` | [] | List of services required by compact service |
| `compact_http_address` | 127.0.0.1:19193 | Compact HTTP listen address |
| `compact_retention_raw` | 14d | Compact retention for raw metrics |
| `compact_retention_5m` | 30d | Compact retention for 5m downsampled metrics |
| `compact_retention_1h` | 90d | Compact retention for 1h downsampled metrics |
| `query_services` | ["thanos-sidecar.service", "thanos-store.service"] | List of services required by query service |
| `query_http_address` | 127.0.0.1:19194 | Query HTTP listen address |
| `query_grpc_address` | 127.0.0.1:10904 | Query gRPC listen address |
| `query_endpoints` | [\<sidecar grpc\>, \<store grpc\>] | List of Thanos endpoints read by Query |

## Author

Andrei Costescu
