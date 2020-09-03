# Ansible Role: Certbot

Manage SSL certificates via Certbot / Let's Encrypt.

## Requirements

This role has been tested under Debian Buster.
Other OSes might work as well.

## Role Variables

### `certbot_email`

Set the e-mail address for obtaining a certificate (certbot: `--email`).

Example:

```yaml
certbot_email: webmaster@example.com
```

### `certbot_certificates`

This dictionary defines which certificates to create.
The key is the certificate name (certbot: `--cert-name`), which can be a
domain.
And the value is a list of domains to be included in the certificate.

Example:

```yaml
certbot_certificates:
  example.com:
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
          - example.com
          - www.example.com
```

## License

This Ansible role is released under the [MIT License](LICENSE.txt).
