---
title: 'TeamViewer - Multi Platform Remote Access Connection via internet'
date: 2010-10-19T10:42:56+07:00
draft: false
---
ในการดูแลเครื่อง หลาย ๆ platform นั้น ไม่ว่าจะเป็น Windows , Mac , Linux ซึ่งในการดูแลเครื่องเหล่านั้นถ้าต้องการ Remote Access เพื่อให้เข้าถึงหน้าเครื่องนั้น ในแต่ละ platform ก็จะใช้โปรโตคอล และ tools ที่ต่างกัน เช่น Windows ใช้ RDP  , Linux ใช้ VNC  และอาจมีปัญหาอื่น ๆ เช่น พอร์ตที่เครื่องไม่ได้เปิดไว้ , ติด firewall เครื่อง หรือปัญหาอื่น ๆ  

TeamViewer นั้นจะเป็น tools ที่ใช้ในการ remote desktop ผ่าน internet ซึ่งมีในหลาย ๆ platform ซึ่งสามารถทำงานร่วมกันได้ ไม่ว่าจะเป็น Windows, Mac , Linux และ iphone

ซึ่งในการทำงานที่เครื่องที่ต้องการให้รีโมทไปนั้นจะต้องทำการรันโปรแกรม TeamViewer ขึ้นมาก่อน ซึ่งตัวโปรแกรมนั้นจะไปติดต่อกับ Server ของ TeamViewer เพื่อ generate session ของเครื่องขึ้นมาซึ่งจะทำการแจ้ง ID และ Password กลับมายังหน้าต่างของ TeamViewer  ที่หัวข้อ Wait for Session จากนั้นก็ทำการแจ้ง ID และ Password ไปยังผู้ที่ต้องการจะ remote มายังเครื่อง   ผู้ที่จะรีโมท เมื่อได้ ID และ password แล้วให้เปิดโปรแกรม TeamViewer ขึ้นมา ที่หน้าต่าง Create Session ID ให้ทำการใส่เลข ID และคลิก connect to partner  จากนั้นทำการใส่ password ก็จะสามารถเข้าถึงหน้าจอของเครื่อง remote ได้

ท่านสามารถ download teamviewer ได้ที่ http://www.teamviewer.com

