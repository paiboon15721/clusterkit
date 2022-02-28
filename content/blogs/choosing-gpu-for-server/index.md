---
title: 'การเลือก GPU ใส่เครื่อง Server หรือ Workstation'
date: 2022-02-28T14:54:30+07:00
draft: false
---
ปกติการ์ด GPU นั้นจะแบ่งตาม Segment ตามตลาด เช่น PC, Workstation, DataCenter โดยแบ่งแยกตามเบอร์ Chip GPU โดยจะมีจำนวนและความเร็วของ Cuda/Tensor/RT Core และ RAM แตกต่างกันไปตามรุ่น โดย GPU สถาปัตยกรรมรุ่นล่าสุดของ Nvidia คือ Ampere แม้จะใช้สถาปัตยกรรมเดียวกัน แต่การ์ด ก็จะถูกแยกกันตาม segment ของ product 

### Products using Ampere
#### GeForce 30 series
* GeForce RTX 3050 (GA106)
* GeForce RTX 3060 (GA106)
* GeForce RTX 3060 Ti (GA104)
* GeForce RTX 3070 (GA104)
* GeForce RTX 3070 Ti (GA104)
* GeForce RTX 3080 (GA102)
* GeForce RTX 3080 12GB (GA102)
* GeForce RTX 3080 Ti (GA102)
* GeForce RTX 3090 (GA102)
* GeForce RTX 3090 Ti (GA102)

#### Nvidia Workstation GPUs (formerly Quadro)
* RTX A2000 (GA106)
* RTX A4000 (GA104)
* RTX A4500 (GA102)
* RTX A5000 (GA102)
* RTX A6000 (GA102)

#### Nvidia Data Center GPUs (formerly Tesla)
* Nvidia A2 (GA107)
* Nvidia A10 (GA102)
* Nvidia A16 (4 × GA107)
* Nvidia A30 (GA100)
* Nvidia A40 (GA102)
* Nvidia A100 (GA100)
* Nvidia A100 80GB (GA100)

ส่วนใหญ่ GPU ในกลุ่ม Data Center (Tesla) และ Workstation (Quadro RTX) ในแบรนด์ใหญ่ ๆ หรือแบรนด์รอง เช่น HPE, HP, Dell, Supermicro จะมีการรับรอง (Certified) ว่าสามารถใส่กับกับเครื่อง Server หรือ Workstation รุ่นนั้น ๆ ได้ โดยการ์ด GPU ที่ใส่ในเครื่อง Server จากแบรนด์หลัก ๆ เช่น HPE, DELL ถ้าติดตั้งมาพร้อมเครื่อง ประกันจะรวมกันกับเครื่อง

<b>หากมีแผนติดตั้ง GPU เพิ่มเติมในเครื่องภายหลัง</b> หรือซื้อการ์ดมาใส่เอง <u>จะต้องเผื่อขนาดของ Power Supply เพื่อจ่ายไฟให้กับ GPU ให้พอเพียง และต้องสั่ง Cable สายไฟจ่ายให้ GPU ตั้งแต่สั่งเครื่องครั้งแรกมาก่อนเลย และเมื่อสั่ง part GPU มา หากมีปัญหาต้องถอด GPU ไปเคลมแยกต่างหาก ประกันจะไม่รวมกับเครื่อง</u> โดยทั่วไป GeForce 30 series จะเป็นการ์ดในกลุ่มของ Gaming PC ซึ่งจะไม่ Certified ในเครื่อง Workstation หรือ Server

#### Geforce RTX กับเครื่อง Server
โดยทั่วไป GPU ใน Series Geforce RTX นั้น ไม่ได้ถูก Certified กับ Server หรือ Workstation ส่วนใหญ่จะมี Certified กับ PC รุ่นใหญ่บางรุ่นเท่านั้น หากต้องการนำ Geforce RTX มาใช้บน Server หรือ Workstation จริง ๆ มีเรื่องที่ต้องสนใจและควรรระวังอยู่หลาย ๆ เรื่อง คือ

#### Server Support GPU
ตรวจสอบเอกสารเครื่อง Server ว่ารองรับ GPU หรือไม่ หาก Support ก็ยังมีโอกาสที่เครื่องจะใส่การ์ด GPU Geforce RTX ได้ โดยส่วนใหญ่เครื่อง Server ที่ support GPU จะมีพื้นที่ว่างใส่การ์ด GPU เป็นขนาด Full Height Full length (FHFL) 
โดยจะมีขนาดความสูง (height) x ความยาว (length) = 120 mm x 312 mm
และความหนา (width) ของ 1 slot = 20.32 mm

{{< image src="blogs/choosing-gpu-for-server/pcie-bracket-height.png" title="" >}}

{{< image src="blogs/choosing-gpu-for-server/pci-card-type.png" title="" >}}

Power Supply and Power Connector
ในกรณีการ์ด GPU ที่ใส่ในเครื่อง Server จากแบรนด์หลัก ๆ เช่น HPE, DELL หากต้องการติดตั้งการ์ด GPU เพิ่มเติมนั้น จะต้องวางแผนเลือกรุ่นที่ Support การใส่ GPU เพราะว่าจะออกแบบพื้นที่ว่างสำหรับ GPU และ Power Connector สำหรับต่อกับ GPU ถ้าเป็นรุ่นที่ไม่ Support อาจจะใส่ได้ แต่ไม่มี Connector ต่อไฟเลี้ยง GPU เพิ่มและเลือก Power Supply เพื่อจ่ายไฟให้กับ GPU ให้พอ (แนะนำเลือกเป็นตัวที่จ่ายไฟได้สูงสุด) และต้องสั่ง Power Connector Cable ที่จ่ายให้ GPU เผื่อตั้งแต่สั่งเครื่องครั้งแรกมาก่อนเลย เนื่องจาก Part พวกนี้จะสั่งที่หลังมาเพิ่มเติมไม่ได้ และตรวจสอบอัตราการกินไฟของการ์ด GPU ที่ต้องการว่าเครื่องจ่ายได้ไหวหรือไม่ และอีกส่วนหนึ่งก็คือ Power connector ที่ต้องจ่ายไฟเพิ่มให้กับ GPU ซึ่งต้องดูว่าเป็น Connector แบบใด 6Pin, 8Pin หรือ 12Pin โดยเครื่อง Server คิดว่าน่าจะ Provide เป็น 8Pin มา หากใส่ GPU รุ่นที่ต้องการไฟแบบ 6 Pin ก็จะต้องหาสาย Convert จาก 8Pin ลงมาเป็น 6Pin

{{< image src="blogs/choosing-gpu-for-server/connector.png" title="" >}}

ตัวการ์ด GPU Geforce RTX ในปัจจุบันนั้นจะมีขนาดความยาวและความสูงของ GPU ไม่ได้มีขนาดตามมาตรฐาน (FHFL) มีโอกาสที่ GPUจะมีความยาวกว่าพื้นที่ใน RACK และจะใส่การ์ดไม่ได้ และอีกส่วนคือการออกแบบพัดลมระบายอากาศขนาดใหญ่บนการ์ด ทำให้บางการ์ด GPU อาจใช้พื้นที่ถึง 3 Slot ดังนั้นต้องตรวจสอบเครื่อง Server ก่อนว่ามีพื้นที่พอสำหรับเสียบการ์ด GPU หรือไม่ แนะนำให้หาข้อมูลความยาวการ์ด GPU ไม่เกิน 32 cm หรือพิจารณาการ์ด Quadro RTX A series แทน

{{< image src="blogs/choosing-gpu-for-server/geforce-rtx-3090-shop-630-d@2x.png" title="" >}}
<center>source: https://www.nvidia.com/en-us/geforce/graphics-cards/30-series/rtx-3090</center>
<br>

หรืออีกทางเลือกก็คือการสั่งประกอบเครื่อง Workstationn หรือ Server โดยใส่ GPU เข้าไป ซึ่งจะ Customize ได้ดีกว่าการใช้แบรนด์หลักมาก บางโมเดลสามารถใส่ได้ถึง 4 GPU บนเครื่อง Server 1 U







