pvs /command for any machine is there any pv ha taht show 
pvdisplay all details showing

#man pvdisplay  
#lsblk
#cd /etc/lvm 
#tree shows all LVM 

pvcrete
#sudo fdisk /dev/vdb
type g for GPT
Type p for print
Type n for a new parton 
type entre 
Type enter +10G
Type L FOR list the LVM ID select 
Select:t   enter then 
:31   for LVM ID
:p  for print 
:w write

#lsblk
#ls -ll /dev/vdb1 show details
#pvcreate /dev/vdb1  /command for physical volume create

#cd /etc/lvm
#tree shows all details for LVM 

#pvs 
#pvdisplay	all ditls lvm 

VG create 

#vgs 
#vgdisplay
#man vgdisplay

#vgcreate mayvg /dev/vdb1  -s 4mb    bydefault 4mb
#pvs 
#Vgs
#vgdisplay shows all vg details

#blkid 
#ll /dev/mapper
#tree /ect/lvm

Lv create

#lvs 
#lvdisplay
#lvcreate myvg -L 10M - n lv1 or

#lvcreate myvg1 -l 2559 -n lvm1
#ll /dev/myvg1/vlm2
#ll /dev/mapper

Mount 
#lvdisplay   that file get the path, then the path format the file system make 
  
#mkfs.ext4 /dev/myvg1/vlm2
#blkid /dev/myvg1/vlm2  showing UUID 

$sudo vim /etc/fstab +

/dev/myvg1/vlm2  /data ext4 default  0 0

UUID="aa650e91-1d16-464d-8272-4790ce97503a" /data ext4 default 0 0

:wq!
$sudo mkdir /data

#mount -av
Show details
$sudo lsblk
$sudo df -H

Lvm resize 
$sudo lvresize -r -L + 10G /dev/myvg1/lvm2 or 
$sudo lvresize -r -l +2095 /dev/ubuntu-vg/ubuntu-lv

EXPERIMENT:

If the machine has 20g, then it needs more 20g then  
Add hardware 20G type SATA

Need to add with vgs:
$sudo pvdisplay
$sudo vgdisplay
$sudo vgextend ubuntu-vg /dev/vdc

$ sudo lvdisplay

$sudo lvresize -r -l +5119 /dev/ubuntu-vg/ubuntu-lv

Add more 30G sda:

$sudo vgextend ubuntu-vg /dev/sda

$sudo vgdisplay /show details

  
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  9
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               68.21 GiB
  PE Size               4.00 MiB
  Total PE              17463
  Alloc PE / Size       9784 / <38.22 GiB
  Free  PE / Size       7679 / <30.00 GiB
  VG UUID               dSH1X8-3pGI-b4r7-kPQx-wcPd-zRik-OxB6LK
   

$sudo lvdisplay
$sudo lvresize -r -l + 7679 /dev/ubuntu-vg/ubuntu-lv

add successfully 

$sudo lsblk

If lmv with swap partition is done then

$sudo free -h
$sudo lvcreate -n swap2 -L 512M ubuntu-vg /with vgs file. if increase

$sudo lvresize -r -L +100M /dev/ubuntu-vg/ubuntu-lv

File system make 
$sudo mkswap /dev/mylv/swap2
$sudo vim /etc/fstab

/dev/mylv/swap swap swap defaults 0 0  /bydefaults swap mountpoint has swap
:wq!

$sudo swapon -av 



Overview:
At fast create disk then. Make pv

$ sudo pvcreate maypv1 /dev/vda
$sudo pvdisplay
$sudo vgcreate vg1 /dev/vda 
$sudo vgdisplay 
$sudo lvcreate vg1 -n lvm1 -L +20G or
$sudo lvcreate vg1 -n lvm1 -l +2096
$sudo lvdisplay  /all is done. then make file system.
$sudo mkfs.ext4 /dev/vg1/mylv1
$sduo lvdisplay  /show lvm path
$sudo blkid /dev/vg1/mypv1 /show UUID for permanent can use uuid or path.
$sudo vim /etc/fstab
/dev/vg1/mypv1 /data ext4 defaults 0 0

:wq!
$sduo mkdir -r /data
$sudo mount -av
 
General purpos
$fallocate -l 1M file 
ext4,xfs,vfat all formate tye have /etc/mkfs.conf
$sudo vim  /etc/mke2fs.conf

$sudo cd /xfs/
$df -h  sow all details
$touch file create a file
$df -i showing i node 
$df -iT show type
$lsblk -f file type showing
$df -hiT




