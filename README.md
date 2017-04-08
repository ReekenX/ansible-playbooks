# Ansible playbooks

Highly reusable `Ansible` automation playbooks.

Can be used with servers and personal computers.

No configuration is needed in order to use this software.

# You know Ansible, right?

`Ansible` is servers/computer automation system which saves your day from repeatable tasks.

It is useful even if you do not have number of servers/computers to administrate.

This repo gives you ability to reuse already created playbooks, extend those and use for repeatable installation and configuration processes.

# How it works?

Mainly you need two things:

- Install `Ansible` on your computer. Nothing to install on servers.
- Learn how to execute playbooks.

Read next about those.

# Installing Ansible

You can install it with:

    $ sudo apt-get install ansible   # if you are on Ubuntu
    $ sudo aptitude install ansible  # if you are on Debian
    $ sudo yum install ansible       # if you are on Centos
    $ sudo dnf install ansible       # if you are on Fedora

# Running playbooks

There are many playbooks in this repo. Playbook is domain specific configuration file (the one which ends in `.yml` extension) which you can run on single/multiple machines.

Let's say I am starting with new dedicated server. Obviously, I need my personal home files there. Here is what I would run:

    $ ansible-playbook -i 12.34.54.78, dotfiles.yml

Explanation:

- -i IP, - apply playbook to single server only (comman is a must!)
- dotfiles.yml - playbook to run (all playbooks docummented below)

# Screenshot

Picture or didn't happened? Here:

![Playing with Ansible playbook on Xterm](screenshots/running_on_single_machine.png?raw=true "Playing with Ansible playbook on Xterm")

# Playbooks included

| File name          | Description                                                                   |
|--------------------|-------------------------------------------------------------------------------|
| locales.yml        | Install all locales on the server (useful when having multilingual projects)  |
| apache.yml         | Install apache; configure to support PHP, Ruby and Python projects.           |
| dotfiles.yml       | Install dotfiles (see ReekenX/dotfiles repo) with highly reusable configs.    |
| monitoring.yml     | Install packages for networking and cpu usage monitoring.                     |
| development.yml    | Install packages developer will use every day.                                |
| ruby_dev.yml       | Install packages every Ruby developer uses.                                   |
| python_dev.yml     | Install packages every Python developer uses.                                 |
| php_dev.yml        | Install packages every PHP developer uses.                                    |
| docker.yml         | Install and configure Docker. Not finished yet.                               |
| docker-compose.yml | Install and configure docker-compose.                                         |
| pil.yml            | Install and configure Python Imaging library (PIL).                           |

# Contribution

Your feedback or PR's are very welcome! I normally reply in hours, max - next day.

You can comment things on GitHub issue tracker:  https://github.com/ReekenX/ansible-playbooks/issues
