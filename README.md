Digital Ocean
=============

Create a new droplet on Digital Ocean. If your droplet uses Ubuntu 16.04, it will also install and symlink Python 2.7 for you so
that the box has the requisite software installed to run further plays against the droplet.

Requirements
------------

This role requires that you have the `dopy` Python package installed. You can install this by running `requirements.txt` either on your base Python 2.7 install,
or through a virtualenv (recommended), as follows:

```
pip install -r requirements.txt
```

Role Variables
--------------

You should set the following variables in your playbooks to override defaults where necessary:

```yml
do_droplet_name: "{{ doname }}"         # pass in --extra-vars "doname=<something>" on the command line.
do_droplet_idempotency: true            # assign a unique name to the droplet.
do_droplet_size: 512mb                  # the size of the droplet.
do_droplet_image: ubuntu-16-04-x64      # the base OS image to be used.
do_droplet_region: fra1                 # the default region.
do_ssh_key_name: Primary                # the name of the SSH key assigned to your account.
do_api_token: 0                         # NB!!! your digital ocean api token.
do_droplet_private_net: no              # do not assign a private network interface (eth1) to this droplet.
```

The default user for SSH connections is `root`, so set an override for this, if applicable, by defining:

```yml
do_root_user: <someone>
```

Dependencies
------------

None

Example Playbook
----------------

You can pre-install the role by passing the following command:

    ansible-galaxy install xnoder.digitalocean

In order to use this role, do the following:

    ---
    - hosts: all
      roles:
        - { role: xnoder.digitalocean }

License
-------

MIT

Author Information
------------------

Created by Paul Stevens | [@xnoder](https://github.com/xnoder) | [xnode.co.za](https://xnode.co.za)
