[![Build Status](https://travis-ci.org/wahidsadik/git-based-deploy.svg?branch=master)](https://travis-ci.org/wahidsadik/git-based-deploy)
[![GitHub version](https://badge.fury.io/gh/wahidsadik%2Fgit-based-deploy.svg)](https://badge.fury.io/gh/wahidsadik%2Fgit-based-deploy)

Role Name
=========

git-based-deploy: An Ansible role to create git-based deployment of a static website.

The role is available on Ansible Galaxy: [https://galaxy.ansible.com/wahidsadik/git-based-deploy/](https://galaxy.ansible.com/wahidsadik/git-based-deploy/).

To add this role from Ansible Galaxy, run: `ansible-galaxy install wahidsadik.git-based-deploy`.

To add this from your Ansible `requirements.yml`, add this to the file:

    src: wahidsadik.git-based-deploy

Requirements
------------

The `remote_user` used run this role should be able change permission of directories and files usually owned by `root`. Hence, you will probably need to `sudo` to successfully run use this role. See examples for more details.

Role Variables
--------------

The role defines the following variables in `defaults/main.yml`:

    www_root: /var/www
    repo_root: /var/repo
    www_user: deployer
    www_group: www-data

>Notes:
>
> - `www_user` **must belong** to `www_group` group.
> - `www_user` **should not be** `root` user for security reasons.

Users must pass the following parameters (i.e. variables):

- `website`. Values should be valid file/directory name on a Linux system.

Example values for `website`:

- example.com
- abc-def.org

Dependencies
------------

None

Example Playbook
----------------

Example 1: Simplest example with minimum variable passing

    - hosts: servers
      remote_user: root
      roles:
      - { role: wahidsadik.git-based-deploy, website: example.com }

 Example 2: With sudo and  minimum variable passing

    - hosts: servers
      remote_user: deployer
      become: true
      become_method: sudo
      roles:
      - { role: wahidsadik.git-based-deploy, website: example.com }

 Example 3: Overriding additional variables

    - hosts: servers
      remote_user: deployer
      become: true
      become_method: sudo
      roles:
      - { role: wahidsadik.git-based-deploy, website: example.com,  www_user: myuser, www_group: www}

License
-------

MIT

Author Information
------------------

Wahid Sadik

Repo: [https://github.com/wahidsadik/git-based-deploy](https://github.com/wahidsadik/git-based-deploy).
