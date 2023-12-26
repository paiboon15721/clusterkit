---
title: 'Extreme Proxmox Cluster Administration'
subID: '658a9f63b765b32335c8bbaa' 
date: 2023-12-26T16:52:47+07:00
draft: false
totalHours: 12
totalDays: 2
price: 14980
pdfURL: 'http://clusterkit.co.th/training/pdf/Extreme-Proxmox-Cluster-Administration.pdf'
---

## รายละเอียดหลักสูตร

หลักสูตรนี้เป็นการเรียนรู้การติดตั้งและใช้งาน Open Source Software ระบบ Virtualization ที่ชื่อ Proxmox Virtual Environment (Proxmox VE หรือ PVE) โดยเป็นซอฟต์แวร์บริหารจัดการทรัพยากร คอมพิวเตอร์สำหรับองค์กร เนื้อหาในหลักสูตรครอบคลุมตั้งแต่ การติดตั้งระบบ การจัดการบัญชีผู้ใช้ การสร้างและรัน VM บนระบบ การ convert VM จากระบบอื่นมาทำงานบน Proxmox การปรับแต่งการใช้งานในรูปแบบคลัสเตอร์ การทำ Live Migration และการขยายระบบในแบบ Hyper Converged Infrastructure

## หลักสูตรนี้เหมาะสำหรับ

ผู้ดูแลระบบคอมพิวเตอร์ และผู้ที่สนใจ

## วัตถุประสงค์

1. เพื่อให้ผู้เข้าอบรมใจในหลักการทำงานและองค์ประกอบของ Proxmox VE
2. เพื่อให้ผู้เข้าอบรมสามารถติดตั้ง และใช้งาน Proxmox ได้ทั้งแบบ Single Node และ คลัสเตอร์
3. เพื่อให้ผู้เข้าอบรมเข้าใจหลักการทำงานร่วมกันระหว่าง Proxmox และ Ceph
4. เพื่อให้ผู้เข้าอบรมสามารถแก้ไขปัญหาเบื้องต้น ทราบถึงปัญหาที่พบบ่อย ๆ

## ความรู้พื้นฐาน

ผู้เข้าอบรมควรมีความรู้ Linux Command หรือใช้งาน Linux มาก่อนบ้าง และควรมีความเข้าใจเรื่องระบบเครือข่ายพื้นฐาน

## ซอฟต์แวร์ที่ใช้

ซอฟต์แวร์ Proxmox VE

## สิ่งที่ผู้เข้าอบรมต้องเตรียม

ผู้เข้าอบรมเตรียมโน้ตบุ๊คมาในวันอบรม

## เนื้อหาหลักสูตร

### วันที่ 1
- Virtualization/Containerization
- Proxmox VE introduction
  - Virtualization Engine : KVM and LXC
  - Nested Virtualization
  - Hardware Recommend
- Proxmox GUI
  - Introduction to web-based management (GUI)
  - จัดการ repository บน Proxmox
  - Proxmox Workstation
  - การเปลี่ยนชื่อ Hostname/ IP Address 
- Default Local Storage 
- Create VM/Container
- Workshop : ติดตั้งซอฟต์แวร์ Proxmox บนระบบ Proxmox ที่เตรียมไว้และทดลองใช้งาน VM/Container
  - KVM: create and manage virtual machines (Windows & Linux)
  - LXC: create and manage containers (Linux only)
- VM Configuration file and Manage VM/Container 
  - Add Device (disk, network) to VM/Container
  - Move Disk ระหว่าง VM
  - Import Disk จากระบบอื่นเข้ามาบนระบบ Proxmox
    - Import qcow2/vmdk disk เข้ามายัง Proxmox 
    - Convert Disk จาก HyperV (vhd,vhdx) เป็น qcow2 
    - Import ไฟล์ VM ที่ Export มาจากระบบ VMWare (ova/ovf) เข้าระบบ Proxmox
- Add Shared Storage
- GPU/USB Passthrough
- Snapshot and Backup 
  - Snapshot and Rollback VM/Container
  - Backup and Restore VM/Container
- Volume Management
  - LVM – Logical Volume Management
  - OpenZFS
- Network Management
  - Bonding
- Authentication and User management
  - Authentication
    - Linux PAM Standard authentication
    - Proxmox VE authentication
    - Roles
  - Add User/group 
  - Sync User from Active Directory/LDAP Server
  - Two Factor Authentication
### วันที่ 2
- Proxmox Cluster
  - Proxmox Cluster File System (pmxcfs)
- Create Proxmox Cluster ปรับแต่งให้ Proxmox ทำงานเป็นคลัสเตอร์ (3 Nodes)
- Hyper Converged Infrastructure (HCI) with Ceph
  - RBD – Block Storage
  - CephFS – File System
- การติดตั้ง Ceph บน Proxmox เพื่อทำ HCI
- Storage Replication : ZFS Replication
- การทำ Offline Migration VM/Container
- การทำ Live Migration สำหรับ VM
- High Availability และสถาปัตยกรรมแบบคลัสเตอร์
- High-Availability Setting
  - HA on Shared Storage
  - HA with ZFS Replication (และจุดที่ต้องกังวล)
- การจัดการโหนดที่ Fail และการเพิ่มโหนดกลับเข้าไปยังคลัสเตอร์
- Proxmox Firewall
- Upgrade Proxmox  7 to 8