# Ansible playbooks

Highly reusable `Ansible` automation playbooks.

Tested with production servers and personal laptops / computers.

*No configuration steps are needed* in order to start using this software.

# What is Ansible?

`Ansible` is servers/computers automation system which saves your day from repeatable tasks.

It is useful even if you do not have number of servers/computers to administrate.

This repo gives you ability to reuse already created playbooks, extend and use for repeatable installation and configuration processes.

# How to start?

You need two things:

- Install `Ansible` on your computer. Nothing to install on servers.
- Learn how to execute playbooks.

Both explained below.

# Installing Ansible

You can install it with:

    $ sudo apt-get install ansible   # if you are on Ubuntu
    $ sudo aptitude install ansible  # if you are on Debian
    $ sudo yum install ansible       # if you are on Centos
    $ sudo dnf install ansible       # if you are on Fedora
    $ sudo brew install ansible      # if you are rich

# Running with Ansible

Assuming you have servers listed:

```bash
$ cat private/hosts.ini
server.one.com ansible_host=123.123.123.123
server.two.com ansible_user=deployment
```

Check uptime for all servers you have:

    ansible all -m command -a uptime

Limit your command to only some hosts:

    ansible-playbook playbooks/docker.yml --limit "server.one.com"

# Playbooks included

| File name          | Description                                                                     |
|--------------------|---------------------------------------------------------------------------------|
| python.yml         | Install Python 2.7 for Ansible compatibility on recent Ubuntu servers.         |
| locales.yml        | Install default locale to fix terminal from warnings                            |
| upgrade.yml        | Upgrade server with dist-upgrade, disk space checks, kernel cleanup, and reboot detection. |
| apache.yml         | Install apache; configure to support PHP, Ruby and Python projects.             |
| dotfiles.yml       | Install dotfiles (see ReekenX/dotfiles repo) with highly reusable configs.      |
| monitoring.yml     | Install packages for networking and CPU usage monitoring.                       |
| development.yml    | Install packages usually used in by engineers (git, rg, neovim, etc.)           |
| ruby_dev.yml       | Install packages every Ruby developer uses.                                     |
| python_dev.yml     | Install packages every Python developer uses.                                   |
| php_dev.yml        | Install packages every PHP developer uses.                                      |
| javascript_dev.yml | Install packages every JavaScript developer uses. Not finished yet.             |
| docker.yml         | Install Docker Engine from official repository with compose and buildx plugins. |
| firewall.yml       | Install and configure UFW firewall with Docker compatibility. HTTP/HTTPS/SSH rate-limited access. |
| pil.yml            | Install and configure Python Imaging library (PIL).                             |
| apport_errors.yml  | Disable apport which gives modal about GUI errors.                              |
| backups.yml        | Daily cron-based backups to /var/backups. Includes custom conf for every machine. |
| nagios-nrpe.yml    | NRPE server configuration, setup and plugins install.                           |

# Contribution

I love receiving PRs. File new branch, change / add something and leave me a note.

Leave your feedback, suggestions, PRs: https://github.com/ReekenX/ansible-playbooks/issues
