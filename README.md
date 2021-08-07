[![Build Status - Master](https://travis-ci.org/juju4/ansible-win-sysmon.svg?branch=master)](https://travis-ci.org/juju4/ansible-win-sysmon)
[![Build Status - Devel](https://travis-ci.org/juju4/ansible-win-sysmon.svg?branch=devel)](https://travis-ci.org/juju4/ansible-win-sysmon/branches)(Syntax Only)

[![Appveyor - Master](https://ci.appveyor.com/api/projects/status/t0mqe5h33m0d0fbl?svg=true)](https://ci.appveyor.com/project/juju4/ansible-win-sysmon)
![Appveyor - Devel](https://ci.appveyor.com/api/projects/status/t0mqe5h33m0d0fbl/branch/devel?svg=true)

# Windows Sysmon ansible role

Ansible role to setup Sysinternals Sysmon on Windows system.

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 2.3 (Not working! [ansible#23940](https://github.com/ansible/ansible/issues/23940) = template upload failing)
 * 2.4
 * 2.5b2

### Operating systems

Tested in Appveyor

## Example Playbook

Just include this role in your list.
For example

```
- host: all
  roles:
    - juju4.win-sysmon
```

Run
```
$ ansible -i inventory -m win_ping win --ask-pass
$ ansible-playbook -i inventory --limit win site.yml
```

## Variables

See defaults/main.yml for full scope

## Continuous integration

This role has a travis basic test (for github, syntax check only), Appveyor test and a Vagrantfile (test/vagrant).

```
$ cd /path/to/roles/juju4.win-sysmon/test/vagrant
$ vagrant up
$ vagrant provision
$ vagrant destroy
$ ansible -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory -m win_ping -e ansible_winrm_server_cert_validation=ignore -e ansible_ssh_port=55986 all
```

## Troubleshooting & Known issues

## FAQ

Reference links
* Sysmon, https://gist.github.com/Neo23x0/f56bea38d95040b70cf5
*  https://onedrive.live.com/view.aspx?resid=D026B4699190F1E6!2575 (RSA 2016)
* http://www.darkoperator.com/blog/2014/8/8/sysinternals-sysmon
```
PS> Get-WinEvent -FilterHashtable @{logname="Microsoft-Windows-Sysmon/Operational";}
```
* native alternative for process auditing (not network?) on Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 (ID 4688)

## License

BSD 2-clause
