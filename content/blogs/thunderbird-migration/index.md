---
title: 'Thunderbird Migration to new machine'
date: 2010-01-18T11:41:47+07:00
draft: false
---
Mozila Thunderbird เป็น e-mail client ตัวหนึ่งที่เป็นที่นิยมในปัจจุบัน  ซึ่งจะเป็นการดึงอีเมลจาก mail server ลงมาเก็บไว้ในเครื่อง ซึ่งถ้าเราต้องการย้ายอีเมลทั้งหมดไปยังเครื่องใหม่ เราจะทำได้อย่างไร

การย้ายทำได้โดย

1. ขั้นแรกให้แบ็คอัพไฟล์อีเมลของ Thunderbird  โดย path ของไฟล์อีเมล จะอยู่ที่

XP : c:\Documents and Settings\[User Name]\Application Data\Thunderbird\Profiles\ [folderName.default]

VISTA: c:\Users\[User Name]\AppData\Roaming\Thunderbird\Profiles\[folderName.default]

2. ขั้นต่อไปทำการ install  mozilla Thunderbird ลงในเครื่องใหม่ ตามปกติ

3. copy ไฟล์ e-mail ที่ backup กลับไปวางไว้ที่ path ที่เรา backup มาในขั้นตอนแรก

4. แก้ไขไฟล์ profiles.ini ซึ่งไฟล์จะอยู่ที่  C:\Users\clusterkit\AppData\Roaming\Thunderbird

โดยแก้ไขบรรทัด Path=C:\Users\[User Name]\AppData\Roaming\Thunderbird\Profiles\ [folderName.default]

โดยแก้ไขชื่อ [folderName.default] ให้เป็นชื่อโฟลเดอร์ที่เรา copy backup กลับมา  เมื่อแก้แล้วให้เซฟกลับไป

เพียงเท่านี้ เราก็สามารถย้ายเมล์ทั้งหมดไปเครื่องใหม่ได้แล้ว

*วิธีนี้สามารถใช้ย้ายจาก thunderbird2 ไป thunderbird3 ได้ด้วย ^^