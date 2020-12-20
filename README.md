# Ansible Role - squid3

Ansible role to install and configure squid3

### Example

```yaml
squid3_localnets:
  - 10.0.0.0/8

squid3_sslports:
  - 443

squid3_safeports:
  - 80
  - 443
  - 8080
  
squid3_port: 3128
squid3_outgoing_adress: ''
squid3_visible_hostname: 'proxy.devo.re'

squid3_acls:
  - { name: 'CONNECT', type: 'method', arg: 'CONNECT' }

squid3_http_access:
  - { perm: 'deny', aclname: '!Safe_ports' }
  - { perm: 'deny', aclname: 'CONNECT !SSL_ports' }
  - { perm: 'allow', aclname: 'localhost manager' }
  - { perm: 'deny', aclname: 'manager' }
  - { perm: 'allow', aclname: 'localnet' }
  - { perm: 'allow', aclname: 'localhost' }
  - { perm: 'deny', aclname: 'all' }

squid3_refresh_pattern:
  - { case_sensitive: '', regex: '^ftp:', min: '1440', percent: '20%', max: '10080', opts: '' }
  - { case_sensitive: '', regex: '^gopher:', min: '1440', percent: '10%', max: '1440', opts: '' }
  - { case_sensitive: '-i', regex: '(/cgi-bin/|\?):', min: '0', percent: '0%', max: '0', opts: '' }
  - { case_sensitive: '', regex: '.', min: '0', percent: '20%', max: '4320', opts: '' }
```

### License

GPLv3

### Author Information

Jonatas Baldin      
<mailto:jonatas.baldin@gmail.com>      
http://deployeveryday.com

Forked by Pierre Coimbra in 2020
