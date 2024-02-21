---
title: "Advanced Proxmox Cluster Management"
subID: "5e32c6df369cdf2fdc2896f7"
date: 2019-06-23T10:51:48+07:00
draft: false
weight: 40
totalHours: 12
totalDays: 2
price: 10700
pdfURL: "http://www.clusterkit.co.th/training/pdf/Advanced%20Proxmox%20Cluster%20Management.pdf"
---

---
## ** เพิ่มเติมเนื้อหา เป็นหลักสูตรใหม่ 
## {{< link url="https://www.clusterkit.co.th/training-courses/extreme-proxmox-cluster-administration/" text="หลักสูตร Extreme Proxmox Cluster Administration" >}}
---
## รายละเอียดหลักสูตร

หลักสูตรนี้เป็นการเรียนรู้การติดตั้งและใช้งาน Open Source Software ระบบ Virtualization ที่ชื่อ Proxmox Virtual Environment (Proxmox VE หรือ PVE) โดยเป็นซอฟต์แวร์บริหารจัดการทรัพยากร คอมพิวเตอร์สำหรับองค์กร เนื้อหาในหลักสูตรครอบคลุมตั้งแต่ การติดตั้งระบบ การจัดการบัญชีผู้ใช้ การสร้างและรัน VM บนระบบ การปรับแต่งการใช้งานในรูปแบบคลัสเตอร์ การทำ Live Migration และการขยายระบบในแบบ Hyper Converged Infrastructure

## หลักสูตรนี้เหมาะสำหรับ

ผู้ดูแลระบบคอมพิวเตอร์ และผู้ที่สนใจ

## วัตถุประสงค์

1. เพื่อให้ผู้เข้าอบรมใจในหลักการทำงานและองค์ประกอบของ Proxmox VE
2. เพื่อให้ผู้เข้าอบรมสามารถติดตั้ง และใช้งาน Proxmox ได้ทั้งแบบ Single Node และ คลัสเตอร์
3. เพื่อให้ผู้เข้าอบรมเข้าใจหลักการทำงานร่วมกันระหว่าง Proxmox และ Ceph
4. เพื่อให้ผู้เข้าอบรมสามารถแก้ไขปัญหาเบื้องต้น ทราบถึงปัญหาที่พบบ่อย ๆ

## ความรู้พื้นฐาน

ผู้เข้าอบรมต้องมีความรู้ความสามารถในการติดตั้งและใช้งาน Linux Server หรือผ่านหลักสูตร Linux Administration มาก่อน และควรมีความเข้าใจเรื่องระบบเครือข่ายพื้นฐาน

## รูปแบบการสอน

บรรยายและปฏิบัติการ โดยทางบริษัทฯ เตรียมเครื่องคอมพิวเตอร์ 3 เครื่องต่อคน เพื่อสร้างระบบ Proxmox Cluster และทางผู้เข้าอบรมเตรียมเครื่อง Notebook พร้อม Browser Firefox หรือ Chrome เพื่อติดต่อเข้า Proxmox

## ซอฟต์แวร์ที่ใช้

1. ซอฟต์แวร์ Proxmox VE

## เนื้อหาหลักสูตร

### วันที่ 1

- Virtualization and Proxmox VE introduction
- Virtualize Engine : KVM and LXC
- Network Device
- Network model
  - Bridge (Default)
  - Routed
  - NAT
- Storage Model
  - Local
  - Share Storage
- **Workshop:** ติดตั้งซอฟต์แวร์ Proxmox แบบ Single Node
- Introduction to web-based management (GUI)
- Authentication and User management
- KVM: create and manage virtual machines (Windows & Linux)
- LXC: create and manage containers (Linux only)
- Manage VM/CT startup and shutdown behavior
- **Workshop:** ทดลองใช้งาน proxmox สร้าง VM
- จัดการ repository บน Proxmox
- Backup and Restore VM
- Firewall
- Ports used by Proxmox VE
- Concepts / architecture / technology of a cluster setupt

### วันที่ 2

- Hyper Converged Infrastructure (HCI)
- High Availability และสถาปัตยกรรมแบบคลัสเตอร์
- Hardware requirement for HA
- Proxmox Cluster File System (pmxcfs)
- การปรับแต่งให้ Proxmox ทำงานเป็นคลัสเตอร์ (3 Nodes)
- การติดตั้ง Ceph บน Proxmox เพื่อทำ HCI
- การทำ Live Migration สำหรับ VM
- Troubleshooting
