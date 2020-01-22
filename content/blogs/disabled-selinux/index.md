---
title: 'วิธีปิด SELinux'
date: 2010-12-17T10:28:42+07:00
draft: false
---
ซึ่งมีความซับซ้อนในการบริหารจัดการอยู่พอสมควร SELinux แตกต่างจากระบบรักษาความปลอดภัยแบบเดิม ซึ่งถ้าไม่เข้าใจดีพออาจจะทำให้เกิดปัญหาในการคอนฟิกเพื่อใช้งานกับระบบได้
เราจะตรวจสอบว่าระบบของเรารัน SELinux อยู่หรือไม่นั้น จะใช้คอมมานด์ getenforce ในการตรวจสอบ
<table class="table table-bordered">
         <td>
            # getenforce  
            Enforcing
         </td>
</table>


ซึ่งถ้าต้องการปิด SELinux ลง เราต้องแก้ไขไฟล์คอนฟิกของ SELinux เพื่อปิดการทำงาน โดยแก้ไขที่ไฟล์ /etc/sysconfig/selinux
<table class="table table-bordered">
         <td>
            # vi /etc/sysconfig/selinux
         </td>
</table>

และเข้าไปแก้ไขบรรทัดที่มีข้อความ SELINUX=enforcing
ให้เป็น SELINUX=disable
เมื่อแก้ไขเรียบร้อย และเซฟ จะเสร็จสิ้นการแก้ไขไฟล์คอนฟิกของ SELinux แต่ SELinux จะยังคงรันอยู่ ถ้าจะให้ SELinux ปิดลงอย่างถาวร ให้ทำการ reboot เครื่อง แต่ถ้าต้องการปิด SELinux ลงทันทีโดยไม่ reboot ให้สั่งคำสั่ง setenforce 0 จะเป็นการปิด SELinux ลงแบบชั่วคราว
<table class="table table-bordered">
         <td>
            # setenforce 0
         </td>
</table>

ซึ่ง SELinux จะทำงานในโหมด Permissive คือ ปิดการทำงานตรวจสอบของ SELinux แต่ยังคงเก็บ log ของ SELinux อยู่
