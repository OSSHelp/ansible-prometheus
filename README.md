# prometheus

[![Build Status](https://drone.osshelp.io/api/badges/ansible/prometheus/status.svg)](https://drone.osshelp.io/ansible/prometheus)

Role for Prometheus installation and configuration.

## Usage

### Default installation

```yaml
    - role: prometheus
```

### Customized installation

```yaml
    - role: prometheus
      prometheus_service_name: prometheus-lts
      prometheus_user: prometheus-lts
      prometheus_dirs:
        config: /etc/prometheus-lts
        data: /var/lib/prometheus-lts
      prometheus_retention:
        time: 90d
        size: 10GB
      prometheus_global_params:
        scrape_interval: 60s
        evaluation_interval: 60s
      prometheus_listen: 0.0.0.0:9091
```

## Available parameters

| Param | Default | Description |
| -------- | -------- | -------- |
| `prometheus_setup` | `full` | Setup mode. See [OSSHelp KB article](https://oss.help/kb4895) |
| `prometheus_version` | `2.37.1` | Version to install. Select from [available releases](https://github.com/prometheus/prometheus/releases). |
| `prometheus_service_name` | `prometheus` | Name of systemd service. |
| `prometheus_user` | `prometheus` | Name of system user. |
| `prometheus_group` | `prometheus` | Name of group. |
| `prometheus_dirs.config` | `/etc/prometheus` | Path to directory with prometheus configuration. |
| `prometheus_dirs.data` | `/var/lib/prometheus` | Path to data directory |
| `prometheus_listen` | `0.0.0.0:9090` | Address on which prometheus will be listening. |
| `prometheus_alertmanager_config` | `[]` | Configuration responsible for pointing where alertmanagers are. This should be specified as list in yaml format. |
| `prometheus_external_url` | - | External address on which prometheus is available. Useful when behind reverse proxy. |
| `prometheus_retention.time` | `30d` | Data retention period |
| `prometheus_retention.size` | `0` | Data retention period by size. Supported: KB, MB, GB, TB, PB. Zero means no limit. |
| `prometheus_scrape_configs` | see [defaults](defaults/main.yml) | Prometheus scrape jobs provided in same format as in [official docs](https://prometheus.io/docs/prometheus/latest/configuration/configuration/#scrape_config) |
| `prometheus_global_params` | see [defaults](defaults/main.yml) | Global params, such as scrape/evaluation intervals. |

## FAQ

...

## Useful links

- [Official documentation](https://prometheus.io/docs/)
- [Available releases](https://github.com/prometheus/prometheus/releases)

## TODO

...

## License

GPL3

## Author

OSSHelp Team, see <https://oss.help>
