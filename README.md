# RPM Specs

A collection of RPM specs for ruby web apps.

## Building

### Buildbox Setup
```bash
sudo yum -y groupinstall "Development Tools"
sudo yum -y install rpm-build rpmdevtools readline readline-devel ncurses ncurses-devel gdbm gdbm-devel glibc-devel glibc-static tcl-devel gcc unzip openssl-devel db4-devel byacc make libffi libffi-devel

rpmdev-setuptree
```

### Building the RPMs

```bash
wget https://github.com/clowder/rpm-specs/archive/master.zip
unzip master && mv rpm-specs-master/* rpmbuild/

cd rpmbuild/
spectool -g -R SPECS/libyaml.spec
rpmbuild -bb --nodeps --clean SPECS/libyaml.spec

sudo yum localinstall RPMS/x86_64/libyaml-devel-0.1.4-1.el6.x86_64.rpm RPMS/x86_64/libyaml-0.1.4-1.el6.x86_64.rpm

spectool -g -R SPECS/ruby19.spec
rpmbuild -bb --nodeps --clean SPECS/ruby19.spec
```

## Thanks
**[imeyer](http://github.com/imeyer)** for the [original ruby19.spec](https://github.com/imeyer/ruby-1.9.3-rpm).

**[repoforge](https://github.com/repoforge)** for the [original libyaml.spec](https://github.com/repoforge/rpms).
