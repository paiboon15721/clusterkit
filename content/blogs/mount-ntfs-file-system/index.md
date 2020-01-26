---
title: 'Mount NTFS File System'
date: 2010-01-17T06:09:57+07:00
draft: false
---
NTFS เป็นไฟล์ซิสเต็มส์ในฝั่งของ Windows ซึ่งถ้าเราต้องการ mount filesystem นี้ เพื่อใช้ในการอ่านเขียนข้อมูล เราสามารถทำได้โดย

ขั้นแรก download package  fuse , fuse-ntfs-3g , dkms , dkms-fuse
โดยสามารถ download package จากเว็บไซต์ dag.wieers.com

fuse                   http://dag.wieers.com/rpm/packages/fuse/

fuse-ntfs-3g     http://dag.wieers.com/rpm/packages/fuse-ntfs-3g/

dkms                 http://dag.wieers.com/rpm/packages/dkms/

dkms-fuse        http://dag.wieers.com/rpm/packages/dkms-fuse/

เมื่อโหลดเสร็จแล้วสั่งติดตั้ง package ทั้งหมดที่ download มา

            ## rpm -Uvh dkms* fuse*

หรือถ้าต้องการใช้ yum ในการติดตั้ง package ให้download rpmforge repository จาก     

http://dag.wieers.com/rpm/packages/rpmforge-release/

จากนั้นติดตั้ง repository เพื่อให้ระบบรู้จัก

            ## rpm -Uvh rpmforge*

สั่งติดตั้ง package fuse , fuse-ntfs-3g , dkms , dkms-fuse  จาก repository โดยการสั่ง

            ## yum install fuse fuse-ntfs-3g dkms dkms-fuse

เมื่อต้องการ mount ntfs partion ให้สั่ง

            mount -t ftfs-3g /dev/<ntfs device>  /<mount path>

หรือ

            ntfs-3g /dev/<ntfs device>  /<mount path>

ยกตัวอย่าง  เช่น

            ## mount -t ntfs-3g /dev/hdb6 /media/ni_e

หรือ

            ## ntfs-3g /dev/hdb6 /media/ni_e

ถ้าต้องการให้ระบบ automount เมื่อเริ่มระบบ

ให้เขียนคำสั่งลงในไฟล์ /etc/fstab โดยการสั่ง

            vi /etc/fstab
            -----------------------------
            #  <ntfsdevice>     <mount path>      <file system>
            /dev/hdb1           /media/ni_c          ntfs-3g          defaults        0 0

เมื่อเริ่มระบบใหม่ระบบก็จะ automount โดยอัตโนมัติ