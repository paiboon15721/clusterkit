---
title: 'เซ็ตเวลาให้ตรงด้วย ntpdate'
date: 2010-08-14T23:06:39+07:00
draft: false
---
เนื่องจากเครื่องมีปัญหานิดหน่อย  ทำให้เวลาในเครื่องผิดเพี้ยนไป  ถ้าเครื่องเราต่ออินเทอร์เน็ตอยู่ มีวิธีง่าย ๆ ในการเซ็ตเวลาให้ตรงกับมาตรฐาน  ซึ่งวิธีนี้น่าจะใช้ได้กับ linux / Unix ส่วนใหญ่เหมือนกัน
วิธีง่าย ๆ ที่จะตั้งเวลาให้ตรงมาตรฐาน
เพียงเราเปิด terminal ขึ้นมา และสั่งคำสั่ง ntpdate < time server >
<table class="table table-bordered">
      <td>
        ~$ sudo ntpdate time.navy.mi.th
      </td>
</table>
     

เพียงเท่านี้ เราก็จะตั้งเวลาให้ตรงกับ time server ที่เราเลือกแล้ว ซึ่งเราสามารถเลือก server ที่เราจะตั้งเวลาให้ตรงกับ server นั้น ๆ ได้ แต่ถ้าจะตั้งเวลาในประเทศไทยนั้น ผมแนะนำ server ของ ทหารเรือ (time.navy.mi.th , time2.navy.mi.th , time3.navy.mi.th )
time server ชุดนี้ดูแลโดย กรมอุทกศาสตร์ กองทัพเรือ ซึ่งเป็นหน่วยงานในการจัดการและดูแลเกี่ยวกับเวลามาตรฐานประเทศไทย

เกร็ดข้อมูล - หน่วยหลักสำหรับนับเวลาที่ใช้อยู่ในปัจจุบันกำหนดให้ 1 วินาที เท่ากับ ความถี่ 9,192,631,770 รอบของปรมาณูธาตุซีเซียม 133 (Cesium 133)