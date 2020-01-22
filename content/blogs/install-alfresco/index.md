---
title: 'Install Alfresco'
date: 2012-11-07T14:27:42+07:00
draft: false
---

Alfresco เป็นระบบ ECM (Enterprise Content Management) ซึ่งจะช่วยในการจัดการ Content ต่าง ๆ ภายในองค์กร ไม่ว่าจะเป็นเอกสารต่าง ๆ , การทำเวอร์ชั่นของเอกสาร, จำกัดสิทธิ์ต่าง ๆ ในการเข้าใช้เอกสาร ซึ่งจะอำนวยความสะดวกให้แก่องค์กร โดยสามารถติดตั้งได้ดังนี้

ขั้นตอนการติดตั้ง

1. download alfresco 4 community edition จาก
   http://dl.alfresco.com/release/community/build-00007/alfresco-community-4.0.e-installer-linux-x64.bin

2. สั่งรัน alfresco จาก terminal ในหน้า gui
   <table class="table table-bordered">
         <td>
           # sh alfresco-community-4.0.e-installer-linux-x64.bin 
         </td>
   </table>
   จากนั้นติดตั้ง ตาม gui window ที่ขึ้นมา

3. ถอนการติดตั้ง mod_nss เนื่องจากถ้ารัน alfresco แล้วจะรัน httpd ไม่ขึ้น
   <table class="table table-bordered">
         <td>
            # yum remove mod_nss 
         </td>
   </table>

4. start alfresco และให้รันอัตโนมัติเมื่อเปิดเครื่อง
   <table class="table table-bordered">
         <td>
           # service alfresco start  
           # chkconfig alfresco on       
         </td>
   </table>
