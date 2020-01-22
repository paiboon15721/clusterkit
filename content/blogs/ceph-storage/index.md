---
title: 'Ceph Storage'
date: 2019-06-19T17:15:24+07:00
draft: false
---

Software-Defined Storage เป็นคำนิยามหนึ่งของฝั่ง Storage ที่เริ่มเป็นที่นิยมหลักการคือการนำเครื่อง คอมพิวเตอร์หรือเซอร์เวอร์หลาย ๆ เครื่อง มาติดตั้งซอฟต์แวร์เพื่อให้บริการเป็นระบบจัดเก็บข้อมูล แทนที่จะต้องซื้อระบบ Storage แบบเดิม ๆ ที่มีราคาแพงกว่า เมื่อมีปัญหาก็ต้องเรียก Vender มาแก้ไข ไม่สามารถดูและระบบเองได้ จะขยายระบบเพิ่มก็ต้องซื้อของจาก Vender เดียวกัน

ซึ่งในตลาดก็มีซอฟต์แวร์หลาย ๆ ตัว ที่เป็น SDS ทั้งที่เป็น Open Source และ Propietory Software สามารถให้บริการเป็น NAS หรือ SAN แทนระบบ Storage แบบเดิมได้ ซึ่งบทความนี้จะแนะนำซอฟต์แวร์ที่ชื่อ Ceph ตัว Ceph มีความแตกต่างจากซอฟต์แวร์ตัวอื่น โดย Ceph เป็น Open Source Software ที่สามารถให้บริการเป็น NAS, SAN หรือ Object Storage ซึ่งเป็นจุดเด่นที่ยังไม่เจอในซอฟต์แวร์ตัวอื่น ๆ

{{< image src="/imgs/blogs/ceph-2.png" title="Software Comparison" >}}

## ความเป็นมาของ Ceph

{{< image src="/imgs/blogs/ceph-1.png" title="Ceph Logo" >}}

Ceph เป็นซอฟต์แวร์ทำ Software-Defined Storage ที่เป็น Open Source ได้รับความนิยมติดตั้งเป็น Backend การเก็บข้อมูลในระบบ OpenStack และมีขนาดของ community ที่ใหญ่ขึ้นเรื่อย ๆ

ชื่อของ Ceph นั้นมาจากคำว่า "cephalopod" ซึ่งเป็นสัตว์ในตระกูลปลาหมึก (Octopus and squid) Ceph นั้นเริ่มต้นโดย Sage Weil ในปี 2003 โดยเป็นส่วนหนึ่งของวิทยานิพนธ์ (PhD project) ณ University of California, Santa Cruz โดยสำเร็จในปี 2007.
ในปี 2012 Sage Weil ได้ก่อตั้งบริษัท Inktank ขึ้นมาเพื่อทำธุรกิจให้บริการ support ซอฟต์แวร์ Ceph ในระดับ Enterprise โดยเป็นทั้งผู้ก่อตั้ง และ CTO ของบริษัทฯ และถูก Red Hat ซื้อไปในปี 2014 ด้วยราคา $175 Million

ปัจจุบัน Sage Weil ทำงานที่ Red Hat ในฐานะ Ceph Principal Architect และเป็น Chief Architect ของโครงการ Ceph Update : ปัจจุบัน Red Hat ได้ถูกซื้อกิจการไปอยู่กับ IBM ด้วยราคา $34 Billion

## Ceph Architecture

{{< image src="/imgs/blogs/ceph-3.png" title="Ceph Architecture" >}}

Ceph จะประกอบด้วยส่วนประกอบหลัก ๆ 3 ส่วน คือ

1. MON (Monitor Node)ทำหน้าที่ดูแลสถานะของ Ceph cluster
2. OSD (Object Storage Node) เป็น Node ทำหน้าที่เก็บข้อมูล ของระบบ หากต้องการใช้ CephFS จะต้องมี
3. MDS (Metadata Node) ทำหน้าที่ดูแลสถานะของ file hierarchy (สำหรับ CephFS เท่านั้น)

MON และ MDS สามารถทำ High Availablity ได้ โดยการติดตั้ง MON ขั้นต่ำ 3 ตัว ส่วน MDS ติดตั้งเป็นแบบ Active/Stand by

ในคลัสเตอร์ Ceph การติดต่อกันระหว่าง MON, MDS และ OSD นั้นจะติดต่อผ่าน Public Network ในวง Cluster Network จะใช้ในการ Replication ข้อมูลระหว่าง OSD เท่านั้น หากดีไซน์แบบประหยัดก็สามารถตัด Cluster Network ออกไปได้ ระบบยังสามารถทำงานได้ แต่จะกระทบจังหวะที่มีการ Replication ข้อมูลระหว่าง OSDs หนัก ๆ จะทำให้ระบบช้าลงได้

## Version

เวอร์ชั่นล่าสุด ณ ปัจจุบัน (มกราคม 2019) จะเป็นเวอร์ชั่น Mimic (v13.2.0) — on June 1, 2018 โดยทาง Ceph มีแผนที่จะปล่อยเวอร์ชั่นใหม่ ทุก ๆ 9 เดือน โดยประมาณ Version number จะแยกได้คือ

- x.0.z — development (for early testers)
- x.1.z — release candidates (for test clusters)
- x.2.z — stable/bugfix (for users/production)

โดยการเลือกใช้งาน Ceph นั้น แนะนำให้เลือกเป็น Stable Version คือ Version.2.x

## การใช้งานระบบ

การให้บริการ สำหรับ Client ที่เข้ามาใช้งานในระบบโดยตรง จะต้องมี Kernel ที่สนับสนุน Ceph มีเบอร์ IP วงเดียวกับ Ceph สามารถติดต่อตรงกับเครื่องในระบบ Ceph ได้ ถ้าต้องการให้บริการ Windows หรือ Clients อื่น ๆ ที่ไม่ได้เป็น Linux จะต้องทำ Gateway เช่น rados gateway และให้เครื่องติดต่อมาที่ gateway หากเป็น CephFS ก็ mount CephFs และแชร์ผ่าน SAMBA ออกไปให้เครื่อง Windows สามารถใช้งานพื้นที่ Ceph ได้

## ข้อดี-ข้อเสีย ของ Ceph

- เป็น Open source ไม่มีค่าใช้จ่ายสำหรับตัวซอฟต์แวร์ แต่หากต้องการ Support ก็จะมี subscirption ของ Vender หลาย ๆ ค่าย เช่น RedHat, SuSe ขายอยู่เช่นกัน
- สามารถให้บริการได้หลากหลายรูปแบบ (Block, Object, Filesystem)
- สามารถขยายระบบได้ง่าย เพียงเติมเครื่องเข้าระบบ
- ใช้ Hardware ทั่ว ๆ ไป ไม่จำเป็นต้องเป็น Hardware เฉพาะแต่ละส่วนมีความคงทนของระบบ (High Availability) ไม่ว่าจะเป็น MON, MDS หรือ OSD

ข้อเสียที่ชัดที่สุดของ Ceph นั้นจะเปลืองดิสก์กว่า Storage แบบปกติ เนื่องจากเทคโนโลยีในการเก็บ ข้อมูลของ Ceph ที่จะเก็บสำเนาของข้อมูลไว้ 2–3 ชุด สำหรับ High Availablity เพื่อให้มั่นใจว่าถ้า บางเครื่องในระบบมีปัญหาจะยังคงสามารถอ่านเขียนข้อมูลจาก Ceph ได้ โดยไม่ต้องปิดระบบ แต่ในเวอร์ชั่นใหม่ ๆ ก็มีการพัฒนาการจัดเก็บแบบ Erasure Coding สำหรับการเก็บแบบ Archive ที่ไม่ได้อ่านเขียนบ่อย โดยจะเปลี่ยนการเก็บข้อมูลคล้าย ๆ RAID ซึ่งจะเก็บข้อมูลได้มากกว่า

{{< image src="/imgs/blogs/ceph-4.png" title="Ceph Erasure Coding" >}}

## Real Case — Ceph Cluster Store Data for Windows Client

เป็นระบบ Ceph Cluster ขนาดประมาณ 500TB จำนวณ 45 เครื่อง ให้บริการ File System แก่ Client ที่เป็น Windows และมีการ Authenticate ผ่าน Active Directory Server

{{< image src="/imgs/blogs/ceph-5.png" title="Ceph Cluster Store Data for Windows Client" >}}

## ผลงานที่ผ่านมา

- สำนักงานพัฒนาเทคโนโลยีอวกาศและภูมิสารสนเทศ (องค์การมหาชน)
- SiS Distribution (Thailand) PCL.
