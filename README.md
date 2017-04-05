# Ansible playbooks

Highly reusable `Ansible` automation playbooks.

`Ansible` is servers/computer automation system which makes saves your day from repeatable tasks. It is useful even if you do not have number of servers/computers to administrate.

This repo gives you ability to reuse already created playbooks, extend those and use for repeatable installation/configuration processes.

# How it works?

Mainly you need two things:

- Install `Ansible` on your computer. On servers - this NOT needed.
- Define your computers/servers once in configuration file.
- Learn how to run playbooks.

All steps are very easy. Read next for tips.

# Installing Ansible

You can install it with:

    $ sudo apt-get install ansible  # if you are on Ubuntu
    $ sudo aptitude install ansible # if you are on Debian
    $ sudo yum install ansible      # if you are on CentOs

# Configure

Craete `hosts` file with following syntax:

    [all]
    localhost
    server.example.org
    server.example.net
    example.server.net

Obviously - put all your computers/servers/machines in this one big list.

Keep this list private.

# Running playbooks

There are many playbooks in this repo. Playbook is domain specific configuration file which you can run on single/multiple machines.

Here is how I quickly install all locales on one of my machines:

    $ ansible-playbook locales.yml -i hosts -l server.example.org,

![Playing with Ansible playbook on Xterm](screenshots/running_on_single_machine.png?raw=true "Playing with Ansible playbook on Xterm")

Explanation:

- locales.yml - is playbook file to run tasks from.
- -i hosts - read servers list from file created earlier.
- -l server.example.org, - apply playbook to single server only (comman is important!)

To run your playbook on all servers:

    $ ansible-playbook locales.yml -i hosts

# Playbooks included

| File name       | Description                                                                   |
|-----------------|-------------------------------------------------------------------------------|
| locales.yml     | Install all locales on the server (useful when having multilingual projects)  |
| apache.yml      | Install apache; configure to support PHP, Ruby and Python projects.           |
| dotfiles.yml    | Install dotfiles (see ReekenX/dotfiles repo) with highly reusable configs.    |
| monitoring.yml  | Install packages for networking and cpu usage monitoring.                     |
| development.yml | Install packages developer will use every day.                                |
| ruby_dev.yml    | Install packages every Ruby developer uses.                                   |

# Problems on Fedora

If you using Fedora servers, you will need manually install two packages:

    $ dnf install python
    $ dnf install python-dnf

And the rest will work just fine.

# Is Ansible > SaltStack?

No, not really.

Previously I have used `SaltStack` for automation but due to many reasons switched to `Ansible`.

I didn't liked very much couple of things in `SaltStack` which made whole deployment-automation unproductive:

- Poor results output.
- Too complex task dependencies management system.
- Master-slave communication (yes, I know such thing as `salt-ssh` exists).

My old `SaltStack` configurations are here: https://github.com/ReekenX/salt-configs

# Bugs

This project has no bugs.

But your feedback would be very valuable to me: https://github.com/ReekenX/ansible-playbooks/issues

I normally respond in less than a day. Or just e-mail me (see my profile for e-mail).
