---
title: 'การทำสำเนา vm ไปใช้เป็น VM template'
date: 2012-11-07T16:04:11+07:00
draft: false
---
ตามปกติในการสร้าง Virtual Machine นั้นจะมีการสร้าง Virtual Haddisk (vdi image สำหรับ virtualbox)  ซึ่งถ้าต้องการทำ VM template เก็บไว้  เพื่อที่จะได้ไม่ต้องมาติดตั้ง OS บ่อย ก็จะสามารถทำได้ ดังนี้

1. เปิด Virtualbox  เลือก Virtual Machine ที่ต้องการทำเป็น template เก็บไว้  และกดไอคอน setting

2. ไปที่ storage คลิกเลือก vdi ที่เลือกทำ template  สังเกตที่ location ทางด้านขวา จะเป็น path ที่อยู่ของไฟล์ .vdi ที่เลือก

3. ทำการ copy ไฟล์ .vdi จาก path ดังกล่าว เก็บไว้เป็นไฟล์ template

4. เนื่องจากไฟล์ .vdi แต่ละตัวจะมีเลข uuid ที่ไม่ซ้ำกันอยู่ ดังนั้นถ้ามีเลขซ้ำกัน เช่น copy vm จากในเครื่องมาสร้างเป็น vm ตัวใหม่อีกตัวหนึ่ง  ตัว Virtual box  จะไม่ยอมให้ add vdi เข้าระบบ  ในกรณีนี้ให้สั่งคำสั่ง  vboxmanage internalcommands  sethduuid  < image.vdi>
   <table class="table table-bordered">
         <td>
            # vboxmanage internalcommands sethduuid image.vdi
         </td>
   </table>
เพื่อเปลี่ยนเลข UUID  ให้ไม่ซ้ำกัน    และใน virtualbox เวอร์ชั่นใหม่ สามารถเลือก clone vm ออกมาเป็นตัวใหม่ได้เลย โดยการคลิกขวาตัว VM ที่ต้องการ clone และเลือก clone ได้เลย  แต่ตัวไฟล์ที่ clone มานั้นจะอยู่ใน home directory ของ user ที่สร้างนั้น ๆ ไม่สามารถกำหนดไว้ path อื่นได้ 

5. ในการนำ template ไปสร้าง vm ตัวใหม่ ก็ให้สร้าง VM เหมือนปกติ แต่จังหวะสร้าง virtual harddisk ให้ browse เลือกไปที่ template ที่ copy มา  ก็จะประหยัดเวลาในการติดตั้ง OS