---
title: 'แก้ปัญหา VirtualBox ใช้ USB Device ไม่ได้'
date: 2015-12-25T10:43:24+07:00
draft: false
---
เมื่อมีปัญหาที่ไม่สามารถใช้ USB Device จากเครื่อง Host เนื่องจากตัว Virtualbox นั้นไม่เห็นอุปกรณ์ USB ที่ต่ออยู่กับ Host ซึ่งจะพบปัญหานี้ในการอัพเกรดหรือติดตั้ง VirtualBox ใหม่ โดยยังมี profile บางอย่างอยู่ในระบบ Virtualbox จึงไม่ได้สร้างขึ้นให้

ซึ่งส่วนปัญหาตรงนี้เกิดจากการที่ User ที่รัน Virtualbox อยู่นั้นไม่ถูกเพิ่มเข้าอยู่ใน group ของ vboxusers ซึ่งเป็น group ของ virtualbox ดังนั้นให้เราเพิ่มชื่อ user ของเราไปต่อท้าย group vboxuser และทำการ logout/login ระบบใหม่ก็จะสามารถใช้งานได้เป็นปกติ

ทางแก้ที่ง่ายที่สุดก็คือไปแก้ไขที่ไฟล์ /etc/group ที่บรรทัด vboxusers โดยเพิ่ม user ที่ใช้งานเขาไป
   <table class="table table-bordered">
         <td>
            # vboxusers:x:129:< user>
         </td>
   </table>

จากนั้นทำการ logout/login ระบบใหม่ก็จะสามารถใช้งานได้เป็นปกติ  
OS : Ubuntu 15.10  
SW : VirtualBox 5.0