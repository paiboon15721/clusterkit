---
title: 'Openstack Administration'
date: 2019-06-23T10:52:42+07:00
draft: false
totalHours: 18
totalDays: 3
price: 10700
pdfURL: 'http://www.clusterkit.co.th/training/pdf/OpenStack%20Administration.pdf'
---

## รายละเอียดหลักสูตร

หลักสูตรนี้กล่าวถึง หลักการทำงานของ OpenStack เพื่อสำหรับการใช้ติดตั้งและตั้งค่าเพื่อให้สามารถสร้างระบบ Cloud Computing โดยใช้ OpenSource เป็นแกนหลัก โดยจะเน้นให้ผู้เรียนเข้าใจถึงสถาปัตยกรรมและโครงสร้างของ OpenStack เทคนิคการติดตั้ง การตั้งค่า และแก้ปัญหาที่เกิดขึ้นกับการใช้งาน OpenStack

## วัตถุประสงค์

1. รู้และเข้าใจแนวคิดของ Cloud Computing เพื่อนำไปสู่การเข้าใจ OpenStack
2. รู้จักภาพรวมของ OpenStack รวมไปถึงสถาปัตยกรรมบน OpenStack
3. สามารถติดตั้ง OpenStack บน server หลายตัวได้
4. สามารถจัดการกับระบบ OpenStack ทั้งในมุมมองของผู้ดูแลระบบและผู้ใช้งานได้

## ความรู้พื้นฐาน

มีความรู้พื้นฐาน Linux Administrator

## สิ่งที่ผู้เข้าอบรมต้องเตรียม

ผู้เข้าอบรมต้องเตรียมเครื่องคอมพิวเตอร์ที่มีหน่วยความจำไม่น้อยกว่า 8 GB และมีพื้นที่ว่าง (Disk space) ไม่น้อยกว่า 50GB มาในการอบรม พร้อมติดตั้ง VirtualBox และ VirtualBox Extension Pack และเปิดฟังก์ชั่น Virtualization ใน BIOS มาให้เรียบร้อยตาม{{< link url="http://www.clusterkit.co.th/training/pdf/VirtualBox_64bit_Problem.pdf" text="คู่มือ" >}}

## เนื้อหาหลักสูตร

### วันที่ 1

- Basic Knowledge
  - ความหมายของ cloud computing
  - เทคโนโลยี virtualization
  - แนวคิดของ OpenAPI
  - RESTful
- OpenStack Overview
  - ประวัติความเป็นมาของ OpenStack
  - ภาพรวมของ project (nova , glance , swift , neutron , keystone ,horizon , cinder)
  - pre-workshop : เตรียมความพร้อมสร้างระบบ Cloud Service
- ตั้งค่า Operating System ตาม Reference Architecture
  - ปรับแต่ง Software Repository
  - Deploying OpenStack with RDO
- **workshop 1:** Deploying OpenStack with RDO
- การเตรียมสภาพแวดล้อมของระบบ
  - การ custom configuration file ก่อนการติดตั้งตาม Reference Architecture
  - ทดสอบการติดตั้งโดยการเข้าใช้งานผ่าน dashboard

### วันที่ 2

- OpenStack Identity Service (Keystone)
  - แนวคิดและหลักปรัชญา
  - สถาปัตยกรรม
  - การติดต่อสื่อสารกับ Component อื่น (keystone API)
  - หน้าที่หลักของ Keystone
- OpenStack Compute Service (Nova)
  - การติดต่อสื่อสารกับ Component อื่น (Nova API)
  - การสื่อสารกันภายใน Nova ด้วย Massage Queue
  - การจัดสรรงานบน Cloud Service (Nova Scheduler)
  - หัวใจแห่งการประมวลผลบน Cloud (Nova-Compute)
  - Nova Conductor
- OpenStack Network Service (Neutron)
  - แนวคิดและหลักปรัชญา
  - สถาปัตยกรรม
  - Network Configuration Flow
  - Plug-in ที่รองรับการทำงาน
- OpenStack Block-Storage Service (Cinder)
  - แนวคิดและหลักปรัชญา
  - สถาปัตยกรรม
  - Cinder Driver
- OpenStack Image Service (Glance)
  - แนวคิดและหลักปรัชญา
  - สถาปัตยกรรม
  - ความสามารถของ Glance
  - Image Format
- **workshop 2:** Create Custom Image
  - การสร้าง centOS 6.4 virtual machine image โดยใช้ apache web server เป็นตัวอย่าง application ที่รันบน

### วันที่ 3

- **workshop 3:** พื้นฐานการใช้งาน OpenStack ทั้งในมุมมองของผู้ใช้และผู้ดูแลระบบ
  - Authentication เพื่อเข้าสู่ OpenStack
  - การสร้างผู้ใช้งาน และ การกำหนดสิทธิ์ต่างในระบบ
  - การจัดการด้วยสิทธื์ผู้ดูแลระบบ
  - เข้าใช้งานด้วยผู้ใช้ที่ถูกสร้างจากผู้ดูแลระบบ
  - การจัดการกับ security ต่าง ๆ ด้วยผู้ใช้
  - การสร้าง VM จาก Image file
  - การจัดการกับ VM ที่ถูกสร้าง
- OpenStack storage service (Swift)
  - สถาปัตยกรรมของ Swift
  - The Ring , Ring Builder , partitioning
  - account, container และ object server
  - Replication
  - Security และ ACL
- **workshop 4:** การติดตั้งและใช้งาน Swift
  - CRUD (Create, Read, Update, Delete) บน container และ object
  - การใช้งาน Swift API
- **workshop 5:** การเคลื่อนย้าย VM ระหว่าง Host (Live Migration)
  - การตั้งค่า file configuration ที่เกี่ยวข้องกับการทำ Live Migration
