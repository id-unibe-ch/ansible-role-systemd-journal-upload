# Ansible Role: systemd-journal-upload

An Ansible role that manages systemd-journal-upload. Currently the role has the following
features:

* Install systemd-journal-upload
* Configure `/etc/systemd/journal-upload.conf`
* Configure automatic service restart via a systemd drop-in override

## Requirements

No prerequisites necessary at the moment.

## Role Variables

Available variables are listed below, along with default values (see also `defaults/main.yml`):
<!-- 
**STYLE GUIDE:**
* All variables should start with the role name (e.g. `systemd_journal_upload_`)
* Variables that are private to the role and only important to people developing the role should be set in `vars/main.yml` and start with `__systemd_journal_upload_`
-->

<!-- Enter ALL mandatory variables into `tasks/check_mandatory_vars.yml` so their presence gets checked before each run -->
### systemd_journal_upload_url

URL of the remote host to upload journal to.

```yaml
systemd_journal_upload_url: 'https://server.domain.com:19532'
```

**Optional:** No

**Default value:** Undefined

### systemd_journal_upload_server_key_file

The server’s private key file.

```yaml
systemd_journal_upload_server_key_file: '/etc/ssl/certs/fqdn.key'
```

**Optional:** No

**Default value:** Undefined

### systemd_journal_upload_server_certificate_file

The server’s certificate file.

```yaml
systemd_journal_upload_server_certificate_file: '/etc/ssl/certs/fqdn.pem'
```

**Optional:** No

**Default value:** Undefined

### systemd_journal_upload_trusted_certificate_file

The file containing the CA certificates.

```yaml
systemd_journal_upload_trusted_certificate_file: '/etc/ssl/certs/ca.cert.pem'
```

**Optional:** No

**Default value:** Undefined

### systemd_journal_upload_restart

The systemd `Restart=` value for the service drop-in override. Controls when the service is automatically restarted.

```yaml
systemd_journal_upload_restart: "on-failure"
```

**Optional:** Yes

**Default value:** `on-failure`

### systemd_journal_upload_restart_sec

The systemd `RestartSec=` value for the service drop-in override. Sets the time to sleep before restarting the service.

```yaml
systemd_journal_upload_restart_sec: "30s"
```

**Optional:** Yes

**Default value:** `5s`

## Example Playbook

Including an example of how to use your role (for instance, with variables passed
in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
     - role: unibeid.systemd_journal_upload
       vars:
         systemd_journal_upload_url: 'https://server.domain.com:19532'
         systemd_journal_upload_server_key_file: '/etc/ssl/certs/fqdn.key'
         systemd_journal_upload_server_certificate_file: '/etc/ssl/certs/fqdn.pem'
         systemd_journal_upload_trusted_certificate_file: '/etc/ssl/certs/ca.cert.pem'
```

## Compatibility

This role has been written for and tested on and is therefore compatible with:

* rockylinux9

## License

MIT

## Author Information

The role was created in 2026 by the IT-Services Office of the University of Bern
