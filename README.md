# certificate_generator Ansible Role

This role generates:

- An RSA 4096-bit Certificate Authority (CA)
- Server private key
- Server CSR
- CA-signed server certificate

## Variables

| Variable | Default | Description |
|---------|---------|-------------|
| cert_ca_dir | /etc/pki/tls/CA | CA key + cert |
| cert_certs_dir | /etc/pki/tls/certs | Server certificates |
| cert_key_dir | /etc/pki/tls/private | Server private keys |
| cert_common_name | inventory_hostname | CN for server cert |
| cert_ca_name | "My Internal CA" | CA common name |
| cert_ca_validity | +5y | CA expiration |
| cert_validity | +1y | Server certificate expiration |

## Example

```yaml
- hosts: vpn_servers
  roles:
    - role: certificate_generator
      vars:
        cert_common_name: "vpn.example.com"