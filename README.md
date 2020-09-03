# Ansible Role: Certbot

Manage SSL certificates via Certbot / Let's Encrypt.

## Requirements

This role has been tested under Debian Buster.
Other OSes might work as well.

## Role Variables

### `certbot_email`

Set the e-mail address for optaining a certificate (certbot: `--email`).

Example:

```yaml
certbot_email: webmaster@example.com
```

### `certbot_certificates`

This dictionary defines which certificates to create.
The key sets the certificate name (certbot: `--cert-name`).
It doesn't have to be a domain and can be any string.
But keep it simple because the certificate name will be included in several
paths.

The value is another dictionary with at least a key named "domains", that
contains a list of domains to include in the certificate.

Example:

```yaml
certbot_certificates:
  example.com:
    domains:
      - example.com
      - www.example.com
```

## Dependencies

None.

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: certbot
      certbot_email: webmaster@example.com
      certbot_certificates:
        example.com:
          domains:
            - example.com
            - www.example.com
```

## License

This Ansible role is released under the [MIT License](LICENSE.txt).
