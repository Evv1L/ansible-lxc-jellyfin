Jellyfin Unprivileged LXC
=========

Role for installing Jellyfin on Unprivileged LXC

Requirements
------------

First you must create an Unprivileged LXC container with certain requirements:

1. Use Debian 12 an OS template;
2. (Optional) Create a subvolume to store Jellyfin's data, cache, logs etc.

Role Variables
--------------

(Optional) Mountpoint for Jellyfin data, config, log and cache.
Useful for storing Jellyfin data outside LXC container, like SMB share or ZFS subvolume.

`jellyfin_data_mountpoint: /mnt/jellyfin`

(Optional) Set `jellyfin` user uid

`jellyfin_user_uid: 103`

Dependencies
------------

The role itself doesn't have any Ansible Galaxy dependencies.

Example Playbook
----------------

Playbook with defined mountpoint:

    - hosts: jellyfin-lxc
      gather_facts: true
      become: true

      roles:
        - role: ansible-lxc-jellyfin
          vars:
            jellyfin_data_mountpoint: /mnt/jellyfin

TODO
----

- Ubuntu LXC support
- Auto enable hardware acceleration for Intel iGPU
