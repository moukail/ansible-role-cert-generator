# cert-generator Ansible Role

This role generates:

- An RSA 4096-bit Certificate Authority (CA)
- Server private key
- Server CSR
- CA-signed server certificate

## Variables

| Variable | Default | Description |
|---------|---------|-------------|
| cert_ca_passphrase | "" | CA passphrase (required) |
| cert_ca_dir | /etc/pki/tls/CA | CA key + cert |
| cert_ca_certificate_path | "{{ cert_ca_dir }}/certs/ca.crt" | CA certificate path |
| cert_ca_common_name | "My Internal CA" | CA common name |
| cert_ca_validity | +5y | CA expiration |
| cert_dir | /etc/pki/tls/certs | Server certificates |
| cert_certificate_path | "{{ cert_dir }}/client.crt" | Server certificate path |
| cert_key_path | "{{ cert_dir }}/client.key" | Server private keys |
| cert_common_name | inventory_hostname | CN for server cert |
| cert_validity | +1y | Server certificate expiration |

## Example

```yaml
- hosts: vpn_servers
  roles:
    - role: cert-generator
      vars:
        cert_common_name: "vpn.example.com"