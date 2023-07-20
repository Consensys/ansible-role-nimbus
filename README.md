# Ansible Role: nimbus

### Description
Ansible role that will install, configure and runs [nimbus](https://github.com/nimbusaticlabs/nimbus): an enterprise Ethereum 2 Client

### Table of Contents
  - [Supported Platforms](#supported-platforms)
  - [Dependencies](#dependencies)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [License](#license)
  - [Author Information](#author-information)

### Supported Platforms
```
* MacOS
* Debian
* Ubuntu
* Redhat(CentOS/Fedora)
* Amazon
```

### Role Variables:

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file. By and large these variables are configuration options. Please refer to the nimbus [docs](https://nimbus.guide/options.html) for more information


| Name                           | Default Value                      |  Description                                                                                                        |
|--------------------------------|------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `nimbus_version`             | ___unset___                        | __REQUIRED__ Version of nimbus to install and run.                                                            |
| `nimbus_user`                | nimbus                         | nimbus user                                                                                                   |
| `nimbus_group`               | nimbus                         | nimbus group                                                                                                  |
| `nimbus_base_dir`            | /opt/nimbus                    | Path to install to                                                                                           |
| `nimbus_config_dir`          | /etc/nimbus                    | Path for default configuration                                                                               |
| `nimbus_data_dir`            | /opt/nimbus/data               | Path for data directory                                                                                      |
| `nimbus_validator_data_dir`  | /opt/nimbus/validatorData      | Path for validaror data directory                                                                            |
| `nimbus_log_dir`             | /var/log/nimbus                | Path for logs directory                                                                                      |
| `nimbus_log_level`           | "info"                        | Log level                                                                                               |
| `nimbus_network`             | mainnet                       | Predefined network configuration                                                                                    |
| `nimbus_jwt_auth_file`       | "/etc/jwt-secret.hex"         | Path of the JWT file                                                                                                |
| `nimbus_execution_urls`                 | "http://127.0.0.1:8551" | The elc execution url                                                                                               |
| `nimbus_validator_beaconnodes`    | "http://127.0.0.1:5051"       | The beacon endpoint for the validator to use                                                                |
| `nimbus_default_fee_recipient`    | ""                            | The default fee recepient address                                                                         |
| `nimbus_keys_dir`                 | "/config/keys"                          |  The keys directory for validators                                                                        |
| `nimbus_secrets_dir`              | "/config/secrets"                       |  The secrets directory for validators                                                                        |
| `nimbus_beacon_enabled`    | True                                 |  Default run the beacon node                                                                              |
| `nimbus_validator_enabled` | False                                | Whether to run in validator mode - please note that the secrets and keys need to be copied by you         |

### Keys/Secrets
Please note that you must put your own secrets and keys in the config directory that you are using ie `nimbus_config_dir`

### Example Playbook

1. Default setup:
Install the role from galaxy
```
ansible-galaxy install consensys.nimbus
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the nimbus [releases](https://github.com/nimbusaticlabs/nimbus/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: consensys.nimbus
    vars:
      nimbus_version: vx.y.z
      nimbus_git_hash: abcd1203

```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


2. Install via github

```
ansible-galaxy install git+https://github.com/consensys/ansible-role-nimbus.git
```

Create a requirements.yml with the following:
Replace `x.y.z` below with the version you would like to use from the nimbus [releases](https://github.com/nimbusaticlabs/nimbus/releases) page
```
---
- hosts: localhost
  connection: local
  force_handlers: True

  roles:
  - role: ansible-role-nimbus
    vars:
      nimbus_version: vx.y.z
      nimbus_git_hash: abcd1203


```

Run with ansible-playbook:
```
ansible-playbook -v /path/to/requirements.yml
```


### License

Apache


### Author Information

Consensys, 2023
