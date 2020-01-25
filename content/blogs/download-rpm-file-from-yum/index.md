---
title: 'How to download rpm file from yum'
date: 2010-01-18T11:37:21+07:00
draft: false
---
คำสั่ง yum เป็นคำสั่งที่ใช้ในการดึง package จาก repository มาลงในเครื่องเรา แบบเดียวกับคำสั่ง apt-get ในฝั่งของ Debian หรือ Ubuntu  แต่ถ้าในบางครั้งถ้าเราต้องการไฟล์ rpm มาเก็บไว้ด้วยล่ะ ? ตามมาว่าเราสามารถทำยังไงได้

วิธีการดาวน์โหลดไฟล์ rpm โดยใช้คำสั่ง yum จาก yum repository

ขั้นแรก สั่งคำสั่ง 
  <table class="table table-bordered">
         <td>
            # yum install yum-downloadonly
         </td>
  </table>

เมื่อต้องการโหลด rpm จาก repository ให้สั่งคำสั่ง
   <table class="table table-bordered">
         <td>
             # yum update <package> -y --downloadonly 
         </td>
   </table>

ปกติไฟล์ที่ดาวน์โหลดจาก yum มานั้นจะเก็บอยู่ที่ directory /var/cache/yum ซึ่งถ้าต้องการระบุไฟล์ให้ไปเก็บไว้ที่ directory ที่ต้องการให้สั่ง
   <table class="table table-bordered">
         <td>
             # yum update <package> -y --downloadonly --downloaddir=/< dir>
         </td>
   </table>

โดยที่  " /< dir> " จะเป็นการระบุ path ปลายทางที่จะเก็บไฟล์