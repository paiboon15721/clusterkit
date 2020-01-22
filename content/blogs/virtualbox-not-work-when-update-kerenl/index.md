---
title: 'แก้ไขปัญหา VirtualBox ทำงานไม่ได้เมื่อมีการ update kernel'
date: 2015-12-25T10:46:42+07:00
draft: false
---
สำหรับ Ubuntu การ update kernel (linux-image) เป็นเรื่องปกติที่มากับ software update อยู่ แต่เมื่อเราใช้ VirtualBox ซึ่งในตัว VirtualBox จะมีการ build kernel module สำหรับตัว Virtualbox เอง ซึ่งต้องการ linux-header ของ linux-image ตัวปัจจุบันด้วย ซึ่งเมื่อ update linux-image แล้ว start vm ไม่ขึ้น เนื่องจาก software update ไม่ได้โหลด kernel-header มาด้วย

วิธีแก้ไขให้โหลด kernel-header ของตัว kernel ปัจจุบัน
   <table class="table table-bordered">
         <td>
            # sudo apt-get install linux-headers-4.2.0-22-generic
         </td>
   </table>

แล้วสั่งคำสั่งเพื่อ build kernel module ใหม่

Ubuntu 15.10
   <table class="table table-bordered">
         <td>
            # sudo rcvboxdrv setup
         </td>
   </table>

Older version
   <table class="table table-bordered">
         <td>
           # /etc/init.d/vboxdrv setup 
         </td>
   </table>

เท่านี้ก็จะสามารถใช้งาน VirtualBox ได้

OS: Ubuntu 15.10

SW: VirtualBox 5

 

Ps. Word for Redhat / Ubuntu

kernel - linux image

kernel-header - linux-headers

