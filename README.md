# system-admin-eng
##KVM on vm Disk resizge and LVM mathode
Cauction: If Configuration disk expend then must kvm-vm disk will be LVM otherwise cant not disk resize.

At fast showing have on system disk-spache. 
# lsblk 
and then uses the disk-spach  which file and directory.
# df -h 
after disk-space showing. vm will be must shutdown.
# sudo poweroff / for host machine # virsh shutdown openclaw-server
Disk spach for resize which have vm location on drive find that.
# sudo virsh domblklist openclow_server

