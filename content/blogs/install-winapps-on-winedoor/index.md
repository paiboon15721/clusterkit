---
title: 'ติดตั้ง winapps ง่าย ๆ สไตล์ Wine Door'
date: 2010-04-26T15:03:29+07:00
draft: false
---
Wine-door เป็นโปรแกรมติดตั้งโปรแกรมทางฝั่งวินโดว์เพื่อใช้งานบน Linux โดยผ่าน Graphic Interface ทำให้ง่ายในการติดตั้งโปรแกรม   ซึ่งการทำงานของ wine-door นั้นจะคล้าย ๆ กับโปรแกรม synaptic package manager หรือ Ubuntu Software Center โปรแกรม wine-door นั้น สามารถดาวน์โหลดได้ที่ https://pkgs.org/download/wine-doors


ซึ่งการติดตั้งนั้น ตัว wine-door ต้องการ package ที่จำเป็นต้องใช้คือ

- Wine
- cabextract, tar, gzip, bzip, unzip
- python-gnome2-desktop >= 2.16 (python rsvg support, Debian/Ubuntu package, might differ on other systems)
- python >= 2.4
- python2.4-cairo >= 1.2.0
- libcairo2 >= 1.2.4
- python-libxml2
- python-glade2

ซึ่งการใช้งานนั้นเมื่อเปิดโปรแกรม wine-door ขึ้นมา ตัว wine-door จะ list รายชื่อ โปรแกรมที่อยู่ใน database ของ wine-door ที่สามารถติดตั้งได้  ซึ่งเพียงเราคลิกเลือก Install ที่ตัวโปรแกรมที่ต้องการ หลังจากเลือกแล้วกดปุ่ม apply ทางด้านล่าง จากนั้นก็รอให้ตัว wine-door ดาวน์โหลดโปรแกรมและติดตั้งโปรแกรมให้  เมื่อติดตั้งเสร็จกดปุ่ม close เพื่อปิด wine-door หลังจากนั้นเราก็พร้อมไช้งานโปรแกรมได้เลย