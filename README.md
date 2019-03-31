# linux_realmd

This Ansible role will join a Linux host to an Active Directory domain using realmd.

## Requirements

* The role uses magic variables to determine the Linux distribution type. Ansible facts must be available.
* This role uses root to install system packages and and join system to an Active directory domain.
* This role uses system package manager install packages. The host must have package sources setup.
* An active directory user with permission to join a host to the domain.

## Role Variables

All over-writable variables used in this role are defined in defaults/main.yml.

You can override the variables in any standard Ansible-way (e.g. group_vars, host_vars, playbook variables, command-line, etc.).

The variables in this role include:

|parameter               |required|default   |choices |comments                                                              |
|:-----------------------|:-------|:---------|:-------|:---------------------------------------------------------------------|
|linux_realmd_ad_user    |true    |user      |`string`|An Active Directory domain user with permission to join host to domain|
|linux_realmd_ad_password|true    |CHANGEME  |`string`|Password for Active Directory user                                    |
|linux_realmd_domain     |true    |domain.com|`string`|The Active Directory domain to join to                                |
|linux_realmd_packages   |false   |['sssd', 'realmd', 'pam_krb5', 'krb5-workstation', 'oddjob', 'oddjob-mkhomedir', 'adcli', 'samba-common', 'samba-common-tools', 'ntpdate', 'ntp', 'python-pip']|`list` of `strings`|A list of packages required for joining to the domain. Normally this shouldn't need to be changed|
## Example Playbook

Run playbook with variables defined outside of playbook
```yaml
    - hosts: servers
      roles:
        - ar_linux_realmd
```

## Author Information

|Author              |E-mail                   |
|:-------------------|:------------------------|
|Derek 'dRock' Halsey|derek.halsey@dinohead.com|

## License

MIT License

Copyright (c) 2019 Dinohead LLC

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Role Development Information

### Testing

### Contributing

### Git SCM
Please refer to the .gitignore file and update accordingly depending on your
development environment, etc.  The particular file was generated at 
[gitignore.io](https://www.gitignore.io/) and contains settings for the following:
  - Ansible
  - Python
  - Vim
  - Eclipse
  - IntelliJ IDEA
  - Linux
  - Windows
  
### Versioning
Please update [VERSION.md](./VERSION.md) as you release new versions of your role and try to
abide by [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

### Self-contained
Please try to keep this role as self-contained as possible such that it may be
simply installed (e.g. `ansible-galaxy install`) and applied as part of a 
playbook.
