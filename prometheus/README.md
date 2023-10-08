# Prometheus

A brief description of setting up Prometheus and Node Exporter on an Ubuntu server.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

### Usage
1. Create a ssh key, copy the ssh key to the remote hosts
```shell
ssh-copy-id -i ~/.ssh/id_rsa.pub <remote-user>@<ip-address>
```
2. Create an inventory file
```shell
[webservers]
<ip-address>
```
3. Run the playbook
```shell
ansible-playbook -i hosts prometheus.yaml
```
```shell
ansible-playbook -i hosts node-exporter.yaml
```

### PromQL
1. Number of running containers (when using docker compose)
```
count(container_memory_usage_bytes{container_label_com_docker_compose_service != ""})
```
2. Average CPU utilization, expressed as a percentage
```
100 - (avg by (instance) (irate(node_cpu_seconds_total{mode="idle"}[24h])) * 100)
```
3. Average Memory utilization, expressed as a percentage
```
100 - (avg_over_time(node_memory_MemAvailable_bytes[24h]) / avg_over_time(node_memory_MemTotal_bytes[24h]) * 100)
```

