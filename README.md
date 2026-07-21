# system-admin-eng
## KVM on vm Disk resizge and LVM mathode
# Cauction: If Configuration disk expend then must kvm-vm disk will be LVM otherwise cant not disk resize.

At fast showing have on system disk-spache. 
# lsblk 
and then uses the disk-spach  which file and directory.
# df -h 
after disk-space showing. vm will be must shutdown.
# sudo poweroff / for host machine # virsh shutdown openclaw-server
Disk spach for resize which have vm location on drive find that.
# sudo virsh domblklist openclow_server
After showing the vm disk path and img location. will be the disk-resize.

if disk spach resize 50GB fot that will be
# sudo qemu-img resize /mnt/mydisk/backup/vm/openclow_server.qcow2 +50G

when vm disk resize is done then vm will be start
# virsh start openclow_server
check the disk > lsblk and > command df -h
when check disk 'lsblk' showing terminal on system disk-size add in vda not root directory '/'. For thsi resone will be LVM
check the disk which mathode format by disk gpt or pmbr 
# sudo fdisk -l /dev/vda
Now will be extend partition vda3 

# sduo growpart /dev/vda 3
varify the partion adding 50Gb showing.check /# sudo pvdisplay /#sudo lvdisplay thsi command for all details lvm 
and then extend the logical volume 
# sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
resizefile system and entry the fstab 
# sudo resize2fs /dev/ubuntu-vg/ubuntu-lv 
finally check the vm 50GB add is it connected the '/' partition
# lsblk
