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
