---
title: 'แก้ปัญหา VirtualBox ไม่เห็น USB Device บน Ubuntu'
date: 2013-06-13T15:21:58+07:00
draft: false
---
เนื่องจากผู้เขียนได้ทำการติดตั้งระบบปฏิบัติการ Ubuntu ใหม่ โดยที่เก็บค่า config เดิมไว้  และได้ติดตั้ง VirtualBox และ Guest Addition เข้าไป ซึ่งปกติจะทำให้สามารถใช้งาน USB Device ที่ต่อกับ Host ได้ แต่ในครั้งนี้กลับมองไม่เห็น Device เลย  

ปัญหาเกิดมาจากในการติดตั้งนั้น user ที่ใช้งานอยู่ไม่ได้ถูก add เข้าไปอยู่ใน group ของ vboxusers ทำให้ใช้งาน USB Device ไม่ได้ 

วิธีแก้ไขให้ทำการ modify user ให้เข้าไปอยู่ใน group ดังกล่าว โดยใช้ คำสั่ง
   <table class="table table-bordered">
         <td>
            # sudo  usermod -aG vboxusers clusterkit 
         </td>
   </table>

และ reboot ก็จะทำให้ใช้งาน usb device ใน virtual box ได้