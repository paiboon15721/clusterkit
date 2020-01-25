---
title: 'วิธีแก้ไข grup error : no such disk. บน Rocks 5.3'
date: 2010-02-15T11:50:10+07:00
draft: false
---
เมื่อท่านเปิดเครื่อง Frontend ขึ้นมา แล้ว เจอ ข้อความแจ้งว่า  
Grup loading...  
Error : no such disk  
grub resecue>  

เมื่อท่านเปิดเครื่อง Frontend ขึ้นมา แล้ว เจอ ข้อความแจ้งว่า  
Grup loading...  
Error : no such disk  
grub resecue>  

ให้ท่านแก้ไขด้วยวิธีดังนี้  
1. restart เครื่อง Frontend  
2. ใส่แผ่น Rocks 5.3 เพื่อบูทจากแผ่น  
3. พิมพ์คำสั่ง build rescue บนหน้าสกรีน เพื่อเข้าสู่โหมด rescue  
4. กดปุ่ม continue  
5. กดปุ่ม OK  
6. พิมพ์คำสั่ง # chroot /mnt/sysimage แล้วกดปุ่ม enter  
7. พิมพ์คำสั่ง # grub แล้วกดปุ่ม enter  
8. พิมพ์คำสั่ง # root (hd0,0) แล้วกดปุ่ม enter  
9. พิมพ์คำสั่ง # setup (hd0) แล้วกดปุ่ม enter  
10. พิมพ์คำสั่ง # quit แล้วกดปุ่ม enter  
11. restart เครื่องอีกครั้ง เป็นอันเสร็จ  