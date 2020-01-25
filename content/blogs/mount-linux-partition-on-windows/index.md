---
title: 'Mount Linux Partition on Windows'
date: 2010-04-01T10:44:48+07:00
draft: false
---
ถ้าคุณเป็นคนที่ทำงานโดยใช้ Operating System ทั้ง Windows และ Linux ท่านคงเคยเจอปัญหาที่ไฟล์ที่จะใช้งานอยู่บนอีก OS หนึ่ง จึงต้องบูตเครื่องใหม่เพื่อไปเอาไฟล์งานแค่นั้นเอง ปัญหานี้ถ้าใช้งานบน Linux คงไม่เท่าใหร่ แต่ถ้าบน Windows ล่ะ ?

Ext2IFS คือคำตอบสำหรับการ mount linux partition เพื่อให้ windows สามารถมองเห็น partition ได้ สามารถ download ได้ที่ http://www.fs-driver.org/download.html

เมื่อดาวน์โหลดมาเรียบร้อยแล้วให้ install ลงเครื่อง ซึ่งจังหวะ install นั้น จะมีหน้าต่างถามขึ้นมาว่าจะให้ map partition linux กับ drive letter อะไร เมื่อเสร็จสิ้นการ install  เราก็จะเห็น drive เพิ่มขึ้นมา ซึ่งก็คือ partition ของ linux ที่เรา map ไว้นั่นเอง

