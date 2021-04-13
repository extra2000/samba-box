# samba-box

| License | Versioning | Build |
| ------- | ---------- | ----- |
| [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) | [![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release) | [![Build status](https://ci.appveyor.com/api/projects/status/psvh5n5r3x2pe7dc/branch/master?svg=true)](https://ci.appveyor.com/project/nikAizuddin/samba-box/branch/master) |

Developer box for [Samba](https://github.com/samba-team/samba).


## Creating Vagrant Box

Copy example pillar file for samba. Optionally you may want to edit the values in the `samba.sls`:
```
$ cp -v salt/roots/pillar/samba.sls.example salt/roots/pillar/samba.sls
```

Copy vagrant file from `vagrant/examples/` and then create the vagrant box (you can change to `--provider=virtualbox` if you want to use Oracle VirtualBox provider):
```
$ cp -v vagrant/examples/Vagrantfile.samba-box.fedora-33.x86_64.example vagrant/Vagrantfile.samba-box
$ vagrant up --provider=libvirt
```

Provision the vagrant box:
```
$ vagrant ssh samba-box -- sudo salt-call state.highstate
```

Install samba:
```
$ vagrant ssh samba-box -- sudo salt-call state.sls samba
```
