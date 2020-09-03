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

### `certbot_deploy_hook`

The command to run after a successful certificate installation or renewal
(certbot: `--deploy-hook`).

Example:

```yaml
certbot_deploy_hook: systemctl restart nginx.service
```

### `certbot_force_renewal`

Force renewal of certificates, even if not due yet (certbot:
`--force-renewal`).

If you want to add / remove a certificate's domain or update the deploy hook
you have to forcefully run `certbot` once.
This ensures that the certicate and configuration gets updated.

Example:

```yes
certbot_force_renewal: yes
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
      certbot_deploy_hook: systemctl restart nginx.service
```

## License

This Ansible role is released under the [MIT License](LICENSE.txt).
