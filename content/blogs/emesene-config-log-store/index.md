---
title: 'config ให้ emesene เก็บ conversation log ได้ บน ubuntu'
date: 2010-11-10T14:52:36+07:00
draft: false
---
emesene เป็นโปรแกรม Instant Messeging ตัวหนึ่งที่ใช้ทำงานแทน Windows Live Messenger ซึ่งหน้าตาของโปรแกรมนั้นมีความคล้ายคลึงกับ Windows Live Messenger เป็นอย่างมากทำให้ผู้ใช้งานไม่ต้องปรับตัวใช้งานมากนัก emesene ข้อดีคือ เร็ว และกินทรัพยากรต่ำกว่า WLM และสามารถรันได้บนหลาย ๆ platform ไม่ว่าจะเป็น Windows, OSX , Linux ค่ายต่าง ๆ เช่น Ubuntu , Fedora , Debian

ซึ่งโดยปกตินั้น ตัว emesene นั้นจะไม่เก็บข้อความสนทนา (conversation log) แต่ถ้าเราต้องการจะให้ตัวโปรแกรมนั้นสามารถเก็บ conversation log ได้ เราจะต้อง config เพิ่มเติม ดังนี้
ขั้นแรก ให้ทำการคัดลอก source code โปรแกรม logconversation.py จาก
http://www.java2s.com/Open-Source/Python/Network/emesene/emesene-1.6.2/plugins_base/LogConversation.py.htm
และเซฟไว้เป็นชื่อ LogConversation.py  หรือ dowload ได้  <a href="http://www.clusterkit.co.th/techblog/logconversation.py"> **ที่นี่**</a> จากนั้นเปิดโปรแกรม emesene และ login เข้าใช้งาน <br>
ไปที่ option -> plugin คลิกที่ปุ่ม Install และ browse ไฟล์ไปยังไฟล์ LogConversation.py ที่เก็บไว้ จากนั้นให้คลิกที่ plugin  2 ตัว คือ  logger และ Conversation Logger
เมื่อเลือกเรียบร้อยให้คลิกปุ่ม close

เท่านี้ emesene ก็จะทำการเก็บ log โดยจะเก็บไว้ที่
~/.config/emesene/<yourmail>/html_logs

