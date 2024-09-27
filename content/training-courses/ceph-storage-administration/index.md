---
title: 'Ceph Storage Administration'
subID: '5e32c6df369cdf2fdc2896f3'
date: 2024-09-27T10:52:33+07:00
draft: false
weight: 20
totalHours: 12
totalDays: 2
price: 10700
pdfURL: 'http://www.clusterkit.co.th/training/pdf/Ceph%20Storage%20Administration.pdf'
---

## รายละเอียดหลักสูตร

หลักสูตรนี้ผู้อบรมจะได้เรียนรู้เรื่อง ระบบ Ceph Storage ทั้งการติดตั้ง การบริหารจัดการและใช้งานระบบ Ceph Storage โดยการลงมือปฏิบัติการคอนฟิกระบบบนเครื่อง Virtual Machine จำลองให้เป็นระบบ Cluster Storage ขึ้นมา โดยจะศึกษาในส่วนของ Storage รูปแบบต่าง ๆ ทั้ง Traditional Storage และ Software-Defined Storage, ความสามารถของ Ceph Storage, การติดตั้งระบบและการขยายระบบ, การบริหารจัดการการให้บริการของ Ceph Storage, การทำ High Availability สำหรับ Ceph Storage และการนำ Ceph Storage ไปใช้งานในรูปแบบต่าง ๆ ได้แก่ Block Storage / Object Storage / File System รวมทั้งการติดตั้ง Monitoring Tool สำหรับระบบ Ceph

## หลักสูตรนี้เหมาะสำหรับ

ผู้ที่สนใจเรื่อง Storage วิศวกรคอมพิวเตอร์ นักเทคโนโลยีสารสนเทศ อาจารย์และบุคลากรทางการศึกษาในสาขาที่เกี่ยวข้อง

## วัตถุประสงค์

1. เพื่อให้มีความรู้ความเข้าใจในระบบ Ceph Storage
2. เพื่อให้ผู้เข้าอบรมสามารถติดตั้ง ใช้งาน และบริหารจัดการ Ceph Storageได้

## ความรู้พื้นฐาน

ผู้เข้าอบรมต้องมีความรู้ความสามารถในการติดตั้งใช้งาน Linux Server ระดับผู้ดูแลระบบหรือผ่านหลักสูตร Linux Administration มาก่อน ควรมีความเข้าใจเรื่องระบบเครือข่ายและไฟร์วอลล์

## รูปแบบการสอน

บรรยายและปฏิบัติการจริง (Workshop) โดยใช้ Virtual Machine 3 เครื่อง เพื่อจำลองสภาพแวดล้อมการติดตั้งระบบ Ceph Storage ให้เสมือนจริง

## ซอฟต์แวร์ที่ใช้

1. Ceph
2. Rocky Linux

## สิ่งที่ผู้เข้าอบรมต้องเตรียม

ผู้เข้าอบรมต้องเตรียมเครื่องโน้ตบุ๊ค โดยมีหน่วยความจำไม่น้อยกว่า 16GB  และมีพื้นที่ว่าง (Disk space) ไม่น้อยกว่า 100GB สำหรับ VMs และติดตั้งซอฟต์แวร์ Oracle VirtualBox โดยในการอบรมจะใช้ซอฟต์แวร์ VirtualBox จำลองเครื่อง โดยจะใช้ทั้งหมด 3 VMs และเปิดฟังก์ชัน Virtualization ใน BIOS ไว้เรียบร้อยแล้วตาม{{< link url="http://www.clusterkit.co.th/training/pdf/VirtualBox_64bit_Problem.pdf" text="คู่มือ" >}} 


## เนื้อหาหลักสูตร

### วันที่ 1

- พื้นฐาน Storage
  - Storage ทั่วไป
    - Internal/External/Network Storage
  - Software-Defined Storage
    - Object Storage
- แนะนำ Ceph Storage
  - สถาปัตยกรรม
  - ส่วนประกอบต่าง ๆ ของซอฟต์แวร์ Ceph
- การทำงานของ Ceph
  - CRUSH Algorithm
  - Placement Group(PGs)
  - Pools
- รูปแบบ Storage ของ Ceph  
  - Block Storage (SAN)
  - File System (NAS)
  - Object Storage (API)
- การติดตั้งซอฟต์แวร์ Ceph
  - ความต้องการของฮาร์ดแวร์
  - Workshop : ติดตั้งซอฟต์แวร์ Ceph
- Ceph Block Storage
  - Rados Block Device (RBD)
  - QEMU/KVM virtual block devices
  - Workshop : ใช้งาน Ceph ในรูปแบบ RBD

### วันที่ 2

- การใช้งานCeph แบบObject Storage
  - librados – library สำหรับใช้งาน Ceph แบบdirect access สำหรับ Application
  - Rados Gateway – สร้าง S3 API Gateway เพื่อเก็บข้อมูลบน Ceph storage 
- การใช้งาน Ceph ในรูปแบบ File System
  - MDS Server - ส่วนประกอบเพิ่มเติมที่ใช้สำหรับ File System 
  - การ ใช้งานCephFS client ( mount in kernel/ FUSE)  
  - การติดตั้ง MDS Server และปรับแต่งใช้งาน File System
  - Workshop : MDS install and Mount Ceph File system 
- Erasure Coding
- Tuning CRUSH Algorithm
- การทำงานแบบ High Availability 
  - ปรับแต่ง Multi monitor service ( 3 Node MON) 
  - ปรับแต่ง MDS ทำงาน แบบ Active / Standby 
  - Workshop : Full High Availability Configuration Ceph Storage 3 mon, 2 mds, 3osd 
- ติดตั้ง Monitoring : Prometheus และ grafana 
- Q&A and Discussion
