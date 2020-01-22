---
title: 'Rocks Cluster reinstall compute node เมื่อเปลี่ยน hardware เป็นเครื่องใหม่'
date: 2012-11-07T13:41:02+07:00
draft: false
---
เนื่องจากในระบบ rocks cluster นั้น ตัวข้อมูลต่าง ๆ ของเครื่องจะถูกเก็บไว้ในฐานข้อมูล ซึ่งรวมถึงเลข MAC Address ของการ์ด LAN แต่ละใบด้วย ซึ่งถ้าเครื่อง compute เกิดมีปัญหา จนต้องเปลี่ยนเครื่องใหม่หรือเปลี่ยนการ์ดแลนใบใหม่แล้ว ตัว MAC Address ของการ์ด ก็จะไม่ตรงกับในฐานข้อมูล  จึงต้องทำการลบข้อมูลเดิมของเครื่องและติดตั้งเครื่องใหม่  โดยทำดังนี้

### ขั้นตอนการติดตั้งใหม่
#### FrontEnd  
    ให้ log in เข้าระบบโดยเป็น root และเปิด shell terminal ขึ้นมา

#### 1. สั่ง rocks list hosts แล้วจดค่า rack และ rank ของเครื่อง compute < compute-0-0> เก็บไว้
   <table class="table table-bordered">
         <td>
            # rocks list hosts
         </td>
   </table>
    
#### 2. สั่ง rocks list hosts interface แล้วจดค่า IP Address ของเครื่อง compute < compute-0-0> เก็บไว้ 
  <table class="table table-bordered">
         <td>
            # rocks list hosts interface 
         </td>
   </table>
    
#### 3. สั่ง insert-ethers --remove compute-x-x เพื่อลบค่าเก่าของเครื่อง compute-0-0 ออกจากระบบ
   <table class="table table-bordered">
         <td>
            # insert-ethers --remove compute-0-0
         </td>
   </table>
    
#### 4. สั่ง rocks list host ดูว่าไม่มีเครื่อง compute-0-0 อยู่ใน list แล้ว
    
   <table class="table table-bordered">
         <td>
            # rocks list hosts
         </td>
   </table>

#### 5. ติดตั้ง compute ใหม่ด้วยคำสั่งด้านล่างนี้โดยเอาค่า rack rank และ ip ที่จดไว้มาแทนค่าใน option ด้านล่างนี้
   <table class="table table-bordered">
         <td>
            # insert-ethers --hostname compute-0-0 --cabinet 0 --rack 0 --rank 0 --ipaddr 172.16.255.254
         </td>
   </table>
    และเลือกการติดตั้งเป็น compute แล้วเปิดค้างไว้

#### Compute
ที่เครื่องลูกให้เปิดเครื่อง เลือกบู๊ตจาก network รอจนติดตั้งสำเร็จให้กลับไปที่เครื่อง FrontEnd ออกจากหน้าจอ insert-ethers  โดยกด F8 เพื่อปิดหน้าต่างลง

เท่านี้ก็จะเสร็จสิ้นการติดตั้งเครื่อง compute กับ hardware ตัวใหม่