---
title: 'แปลงไฟล์ text ที่ encode ด้วย ANSI จาก Windows เป็น UTF8 เพื่อให้อ่านภาษาไทยได้ไม่เพี้ยน'
date: 2012-11-21T09:39:19+07:00
draft: false
---
ในการรับส่งไฟล์ txt ระหว่าง windows และ ubuntu มักจะเจอปัญหาอ่านภาษาไทยไม่ได้จากไฟล์ที่เซฟมาจาก notepad บน windows
ซี่งโดย default นั้น notepad บน Windows นั้นเมื่อจะทำการเซฟไฟล์ จะมี encoding เป็น ANSI เป็น default setting  เมื่อนำไฟล์มาเปิดบน Ubuntu จะมีปัญหา ไม่สามารถอ่านภาษาไทย กลายเป็นตัวอักษรประหลาด เนื่องจาก default ของ text editor บน ubuntu จะใช้ UTF8 เป็น default encoding ดังนั้นเราจึงต้องใช้ encoding เป็น UTF8 เพื่อให้ encoding เหมือนกัน สามารถเปิดไฟล์อ่านได้อย่างไม่มีปัญหา  แต่ถ้าไฟล์ที่ส่งมาไม่ได้เข้ารหัสเป็น UTF8 จะต้องทำการแปลงไฟล์ ให้เป็น UTF8 เหมือนกันก่อน จึงจะสามารถอ่านไฟล์ได้
โดยเราจะใช้ คำสั่ง iconv ช่วยในการแปลงไฟล์ ให้ encoding เป็น UTF8 โดยให้ทำดังนี้

1. เปิด terminal ขึ้นมา

2. สั่งคำสั่ง iconv ตามด้วย option ดังนี้
<table class="table table-bordered">
      <td>
        # iconv -f tis620 -t utf8 -o <new filename> <source file>
      </td>
</table>
      
     โดย -f คือ encode ของต้นทาง ซึ่งภาษาไทยจะใช้ tis620 เป็น encoder 
-t คือ encode ของปลายทาง ที่จะแปลง ซึ่งกำหนดให้เป็น UTF8

            <new filename> คือ ชื่อไฟล์ปลายทางที่แปลงเรียบร้อยแล้ว
            <source file> คือ ไฟล์ต้นทางที่จะแปลงไฟล์

ซึ่งเมื่อเราแปลงไฟล์ ให้เปิดไฟล์ดูจะเห็นว่าสามารถอ่านภาษาไทยในไฟล์ได้แล้ว