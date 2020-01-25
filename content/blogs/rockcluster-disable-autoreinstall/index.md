---
title: 'ปิด Auto Reinstall ของ Rocks Cluster'
date: 2010-12-22T10:04:44+07:00
draft: false
---
โดย default ของระบบ rocks cluster เมื่อเครื่อง compute มีปัญหา เกิดการปิดเครื่องที่ไม่สมบูรณ์ ระบบจะทำการ reinstall เครื่องนั้นใหม่โดยอัตโนมัติ ซึ่งถ้าต้องการปิด feature นี้ สามารถทำได้โดย

เข้าไปยังเครื่อง compute แต่ละเครื่อง แล้วสั่งคำสั่งด้านล่างนี้เพื่อปิดการทำงานของ autoreinstall

หยุด service rocks-grub
   <table class="table table-bordered">
         <td>
            # /etc/rc.d/init.d/rocks-grub stop
         </td>
   </table>

ปิดการรันเมื่อเปิดเครื่องใหม่ โดยการลบรายการออก
   <table class="table table-bordered">
         <td>
            # /sbin/chkconfig --del rocks-grub
         </td>
   </table>

หรือ ปิดการรันของ service rocks-grub เมื่อบูตเครื่องขึ้นมาใหม่
   <table class="table table-bordered">
         <td>
            # chkconfig rocks-grub off
         </td>
   </table>

หรือใช้คำสั่ง tentakel เข้าช่วยในการสั่งงาน ในกรณีที่มีเครื่อง compute มาก ๆ

โดยสั่งงานจาก frontend หยุด service rocks-grub
   <table class="table table-bordered">
         <td>
            # tentakel /etc/rc.d/init.d/rocks-grub stop
         </td>
   </table>

ปิดการรันเมื่อเปิดเครื่องใหม่ โดยการลบรายการออก
   <table class="table table-bordered">
         <td>
            # tentakel /sbin/chkconfig --del rocks-grub
         </td>
   </table>

หรือ ปิดการรันของ service rocks-grub เมื่อบูตเครื่องขึ้นมาใหม่
   <table class="table table-bordered">
         <td>
            # tentakel chkconfig rocks-grub off 
         </td>
   </table>


