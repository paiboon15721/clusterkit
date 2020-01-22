---
title: 'แชร์เครื่องพิมพ์บน Ubuntu เพื่อทำให้ Windows สามารถสั่งพิมพ์เอกสารได้'
date: 2010-02-17T16:36:01+07:00
draft: false
---

ท่านสามารถติดตั้งเครื่องพิมพ์บนระบบปฏิบัติการ Ubuntu พร้อมทั้งแชร์เครื่องพิมพ์ให้กับระบบปฏิบัติการ Windows เข้าใช้งานเครื่องพิมพ์ได้ด้วย ซึ่งมีวิธีด้งนี้

เครื่อง Ubuntu ที่ต้องการแชร์เครื่องพิมพ์ (Print Server)
ก่อนอื่นต้องนำเครื่องพิมพ์มาเชื่อมต่อกับเครื่องที่เป็น Ubuntu ก่อน แล้วติดตั้งไดรเวอร์ของเครื่องพิมพ์ตามขั้นตอนดังนี้

### 1. ติดตั้งเครื่องพิมพ์ที่เครื่อง Ubuntu

1.1 ไปที่เมนู System>Administration>Printing

1.2 คลิกปุ่ม New ระบบจะค้นหาเครื่องพิมพ์ที่เชื่อมต่อ

1.3 เลือกเครื่องพิมพ์ที่ต้องการ พร้อมติดตั้งไดรเวอร์ # ติดตั้ง samba เพื่อแชร์เครื่องพิมพ์ให้กับ Windows

### 2. อัปเดต package

<table class="table table-bordered">
      <td>
         # apt-get update
      </td>
</table>

### 3. ติดตั้ง samba

<table class="table table-bordered">
      <td>
        # apt-get install samba smbfs
      </td>
</table>
 
### 4. ปรับแต่งไฟล์ smb.conf
<table class="table table-bordered">
      <td>
        # nano /etc/samba/smb.conf
      </td>
</table>
 
### 5. แก้ไขตามด้านล่าง 
<table class="table table-bordered">
      <td>
        [printers] <br>
        comment = All Printers <br>
        browseable = yes <br>
        path = /var/spool/samba <br>
        printable = yes <br>
        guest ok = yes <br>
        read only = yes <br>
        create mask = 0700 <br>
    <br>
        # Windows clients look for this share name as a source of downloadable <br>
        # printer drivers <br>
        [print$] <br>
        comment = Printer Drivers <br>
        path = /var/lib/samba/printers <br>
        browseable = yes <br>
        read only = yes <br>
        guest ok = yes 
      </td>
</table>
    
### 6. รีสตาร์ท samba
<table class="table table-bordered">
      <td>
         # /etc/init.d/samba reload
      </td>
</table>
เครื่อง Windows XP (Client)

1. ไปที่เมนู Start>Run
2. พิมพ์ \\IP address ของเครื่อง ubuntu ที่แชร์เครื่องพิมพ์เอาไว้ ตัวอย่าง \\192.168.123.121 คลิกปุ่ม open
3. ถ้าเชื่อมต่อได้ จะเห็นเครื่องพิมพ์ในเครื่อง ubuntu
4. คลิกขวาที่เครื่องพิมพ์ แล้วเลือก connect
5. ติดตั้ง driver ของเครื่องพิมพ์นั้น 
6. ทดสอบการพิมพ์
