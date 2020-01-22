---
title: 'ขยายพื้นที่ disk ของ vm บน virtualbox'
date: 2014-04-10T09:32:13+07:00
draft: false
---
ในการใช้งาน vm ถ้าเราสร้าง disk น้อยไป เวลาใช้งานดิสก์ก็อาจจะเต็มได้ เราสามารถขยายดิสก์ของ vm ได้ ในการขยายดิสก์ เราจะสั่งที่เครื่อง Host หรือก็คือ OS หลักที่เรารันอยู่นั่นเอง โดยรันคำสั่ง
   <table class="table table-bordered">
         <td>
            Vboxmanage modifyhd < hdd path> --resize < size in MB>
         </td>
   </table>
 
ถ้าเป็นวินโดว์อาจจะต้องเรียกคำสั่งแบบ full path ถ้ายังไม่ได้ทำการเพิ่มตัวแปร environment variable
ตัวอย่างการเพิ่มขนาด
   <table class="table table-bordered">
         <td>
            # vboxmanage modifyhd /media/data/vm/xp.vdi --resize 20480  
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%mod_nss 
         </td>
   </table>


เมื่อเข้าไปดู vm จะสังเกตว่าขนาดของ hdd ได้เพิ่มขึ้นตามที่เรา resize ไปแล้ว
หลังจากนี้ก็ให้เราหาเครื่องมือ หรือทูลเพื่อเข้าไปจัดการ Partition ที่อยู่ข้างใน vm disk ให้ใช้งานพื้นที่ที่เพิ่มเข้ามาได้

