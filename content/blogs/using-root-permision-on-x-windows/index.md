---
title: 'การใช้สิทธิ์ root บน X-Window (graphic mode)'
date: 2010-01-16T09:08:+07:00
draft: false
---
ในบางครั้งถ้าเราต้องการใช้สิทธิ์ root ในการทำงานบนระบบ X-Window  เราสามารถใช้สิทธิ์ root ได้โดยการใช้การทำ sudo บน graphic mode สามารถทำได้ 2 วิธี คือ  

วิธีที่ 1 เปิด terminal >> พิมพ์ sudo nautilus

วิธีที่ 2 กด Alt+F2 จะปรากฏหน้าต่าง Run Application >> พิมพ์ GKSU nautilus


เมื่อกด Enter จะได้หน้าต่างที่มีสิทธิ์ root  (เหมือนการใช้ sudo แปลงสิทธิ์ ใน command line)

