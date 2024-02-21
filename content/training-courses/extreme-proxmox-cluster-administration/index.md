---
title: 'Extreme Proxmox Cluster Administration'
subID: '658a9f63b765b32335c8bbaa' 
date: 2024-02-21T15:48:47+07:00
draft: false
totalHours: 18
totalDays: 3
price: 17655
pdfURL: 'http://clusterkit.co.th/training/pdf/Extreme-Proxmox-Cluster-Administration-3Days.pdf'
---

## รายละเอียดหลักสูตร

หลักสูตรนี้เป็นการเรียนรู้การติดตั้งและใช้งาน Open Source Software ระบบ Virtualization ที่ชื่อ Proxmox Virtual Environment (Proxmox VE หรือ PVE) โดยเป็นซอฟต์แวร์บริหารจัดการทรัพยากร คอมพิวเตอร์สำหรับองค์กร เนื้อหาในหลักสูตรครอบคลุมตั้งแต่ การติดตั้งระบบ การจัดการบัญชีผู้ใช้ การสร้างและรัน VM บน ระบบ การจัดการ Storage ทั้งแบบ Local และ Network จากระบบ Virtualization  การ convert VM อื่นมาทำงานบน Proxmox การปรับแต่งการใช้งานในรูปแบบคลัสเตอร์ การทำ Live Migration การขยายระบบในแบบ Hyper Converged Infrastructure การทำ High-Availability รวมถึงการ Upgrade version และการจัดการเครื่องในระบบกรณีฮาร์ดแวร์เสียหาย

## หลักสูตรนี้เหมาะสำหรับ

ผู้ดูแลระบบคอมพิวเตอร์ ผู้ที่สนใจ ผู้ที่ต้องการย้ายระบบ Virtualization อื่น ๆ มายัง Proxmox

## วัตถุประสงค์

1. เพื่อให้ผู้เข้าอบรมใจในหลักการทำงานและองค์ประกอบของ Proxmox VE
2. เพื่อให้ผู้เข้าอบรมสามารถติดตั้ง และใช้งาน Proxmox ได้ทั้งแบบ Single Node และ คลัสเตอร์
3. เพื่อให้ผู้เข้าอบรมเข้าใจหลักการทำงานร่วมกันระหว่าง Proxmox และ Ceph
4. เพื่อให้ผู้เข้าอบรมสามารถแก้ไขปัญหาเบื้องต้น ทราบถึงปัญหาที่พบบ่อย ๆ

## ความรู้พื้นฐาน

ผู้เข้าอบรมควรมีความรู้หรือใช้งาน Linux มาก่อนบ้าง และมีความเข้าใจเรื่องระบบเครือข่ายพื้นฐาน

## ซอฟต์แวร์ที่ใช้

ซอฟต์แวร์ Proxmox VE 8

## สิ่งที่ผู้เข้าอบรมต้องเตรียม

ผู้เข้าอบรมเตรียมโน้ตบุ๊คมาในวันอบรม

## เนื้อหาหลักสูตร

### วันที่ 1
- Virtualization/Containerization Concept
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
- VM Configuration file and Manage VM/Container 
  - Add Device (disk, network) to VM/Container
  - Import Disk จากระบบอื่นเข้ามาบนระบบ Proxmox
    - Import qcow2/vmdk/vhd,vhdx เข้ามายัง Proxmox 
    - Import ไฟล์ VM ที่ Export มาจากระบบ VMWare (ova/ovf) เข้าระบบ Proxmox
- การย้ายเครื่อง Proxmox เมื่อ HW เสียหาย
### วันที่ 2
- Add Network Shared Storage SMB/NFS/iSCSI
- หลักการทำ Passthrough  PCIe/GPU/USB
- Snapshot and Backup 
  - Snapshot and Rollback VM/Container
  - Backup and Restore VM/Container
- Volume Management
  - LVM – Logical Volume Management
  - OpenZFS
- Network Management
  - OVS
  - Bonding
  - VLAN
- Authentication and User management
  - Authentication
    - Linux PAM Standard authentication/Proxmox VE authentication
    - Roles
  - Add User/group 
  - Sync User from Active Directory/LDAP Server
  - Two Factor Authentication
### วันที่ 3
- Proxmox Cluster
  - Proxmox Cluster File System (pmxcfs)
- Create Proxmox Cluster ปรับแต่งให้ Proxmox ทำงานเป็นคลัสเตอร์ (3 Nodes)
- Hyper Converged Infrastructure (HCI) with Ceph
  - RBD – Block Storage
  - CephFS – File System
- การติดตั้ง Ceph บน Proxmox เพื่อทำ HCI
- Storage Replication : ZFS Replication
- Migration VM ระหว่างเครื่อง
  - Offline Migration VM/Container
  - Live Migration สำหรับ VM
- High Availability และสถาปัตยกรรมแบบคลัสเตอร์
- High-Availability Setting
  - HA on Shared Storage
  - HA with ZFS Replication (และจุดที่ต้องกังวล)
- การจัดการโหนดที่เสียหายและการเพิ่มโหนดกลับเข้าไปยังคลัสเตอร์
- Proxmox Firewall
- Upgrade Proxmox  7 to 8