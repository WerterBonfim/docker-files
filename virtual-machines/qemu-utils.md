

```bash

qemu-img create -f qcow2 alpine.qcow 20G

# install alpine
qemu-system-x86_64 \
    -hda alpine.qcow \
    -boot d \
    -cdrom ../sistemas/alpine-virt-3.16.0-x86_64.iso -m 1G   


# after install
qemu-system-x86_64 \
    -hda alpine.qcow \
    -boot d \
    -m 1G




# Slackware 15
qemu-system-x86_64 \
    -enable-kvm \
    -m 4G \
    -smp 2 \
    -name 'slackware' \
    -hda slackware.qcow2 \
    -boot d \
    -cdrom ../sistemas/slackware64-15.0-install-dvd.iso 


```
