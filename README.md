Ansible role: AMP Collector
===========================

Install and configure amppki and nntsc.

Role Variables
--------------

```
ENTRY POINT: main - Install and configure amppki and nntsc

OPTIONS (= is mandatory):

- amp_apt_key_fingerprint
        Fingerprint for amp apt signing key
        [Default: (null)]
        type: str

= ampname
        Domain name of the amppki server

        type: str

- amppki_acl_networks
        List of networks permitted to have access to amppki
        [Default: (null)]
        elements: str
        type: list

- amppki_cacertfile
        Path to CA certificate file
        [Default: /etc/amppki/cacert.pem]
        type: str

- amppki_certfile
        Path to server certificate file
        [Default: /etc/amppki/server/amppki-cert.pem]
        type: str

- amppki_keyfile
        Path to server key file
        [Default: /etc/amppki/server/amppki-key.pem]
        type: str

- bintray_amp_apt_key_fingerprint
        Fingerprint for apt signing key for old bintray amp repo
        [Default: (null)]
        type: str

- nntsc_config
        NNSTC configuration
        [Default: (null)]
        elements: dict
        type: list

        OPTIONS:

        = option
            Name of the option

            type: str

        = section
            Name of the section

            type: str

        = value
            Value for the option

            type: str

- old_amp_apt_key_fingerprint
        Fingerprint for apt signing key for old amp repo
        [Default: (null)]
        type: str
```

Installation
------------

This role can either be installed manually with the ansible-galaxy CLI tool:

    ansible-galaxy install git+https://github.com/wandansible/amp.collector,main,wandansible.amp.collector
     
Or, by adding the following to `requirements.yml`:

    - name: wandansible.amp.collector
      src: https://github.com/wandansible/amp.collector

Roles listed in `requirements.yml` can be installed with the following ansible-galaxy command:

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

    - hosts: amp_collectors
      roles:
         - role: wandansible.amp.collector
           become: true
           vars:
             ampname: amp.example.org
