# Ubuntu 22.04 Goss config

## Overview

### Based on CIS Ubuntu Linux 22.04 LTS Benchmark v3.0.0 [Release](https://downloads.cisecurity.org/#/)

Set of configuration files and directories to run the first stages of CIS of Ubuntu 22.04 servers

This is configured in a directory structure level.

This could do with further testing but sections 1.x should be complete

Goss is run based on the goss.yml file in the top level directory. This specifies the configuration.

## Requirements

You must have [goss](https://github.com/krameff/goss/) >= 0.5.0 available to your host you would like to test.

You must have sudo/root access to the system as some commands require privilege information.

Assuming you have already clone this repository you can run goss from where you wish.

Please refer to the audit documentation for usage.

- [readthedocs](https://ansible-lockdown.readthedocs.io/en/latest/)

This also works alongside the [Ansible Lockdown UBUNTU22-CIS role](https://github.com/ansible-lockdown/UBUNTU22-CIS)

Which will:

- install
- audit
- remediate
- audit

## Join us

On our [Discord Server](https://www.lockdownenterprise.com/discord) to ask questions, discuss features, or just chat with other Ansible-Lockdown users

## Contributing

Bug reports and feature requests are welcome from everyone, please raise an issue.

Pull requests are accepted from approved contributors only. To be onboarded, join the [Discord Server](https://www.lockdownenterprise.com/discord) and request contributor access. See [CONTRIBUTING.md](CONTRIBUTING.md) for the full process.

## further information

- [ReadtheDocs](https://ansible-lockdown.readthedocs.io/en/stable/)
- [goss documentation](https://github.com/krameff/goss/blob/master/README.md)
- [CIS standards](https://www.cisecurity.org)
