---
title: 'ATAoE setup'
date: 2011-07-22T10:15:16+07:00
draft: false
---
ATAoE (ATA over Ethernet) เป็นซอฟต์แวร์ที่จะทำให้เครื่องภายในวงแลนเดียวกัน สามารถใช้ดิสก์ที่ server แชร์ออกมา โดยเสมือนว่าเป็น Local disk โดย ataoe จะทำงานบน layer2 ของ OSI Model

ในการทำงานของ ataoe จะประกอบด้วย 2 ส่วน คือ ฝั่ง server และ client โดยในฝั่ง server นั้นจะทำการ share พื้นที่ โดยอาจจะแชร์ file , partition หรือ disk ทั้งลูก ออกไปทาง network ที่กำหนด โดยผ่านบริการ vblade และฝั่ง client จะติดตั้ง aoetools และเริ่มการทำงานของ aoe จากนั้นจะเห็น device ที่ server share ออกมา โดยเสมือนเป็น local device

### ขั้นตอนการติดตั้ง server

1. ติดตั้ง package vblade ที่ฝั่ง server
2. สร้างไฟล์เปล่า ๆ ขึ้นมาในกรณีที่จะแชร์พื้นที่จากไฟล์
3. #dd if=/dev/zero bs=1024 count=10240 of=/root/disk1
4. แก้ไขไฟล์คอนฟิก vblade.conf ซึ่งจะอยู่ที่ /etc/vblade.conf โดยค่าในไฟล์คอนฟิกจะเรียงกันโดยแบ่งค่าโดยใช้ space (ช่องว่าง) โดยค่าจะเรียงดังนี้  
    network_device ช่องทางเครือข่ายที่จะแชร์ดิสก์ออกไป  
    shelf ชั้นดิสก์เสมือน มีค่าได้ตั้งแต่ 0 ถึง 65535  
    slot ช่องดิสก์เสมือน มีค่าได้ตั้งแต่ 0 ถึง 255  
    file/disk/partition Path ที่เป็น device หรือไฟล์ที่จะแชร์  
    mac[,mac[,mac]] สำหรับการแชร์เฉพาะเครื่อง โดยจะนำ MAC Address เครื่อง client มาใส่ ถ้ามีหลาย เครื่อง client ที่จะแชร์ให้คั่นด้วยเครื่องหมาย , โดยรูปแบบจะเป็นดังนี้  
<table class="table table-bordered">
         <td>
           # network_device shelf slot file/disk/partition mac[,mac[,mac]]  
           # eth0 0 0 /dev/sdb 00:11:22:33:44:55  
           eth0 0 1 /root/disk1 # แชร์จากไฟล์ที่สร้าง  
           eth0 0 2 /dev/sdb # แชร์จาก disk  
           eth0 0 3 /dev/sdc1 # แชร์จาก partition
         </td>
</table>
5. เริ่มบริการ vblade และให้เริ่มบริการอัตโนมัติ  
<table class="table table-bordered">
         <td>
           # service vblade start  
           # chkconfig vblade on
         </td>
</table>
    
### ขั้นตอนการติดตั้ง Client

1. ติดตั้ง aoetools
2. สั่ง modprobe aoe เพื่อโหลดโมดูล aoe
3. สั่งคำสั่ง aoe-stat ดูว่าเห็น device ที่แชร์จาก server หรือไม่ ถ้าเห็นให้สั่ง fdisk -l ดูว่าเห็น device เพิ่มขึ้นมารึปล่าว ถ้าเห็นแล้วก็สามารถ mount ใช้งานได้เสมือนเป็น local device ได้เลย โดยตำแหน่งของ device จะอยู่ที่ /dev/etherd/ex.x โดย x.x คือ blade และ shelf ที่ตั้งไว้ในค่าการแชร์ทางฝั่งของ server
4. ถ้าต้องการใช้ aoetools ทำงานเมื่อเริ่มระบบให้เขียนสคริปต์เก็บไว้ที่ /etc/sysconfig/modules/ โดยภายในมีข้อความดังนี้
<table class="table table-bordered">
         <td>
           #!/bin/bash  
            if [ ! -c /dev/etherd/discover ]  
            then  
            echo "--* Modprobe aoe modules ----"  
            modprobe aoe  
            fi
         </td>
</table>
บันทึกไว้และ chmod ให้สามารถ execute ได้
<table class="table table-bordered">
         <td>
           # chmod +x /etc/sysconfig/modules/AoE.modules
         </td>
</table>
note  ถ้าเป็นเวอร์ชั่นใหม่ ๆ ในปัจจุบัน จะไม่ต้องเขียนสคริปต์นี้แล้ว เนื่องจากได้มีการทำการเรียกใช้งานเป็น service แล้ว   โดยสั่ง service aoe {start | stop | restart } 
