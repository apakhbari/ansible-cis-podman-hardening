# Ansible CIS Podman Hardening

```
 _______  _______  ______   __   __  _______  __    _      __   __  _______  ______    ______   _______  __    _  ___   __    _  _______ 
|       ||       ||      | |  |_|  ||   _   ||  |  | |    |  | |  ||   _   ||    _ |  |      | |       ||  |  | ||   | |  |  | ||       |
|    _  ||   _   ||  _    ||       ||  |_|  ||   |_| |    |  |_|  ||  |_|  ||   | ||  |  _    ||    ___||   |_| ||   | |   |_| ||    ___|
|   |_| ||  | |  || | |   ||       ||       ||       |    |       ||       ||   |_||_ | | |   ||   |___ |       ||   | |       ||   | __ 
|    ___||  |_|  || |_|   ||       ||       ||  _    |    |       ||       ||    __  || |_|   ||    ___||  _    ||   | |  _    ||   ||  |
|   |    |       ||       || ||_|| ||   _   || | |   |    |   _   ||   _   ||   |  | ||       ||   |___ | | |   ||   | | | |   ||   |_| |
|___|    |_______||______| |_|   |_||__| |__||_|  |__|    |__| |__||__| |__||___|  |_||______| |_______||_|  |__||___| |_|  |__||_______|
```

> [!WARNING]
> Work In Progress

- This Role configures Podman Daemon as per CIS Docker Community Edition Benchmark

> [!IMPORTANT]
> Tested with Podman 18.06 on rocky linux 8

## Requirements
- If you must expose the Podman daemon via a network socket, TLS authentication for the daemon need to be configured.
- Please Generate CA cert and CA Key and place it in the files directory and provide the following aruguments.

```
dockerd_via_network: true

dockerd_ip: 0.0.0.0
dockerd_port: 2376

ca_cert: ca.pem
ca_key: ca-key.pem
ca_key_passphrase: changeme

host_ip: 10.10.10.20

server_cert_path: /etc/docker/tls/server_certs
server_cert: server-cert.pem
server_cert_key: server-key.pem

client_cert_path: /etc/docker/tls/client_certs
client_cert: cert.pem
client_cert_key: key.pem
```

## Role Variables
```
tursted_users:
  - vagrant

config_file: /etc/docker/daemon.json

dockerd_via_network: false

default_ulimits_nofile_soft: 100
default_ulimits_nofile_hard: 200
default_ulimits_nproc_soft: 1024
default_ulimits_nproc_hard: 2048

syslog_address: ''
seccomp_profile: ''
authorization_plugins: []
```

## Issues
- Control `2.8 Enable user namespace support` currently disabled since this interferes with `selinux-enabled` configuration.

## Example Playbook

- Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }
```

## My organization's requiremetns
- My organization requirs this sections to be hardened

| Section 1    | Section 2    | Section 3    | Section 4   | Section 5    | Section 6   | Section 7   |
| ---- | ---- | ---- | --- | ---- | --- | --- |
| 1_1  | 2_1  | 3_1  | 4_2 | 5_1  | 6_1 | 7_1 |
| 1_3  | 2_2  | 3_2  | 4_3 | 5_2  | 6_2 |     |
| 1_4  | 2_5  | 3_3  | 4_5 | 5_3  |     |     |
| 1_5  | 2_6  | 3_4  | 4_6 | 5_4  |     |     |
| 1_6  | 2_7  | 3_5  | 4_7 | 5_5  |     |     |
| 1_7  | 2_8  | 3_6  | 4_8 | 5_6  |     |     |
| 1_8  | 2_9  | 3_7  | 4_9 | 5_7  |     |     |
| 1_9  | 2_11 | 3_8  |     | 5_8  |     |     |
| 1_10 | 2_12 | 3_9  |     | 5_9  |     |     |
| 1_12 | 2_13 | 3_10 |     | 5_13 |     |     |
| 1_13 | 2_14 | 3_11 |     | 5_14 |     |     |
|      | 2_15 | 3_12 |     | 5_15 |     |     |
|      | 2_16 | 3_13 |     | 5_16 |     |     |
|      | 2_17 | 3_14 |     | 5_17 |     |     |
|      | 2_18 | 3_15 |     | 5_18 |     |     |
|      |      | 3_16 |     | 5_19 |     |     |
|      |      | 3_17 |     | 5_20 |     |     |
|      |      | 3_18 |     | 5_21 |     |     |
|      |      | 3_19 |     | 5_22 |     |     |
|      |      | 3_20 |     | 5_23 |     |     |
|      |      |      |     | 5_24 |     |     |
|      |      |      |     | 5_25 |     |     |
|      |      |      |     | 5_26 |     |     |
|      |      |      |     | 5_27 |     |     |
|      |      |      |     | 5_28 |     |     |
|      |      |      |     | 5_29 |     |     |
|      |      |      |     | 5_30 |     |     |
|      |      |      |     | 5_31 |     |     |


# acknowledgment
## Contributors

APA 🖖🏻

## Links

```                                                                                
  aaaaaaaaaaaaa  ppppp   ppppppppp     aaaaaaaaaaaaa   
  a::::::::::::a p::::ppp:::::::::p    a::::::::::::a  
  aaaaaaaaa:::::ap:::::::::::::::::p   aaaaaaaaa:::::a 
           a::::app::::::ppppp::::::p           a::::a 
    aaaaaaa:::::a p:::::p     p:::::p    aaaaaaa:::::a 
  aa::::::::::::a p:::::p     p:::::p  aa::::::::::::a 
 a::::aaaa::::::a p:::::p     p:::::p a::::aaaa::::::a 
a::::a    a:::::a p:::::p    p::::::pa::::a    a:::::a 
a::::a    a:::::a p:::::ppppp:::::::pa::::a    a:::::a 
a:::::aaaa::::::a p::::::::::::::::p a:::::aaaa::::::a 
 a::::::::::aa:::ap::::::::::::::pp   a::::::::::aa:::a
  aaaaaaaaaa  aaaap::::::pppppppp      aaaaaaaaaa  aaaa
                  p:::::p                              
                  p:::::p                              
                 p:::::::p                             
                 p:::::::p                             
                 p:::::::p                             
                 ppppppppp                                                        
```