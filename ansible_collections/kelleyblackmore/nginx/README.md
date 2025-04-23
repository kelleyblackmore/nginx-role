# Ansible Collection - kelleyblackmore.nginx

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-kelleyblackmore.nginx-blue.svg)](https://galaxy.ansible.com/kelleyblackmore/nginx)
[![CI](https://github.com/kelleyblackmore/nginx/actions/workflows/ansible-test.yml/badge.svg)](https://github.com/kelleyblackmore/nginx/actions/workflows/ansible-test.yml)

This Ansible collection provides roles for managing Nginx installations across different Linux distributions. It allows for consistent installation and upgrading of Nginx servers in your infrastructure.

## Included Content

### Roles

- `kelleyblackmore.nginx.install` - Installs and configures Nginx
- `kelleyblackmore.nginx.upgrade` - Safely upgrades an existing Nginx installation

### Playbooks

- `install_nginx.yml` - Example playbook for installing Nginx
- `upgrade_nginx.yml` - Example playbook for upgrading Nginx

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
