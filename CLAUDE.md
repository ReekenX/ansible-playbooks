# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a collection of highly reusable Ansible automation playbooks for server and computer configuration. The playbooks are tested with production servers and personal machines, requiring no configuration to start using.

## Key Architecture Concepts

### Playbook Organization

All playbooks are located in `playbooks/` directory and target `hosts: all` by default. They are designed to be:

- Self-contained and independently executable
- Idempotent (safe to run multiple times)
- Apt-based (Ubuntu/Debian focused)

## Common Commands

### Running Playbooks

Execute a playbook with host limiting:

```bash
ansible-playbook playbooks/docker.yml --limit "server.example.org"
```

Check uptime across all servers:

```bash
ansible all -m command -a uptime
```

## Development Workflow

### Creating New Playbooks

- Place new playbooks in `playbooks/` directory
- Use `.yml` extension
- Start with standard structure:

  ```yaml
  ---
  # Description comment

  - hosts: all
    tasks:
    - name: Task description
      apt:
        update_cache: yes
        pkg:
          - package-name
  ```

### Common Playbook Patterns

**Package installation:**

```yaml
- name: Install packages
  apt:
    update_cache: yes
    pkg:
      - package1
      - package2
```

**File copying:**

```yaml
- name: Copy configuration
  ansible.builtin.copy:
    src: files/filename
    dest: ~/destination
```

**Using ansible_fqdn for host-specific files:**

```yaml
- name: Install per-host script
  copy: src=files/{{ ansible_fqdn }}/script-name dest=/usr/sbin/script-name
```

### Playbook Categories

**System Administration:**

- `upgrade.yml` - System package upgrades with kernel cleanup

**Security:**

- `security_updates.yml` - Automatic security updates via unattended-upgrades
- `firewall.yml` - UFW firewall with Docker compatibility, rate-limited SSH/HTTP/HTTPS access
- `lock.yml` - Lock down server to SSH-only access with rate limiting

**Development Environments:**

- `development.yml` - Dev and monitoring tools (git, ripgrep, neovim, fzy, tree, curl, htop, iftop, iotop, nmap, whois)

**Server Services:**

- `docker.yml` - Docker Engine installation (removes old versions, adds official repository)

**User Configuration:**

- `dotfiles.yml` - Install dotfiles from ReekenX/dotfiles repository
- `backups.yml` - Daily cron-based backups to /var/backups, creates backup-sync user
- `motd.yml` - Clean Ubuntu MOTD, add figlet banner (configurable via `motd_banner`) and needrestart notifications

**Libraries:**

- `python.yml` - Python 2.7 for Ansible compatibility

## Important Notes

- Playbooks assume apt package manager (Debian/Ubuntu)
- Most playbooks use `update_cache: yes` to refresh package lists
- The `upgrade.yml` playbook includes kernel package purging logic
