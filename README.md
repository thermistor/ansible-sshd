# Ansible role for sshd

The `sshd_config` file is based on what shipped with Ubuntu xenial 16.04 LTS.

## Example playbook

Configures /etc/ssh/sshd_config. Defaults are secure except it uses port 22.

    - role: sshd

Here would be with the addition of an obscure port:

    - role: sshd
      sshd_port: 9999

Here is example usage to allow some accounts to use sftp only, see also the ([sftponly_user](htps://github.com/thermistor/thermistor-ansible-sftponly_user) role).

    - role: sshd
      sshd_port: 9999
      sshd_sftp_only_enabled: yes
      sshd_password_authentication: 'yes'
      sshd_permit_root_login: 'no'
      tags:
        - sshd

Note that by default `sshd_sftp_enabled` is set to `no`. So the following must be added
to your `ansible.cfg`.

    [ssh_connection]
    scp_if_ssh = True

## License

MIT

