---
title: 'การติดตั้ง PDF Printer for Ubuntu'
date: 2010-01-18T08:05:19+07:00
draft: false
---
การทำไฟล์ PDF บน Ubuntu นั้น  สามารถทำได้ง่าย ๆ เปรียบได้กับการ print เอกสารธรรมดา ๆ
ถ้าอยากรู้วิธีทำ ตามมาเลยครับ

PDF file เป็นไฟล์ที่ใช้แพร่หลายในปัจจุบัน เหมาะสำหรับการส่งเป็นเอกสารเพื่ออ่านและพิมพ์ เนื่องจากรูปแบบที่จัดไว้จะไม่เพี้ยน เปิดไฟล์ที่ใหนก็จะเห็นเหมือนกัน  ซึ่งถ้าเราต้องการที่จะทำไฟล์ pdf  จากโปรแกรมต่าง ๆ บน Ubuntu นั้น สามารถทำได้ง่าย ๆ เปรียบเทียบไปก็เหมือนกับการ print ออกมาจาก printer แต่แทนที่เราจะพิมพ์ลงกระดาษ เราก็พิมพ์เป็น pdf file แทน

ขั้นแรก
install cups-pdf from repository โดย สั่ง
<table class="table table-bordered">
      <td>
        ~$ sudo apt-get install cups-pdf
      </td>
</table>

จากนั้นไปที่  System -> Administration -> Printing กด new printer เลือก Print into PDF File

PDF Printer (Virtual Printer) คลิ๊ก Forward

Manufacturer -> Generic

Model -> postscript color

Driver -> Standard

คลิ๊ก Forward

ตั้งชื่อ Name -> PDF_Printer (ตั้งเป็นอะไรก็ได้แต่ชื่อไม่ให้มีช่องว่าง)

Apply เสร็จ


เวลาสั่ง print งาน จาก PDF Printer  ไฟล์ pdf ที่ได้จะอยู่ที่ 
home directory/pdf/