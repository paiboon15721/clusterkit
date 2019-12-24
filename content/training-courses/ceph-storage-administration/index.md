---
title: 'Ceph Storage Administration'
subID: '22'
date: 2019-06-23T10:52:33+07:00
draft: false
weight: 20
totalHours: 12
totalDays: 2
price: 7490
pdfURL: 'http://www.clusterkit.co.th/training/pdf/Ceph%20Storage%20Administration.pdf'
---

## รายละเอียดหลักสูตร

หลักสูตรนี้กล่าวถึงการติดตั้ง, การบริหารจัดการและใช้งานระบบ Ceph Storage โดยการลงมือปฏิบัติการคอนฟิกระบบบนเครื่อง Virtual Machine จำลองให้เป็นระบบ Cluster Storage ขึ้นมา โดยจะศึกษาในส่วนของ Storage รูปแบบต่าง ๆ ในปัจจุบัน Traditional Storage และ Software-Defined Storage ความสามารถของ Ceph Storage การติดตั้งระบบและการขยายระบบ การบริหารจัดการการให้บริการของ Ceph Storage การทำ High Availability สำหรับ Ceph Storage และการนำ Ceph Storage ไปใช้งานในรูปแบบต่าง ๆ เช่น Block Storage / Object Storage / File System การติดตั้ง Web Monitoriing Tool เพื่อตรวจสอบสถานะของเครื่อง

## หลักสูตรนี้เหมาะสำหรับ

ผู้ที่สนใจเรื่อง Storage วิศวกรคอมพิวเตอร์ นักเทคโนโลยีสารสนเทศ อาจารย์และบุคลากรทางการศึกษาในสาขาที่เกี่ยวข้อง

## วัตถุประสงค์

1. เพื่อให้มีความรู้ความเข้าใจในระบบ Ceph Storage

## ความรู้พื้นฐาน

ผู้เข้าอบรมต้องมีความรู้ความสามารถในการติดตั้งใช้งาน Linux Server ระดับผู้ดูแลระบบหรือผ่านหลักสูตร Linux Administration มาก่อน ควรมีความเข้าใจเรื่องระบบเครือข่ายและไฟร์วอลล์

## รูปแบบการสอน

บรรยายและปฏิบัติการจริง (Workshop) โดยใช้ Virtual Machine 6 เครื่อง เพื่อจำลองสภาพแวดล้อมการติดตั้งระบบ Ceph Storage ให้เสมือนจริง

## ซอฟต์แวร์ที่ใช้

1. Ceph
2. CentOS 7.1

## สิ่งที่ผู้เข้าอบรมต้องเตรียม

ผู้เข้าอบรมต้องเตรียมเครื่องคอมพิวเตอร์ที่มีหน่วยความจำไม่น้อยกว่า 8 GB และมีพื้นที่ว่าง (Disk space) ไม่น้อยกว่า 50GB มาในการอบรม พร้อมติดตั้ง VirtualBox และ VirtualBox Extension Pack และเปิดฟังก์ชั่น Virtualization ใน BIOS มาให้เรียบร้อยตาม{{< link url="http://www.clusterkit.co.th/training/pdf/VirtualBox_64bit_Problem.pdf" text="คู่มือ" >}}

## เนื้อหาหลักสูตร

### วันที่ 1

- Storage Introduction
  - Traditional Storage
  - Int /Ext /Network Storage
  - Software-Defined Storage
  - Object Storage
  - Ceph Storage
- Ceph Introduction
  - Ceph Architecture
  - Ceph component
  - CRUSH Algorithm
  - Placement Group(PGs)
  - Pools
- Communicate Ceph
  - Block Storage (SAN)
  - File System (NAS)
  - Object Storage (API)
- Ceph Storage : Installation
  - Hardware Requirement
  - Production Implement requirement
  - Workshop : Install Ceph Storage for Object Storage and Block Storage
- Ceph Block Storage
  - Rados Block Device (RBD)
  - QEMU/KVM virtual block devices
  - **Workshop:** Using RBD

### วันที่ 2

- Ceph Object Storage
- librados – library direct access to ceph for apps
- Rados Gateway – REST based interface to Ceph storage
- Ceph File System
- MDS Server
  - CephFS client (in kernel/ FUSE)
  - MDS install and using
  - Workshop : MDS install and Mount Ceph File system
- High Availability
  - Multi mon service
  - MDS Active / Standby
  - Workshop : Full High Availability Configuration Ceph Storage 3 mon, 2 mds, 3osd
- Install Web Mornitoring : Ganglia
- Real Implement Case sharing
  - Sharing Ceph FS via SAMBA for Windows Clients access with Active Directory Authentication
  - **Workshop:** Simple Ceph FS sharing to Windows Clients via SAMBA
