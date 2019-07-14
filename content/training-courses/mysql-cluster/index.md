---
title: 'Mysql Cluster'
subID: '09'
date: 2019-06-23T10:52:53+07:00
draft: false
weight: 50
totalHours: 18
totalDays: 3
price: 10700
pdfURL: 'http://www.clusterkit.co.th/training/pdf/MySQL%20Cluster.pdf'
---

## รายละเอียดหลักสูตร

เนื้อหาหลักสูตรจะกล่าวถึงทฤษฎีหลักการทำงานของระบบคลัสเตอร์ในรูปแบบต่าง ๆ ทฤษฎีและหลักการทำงานของซอฟต์แวร์ MySQL Cluster การออกแบบระบบเพื่อรองรับผู้ใช้งานจำนวนมาก เพื่อให้ระบบมีอัตราการล่ม (Downtime) ต่ำที่สุด การออกแบบด้านความปลอดภัยของงระบบ เป็นหลักสูตรที่เน้นการปฎิบัติใช้งานจริง โดยเนื้อหาครอบคลุมตั้งแต่กระบวนการออกแบบ การติดตั้ง ทฤษฎีกระจายภาระงาน (Load balancing) การสร้างระบบคงอยู่สูง (High Availability - HA) การปรับแต่งความปลอดภัยของระบบ และมีการปรับพื้นฐานทฤษฎีระบบเครือข่ายในส่วนที่เกี่ยวข้องกับ MySQL Cluster เช่น Mac Address, ARP Protocol, Public และ Private Network เป็นต้น

## หลักสูตรนี้เหมาะสำหรับ

ผู้ดูแลระบบฐานข้อมูล ระบบเว็บ องค์กรที่ให้บริการโดยใช้งานระบบฐานข้อมูล MySQL และผู้ที่สนใจ

## วัตถุประสงค์

1. เพื่อให้ผู้เข้าอบรมมีความรู้ความเข้าใจในหลักการออกแบบ MySQL Cluster
2. เพื่อให้ผู้เข้าอบรมทราบถึงความแตกต่างของวิธีการกระจายภาระงานในแบบต่าง ๆ
3. เพื่อให้ผู้เข้าอบรมสามารถนำไปประยุกต์ใช้งานได้จริง

## ความรู้พื้นฐาน

ผู้เข้าอบรมต้องมีความรู้ความสามารถในการติดตั้ง Linux Server หรือผ่านหลักสูตร Linux Administration มาก่อน เคยติดตั้งและใช้งานซอฟต์แวร์ MySQL และควรมีความเข้าใจเรื่องระบบเครือข่ายพื้นฐาน

## รูปแบบการสอน

บรรยายและปฏิบัติการ โดยใช้ระบบคอมพิวเตอร์แบบเสมือน (Virtual Machine) เพื่อต่อเป็นระบบคลัสเตอร์

## ซอฟต์แวร์ที่ใช้

1. ซอฟต์แวร์ CentOS เวอร์ชั่น 5 ขึ้นไป
2. MySQL Cluster เวอร์ชั่น 7 ขึ้นไป

## สิ่งที่ผู้เข้าอบรมต้องเตรียม

ผู้เข้าอบรมต้องเตรียมเครื่องคอมพิวเตอร์ที่มีหน่วยความจำไม่น้อยกว่า 8 GB และมีพื้นที่ว่าง (Disk space) ไม่น้อยกว่า 50GB มาในการอบรม พร้อมติดตั้ง VirtualBox และ VirtualBox Extension Pack และเปิดฟังก์ชั่น Virtualization ใน BIOS มาให้เรียบร้อยตาม{{< link url="http://www.clusterkit.co.th/training/pdf/VirtualBox_64bit_Problem.pdf" text="คู่มือ" >}}

## เนื้อหาหลักสูตร

### วันที่ 1

#### เช้า

- แนะนำเทคโนโลยีระบบคลัสเตอร์ (30 นาที)
  - รู้จักกับระบบคอมพิวเตอร์คลัสเตอร์
  - การประยุกต์ใช้งานระบบคลัสเตอร์ในด้านต่าง ๆ
- รูปแบบต่าง ๆ ของการทำ Database แบบคลัสเตอร์
- รูปแบบต่าง ๆ ของการใช้ Share Disk และ Share Storage
- รู้จักกับ MySQL และ MySQL Cluster (15 นาที)
  - กล่าวสรุปเรื่องสำคัญของระบบจัดการฐานข้อมูล MySQL
  - รู้จักกับ Storage Engine
  - รู้จักกับ NDBCLUSTER Storage engine
  - แผนการพัฒนาระบบจัดการฐานข้อมูล MySQL
- MySQL Cluster Concept (30 นาที)
  - จุดเด่นจุดด้อยของ MySQL Cluster
  - องค์ประกอบของMySQL Cluster
  - การทำงานของ MySQL Cluster
  - การทำงานในแบบ In-memory และ Disk-Bases Tables
- Pre-Workshop (60 นาที)
  - ปรับแต่งไฟล์เพื่อการใช้งานด้วยชื่อเครื่อง
  - การตั้งค่า SSH ให้ระบบคลัสเตอร์สามารถทำงานในแบบ Single Sign On ด้วยการใช้ Public key Infrastructure (PKI)
  - จัดการกับ iptables firewall สำหรับ MySQL Cluster
  - **workshop 1:** MySQL Cluster Software Installations (30 นาที)

#### บ่าย

- รู้จักกับคอนฟิกกูเรชั่นไฟล์ที่สำคัญ คือไฟล์ config.ini และไฟล์ my.cnf
- **workshop 2:** สร้างระบบ MySQL Cluster แบบง่าย ๆ (1 client, 1 mgm, 2 ndb)
  - ทบทวนคำสั่งที่เกี่ยวข้องกับระบบ MySQL Cluster
  - ทดลองสร้างฐานข้อมูลและใช้งานระบบ
  - ทดลองความสามารถด้าน High Availability
- การใช้งานคำสั่ง management client (ndb_mgm)
- การทำงานร่วมกันระหว่าง PHP และ MySQL Cluster
- **workshop 3:** ปรับแต่ง PHP ให้สามารถใช้งานร่วมกับ MySQL Cluster ได้

### วันที่ 2

#### เช้า

- การสร้างระบบแบบ No single point of failure บน MySQL Cluster (60 นาที)
- **workshop 4:** MySQL Cluster with Dual MGM Nodes
- สรุปคุณสมบัติด้าน High Availability
- รู้จักกับDisk-bases Tables (115 นาที)
  - หลักการทำงานของ Tablespace & Log File Group
  - ข้อจำกัดของ Disk table data
  - การคำนวณขนาดพื้นที่ของ Tablespace
- **workshop 5:** สร้างและใช้งาน table space and log file group
- วิธีการจัดการกับข้อมูลขนาดใหญ่
- วิธีปฏิบัติที่ดีและกรณีศึกษา

#### บ่าย

- การใช้งานคำสั่งสำคัญ ๆ ที่เกี่ยวข้อง (60 นาที)
  - Management Client tools
  - MySQL Cluster Utility Programs
- เข้าใจการทำData Partitioning (60 นาที)
- เข้าใจหลักการแบ่ง node group
- **workshop 6:** ทดลองทำData Partitioning บน MySQL Cluster
- การเพิ่มโหนดแบบ online และการทำ rolling update
- Designing Concept (45 นาที)
  - หลักการในการคำนวณพื้นที่จัดเก็บข้อมูล และ
  - การแบ่งพาร์ทิชั่นบนดิสก์สำหรับ MySQL Cluster
  - การกำหนดขนาดไฟล์สำหรับ Tablespace และ Undo Log File

### วันที่ 3

#### เช้า

- ความปลอดภัยใน MySQL Cluster
  - การออกแบบระบบเพื่อความปลอดภัย
  - การสำรอง (Backup) และกู้คืนข้อมูล (Restore)
- **workshop 7:** การใช้งานโปรแกรมสำรองข้อมูล NDB Backup
- การปรับแต่งประสิทธิภาพของ MySQL Cluster
  - ทฤษฎีในการกระจายภาระงาน (Load Balancing) เบื้องต้น
  - การทำงานแบบ Multi-threading ในระบบ MySQL Cluster
  - เข้าใจการทำงานภายในระบบ MySQL Cluster
  - เทคนิคที่สำคัญในการปรับแต่งประสิทธิภาพของ MySQL Cluster
  - การจัดการกับระบบเครือข่าย
  - พารามิเตอร์และตัวแปรที่สำคัญของระบบ
- **workshop 8:** Direct tcp crossover between data nodes

#### บ่าย

- การติดตั้งและใช้งานระบบ CMON web monitor สำหรับ MySQL Cluster
- หลักการปฏิบัติที่ดีในการสร้างระบบจริง
  - การประเมินความเหมาะสม
  - การออกแบบ
  - การคำนวณพื้นที่ที่ต้องการ
  - การเลือกใช้ฮาร์ดแวร์ที่เหมาะสม
  - การวางแผนขั้นตอนการติดตั้ง
  - ระยะเวลาในการติดตั้งระบบ
  - แนะนำระบบ Web Cluster
