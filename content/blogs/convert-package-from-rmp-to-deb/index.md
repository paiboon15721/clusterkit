---
title: 'Convert package from .rmp to .deb'
date: 2010-01-17T21:45:32+07:00
draft: false
---
การแปลงร่าง package ข้ามสายพันธุ์ จากฝั่ง Redhat ไปฝั่ง Debian

การแปลง package จาก .RPM เป็น .DEB

1. Install alien จาก repository
เลือกค้นหา package จาก synaptic ใส่คำว่า alien แล้วค้นหา เมื่อเจอให้คลิกเลือกแล้ว apply หรือสั่งผ่าน command line เพื่อความสะดวกสบายของชีวิต โดยพิมพ์
<table class="table table-bordered">
      <td>
        ~$ sudo apt-get install alien
      </td>
</table>

2. ย้าย .rpm ที่จะแปลงสัญชาตินั้น ย้ายไปไว้ที่ /tmp

3. สั่ง คำสั่งเพื่อแปลงสัญชาติ
<table class="table table-bordered">
      <td>
        ~$ sudo alien package.rpm
      </td>
</table>
    

4. เมื่อแปลงเสร็จจะได้ package.deb ออกมา

5. สั่ง sudo dpkg -i package.deb เพื่อ install

จากนั้นมาลุ้นกัน ว่า package ที่แปลงร่างมานี้จะ "work" รึปล่าว  :P