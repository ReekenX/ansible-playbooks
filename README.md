# Ansible playbooks

Highly reusable `Ansible` automation playbooks.

Tested with production servers and personal laptops / computers.

*No configuration steps are needed* in order to start using this software.

# In action

I recently got notified from Nagios that one of my servers has security package updates. Here is how I have upgraded and tested it later:

![Upgrading servers with Ansible](https://www.jarmalavicius.lt/assets/ansible_serveriu_atnaujinimui.gif)

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
    $ sudo brew install ansible      # if you are in Starbucks

# Running playbooks

There are many playbooks in this repo (see `playbooks/` folder).

Playbook is domain specific configuration file (the one which ends in `.yml` extension) which you can run on single/multiple machines.

Let's say I am starting with new dedicated server. Obviously, I need my personal home files there. Here is what I would run:

    $ ansible-playbook -i 12.34.54.78, dotfiles.yml

Explanation:

- -i IP, - apply playbook to single server only (comman is a must!)
- dotfiles.yml - playbook to run (all playbooks docummented below)

# Playbooks included

| File name          | Description                                                                     |
|--------------------|---------------------------------------------------------------------------------|
| locales.yml        | Install all locales on the server (useful when having multilingual projects)    |
| apache.yml         | Install apache; configure to support PHP, Ruby and Python projects.             |
| dotfiles.yml       | Install dotfiles (see ReekenX/dotfiles repo) with highly reusable configs.      |
| monitoring.yml     | Install packages for networking and cpu usage monitoring.                       |
| development.yml    | Install packages developer will use every day.                                  |
| ruby_dev.yml       | Install packages every Ruby developer uses.                                     |
| python_dev.yml     | Install packages every Python developer uses.                                   |
| php_dev.yml        | Install packages every PHP developer uses.                                      |
| javascript_dev.yml | Install packages every JavaScript developer uses. Not finished yet.             |
| docker.yml         | Install and configure Docker. Not finished yet.                                 |
| docker-compose.yml | Install and configure docker-compose.                                           |
| pil.yml            | Install and configure Python Imaging library (PIL).                             |
| apport_errors.yml  | Disable apport which gives modal about GUI errors.                              |
| backups.yml        | Daily backups to Dropbox automatically. Includes custom conf for every machine. |
| server_upgrade.yml | Upgrade server software.                                                        |

# Contribution

I love PR! I normally reply in hours, max - next day.

Leave your feedback, suggestions, PRs:  https://github.com/ReekenX/ansible-playbooks/issues
