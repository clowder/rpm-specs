```
ARCH=`uname -m`
KERNEL_REL=`uname -r`
KERNEL_TMP=${KERNEL_REL%.$ARCH}
DISTRIB=${KERNEL_TMP##*.}

spectool -g SPECS/libyaml.spec
rpmbuild -bb —nodeps SPECS/libyaml.spec

yum localinstall ~/rpmbuild/RPMS/${ARCH}/libyaml-0.1.4-1.${DISTRIB}.${ARCH}.rpm
```
