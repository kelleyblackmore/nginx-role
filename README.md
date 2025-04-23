# Ansible Nginx Collection

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-kelleyblackmore.nginx-blue.svg)](https://galaxy.ansible.com/kelleyblackmore/nginx)
[![CI](https://github.com/kelleyblackmore/nginx/actions/workflows/ansible-test.yml/badge.svg)](https://github.com/kelleyblackmore/nginx/actions/workflows/ansible-test.yml)

This repository contains the `kelleyblackmore.nginx` Ansible collection, which provides roles and playbooks for installing, configuring, and upgrading Nginx across different Linux distributions.

## Collection Contents

### Roles

- **install**: Installs and configures Nginx with customizable parameters
- **upgrade**: Safely upgrades an existing Nginx installation with backup and validation

### Playbooks

- **install_nginx.yml**: Example playbook for installing Nginx
- **upgrade_nginx.yml**: Example playbook for upgrading Nginx

## Requirements

- Ansible 2.9 or newer
- Python 3.6 or newer

## Supported Platforms

- Debian/Ubuntu
- RHEL/CentOS/Fedora
- Amazon Linux

## Installation

### Using ansible-galaxy (recommended)

```bash
ansible-galaxy collection install kelleyblackmore.nginx
```

### Using git

```bash
git clone https://github.com/kelleyblackmore/nginx.git
cd nginx
ansible-galaxy collection build ansible_collections/kelleyblackmore/nginx
ansible-galaxy collection install kelleyblackmore-nginx-*.tar.gz
```

## Usage

### Install Nginx

```yaml
---
- name: Install Nginx
  hosts: web_servers
  become: true
  collections:
    - kelleyblackmore.nginx
  
  vars:
    nginx_version: "stable"
    nginx_http_port: 80
    nginx_ssl_enabled: true
    
  roles:
    - role: kelleyblackmore.nginx.install
```

### Upgrade Nginx

```yaml
---
- name: Upgrade Nginx
  hosts: web_servers
  become: true
  collections:
    - kelleyblackmore.nginx
  
  vars:
    nginx_upgrade_version: "latest"
    nginx_upgrade_backup: true
    nginx_upgrade_validate_config: true
    
  roles:
    - role: kelleyblackmore.nginx.upgrade
```

## Role Variables

### kelleyblackmore.nginx.install

| Variable | Description | Default |
|----------|-------------|---------|
| `nginx_version` | Version to install (stable/mainline) | `stable` |
| `nginx_http_port` | HTTP port | `80` |
| `nginx_https_port` | HTTPS port | `443` |
| `nginx_ssl_enabled` | Enable SSL | `false` |
| `nginx_worker_processes` | Worker processes | `auto` |
| `nginx_worker_connections` | Worker connections | `1024` |
| `nginx_client_max_body_size` | Client max body size | `64m` |

### kelleyblackmore.nginx.upgrade

| Variable | Description | Default |
|----------|-------------|---------|
| `nginx_upgrade_version` | Version to upgrade to (stable/mainline/latest) | `latest` |
| `nginx_upgrade_backup` | Create backup before upgrade | `true` |
| `nginx_upgrade_backup_path` | Backup path | `/var/backups/nginx` |
| `nginx_upgrade_max_backups` | Number of backups to keep | `5` |
| `nginx_upgrade_validate_config` | Validate config after upgrade | `true` |
| `nginx_upgrade_package_state` | Package state | `latest` |
| `nginx_upgrade_restart` | Restart Nginx after upgrade | `true` |

## Development

### Testing

This collection uses Molecule for testing:

```bash
cd ansible_collections/kelleyblackmore/nginx
molecule test
```

To test on a specific platform:

```bash
MOLECULE_DISTRO=ubuntu2004 molecule test
```

### Linting

To check code quality:

```bash
ansible-lint
yamllint .
```

## License

MIT

## Author

Kelley Blackmore

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin feature-name`
5. Submit a Pull Request