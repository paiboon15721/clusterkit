---
title: 'Postgresql Administration'
subID: '67c686dcb765b32335c8bc1f' 
date: 2025-03-07T14:14:43+07:00
draft: false
totalHours: 18
totalDays: 3
price: 14980
pdfURL: 'http://www.clusterkit.co.th/training/pdf/PostgreSQL-Administration-rev.3.pdf'
---

## รายละเอียดหลักสูตร
หลักสูตรนี้กล่าวถึงวิธีการติดตั้งซอฟต์แวร์จัดการฐานข้อมูล PostgreSQL หลักการจัดการกับฐานข้อมูลของ
PostgreSQL การเริ่มและการหยุดการทำงานของเซิร์ฟเวอร์ การเพิ่มลบบัญชีผู้ใช้ การกำหนดสิทธิต่าง ๆ การกำหนดค่าเพื่อความปลอดภัยของระบบ การจัดการกับพื้นที่ในการจัดเก็บข้อมูล การสำรองและกู้คืนข้อมูล การปรับแต่งประสิทธิภาพ การอัพเกรดเมเจอร์เวอร์ชัน การทำสำเนาข้อมูลด้วย replication และการคอนฟิก PostgreSQL Active/Standby พร้อม Automatic Fail over ด้วย Patroni การใช้เครื่องมือต่าง ๆ ที่เกี่ยวข้อง รวมถึงบทบาทและหน้าที่ของผู้ดูแลระบบที่ดี

## วัตถุประสงค์
1. เพื่อให้ผู้รับการอบรมสามารถติดตั้งและบริหารจัดการ PostgreSQL Server ได้
2. เพื่อให้ผู้รับการอบรมสามารถดูแลระบบและแนะนำผู้ใช้งานระบบได้ 
3. เพื่อให้ผู้รับการอบรมสามารถทำการสำรองและกู้คืนข้อมูลในระบบได้
4. เพื่อให้ผู้รับการอบรมสามารถปรับแต่งประสิทธิภาพของ PostgreSQL ได้
5. เพื่อให้ผู้รับการอบรมสามารถติดตั้ง PostgreSQL แบบ Active/standby ผ่าน patroni ได้

## ความรู้พื้นฐาน
ผู้เข้าอบรมควรมีทักษะการใช้งานคำสั่งลีนุกซ์ (Linux) พื้นฐาน และเคยใช้งานซอฟต์แวร์ระบบจัดการฐานข้อมูลมาก่อน

## สภาพแวดล้อมและเครื่องมือในการพัฒนาที่ใช้ในการอบรม :
* CentOS/Ubuntu Linux 
* PostgreSQL, PgAdmin
* Prometheus & Grafana
* Patroni, etcd, keepalived

## สิ่งที่ผู้เข้าอบรมต้องเตรียม
ผู้เข้าอบรมต้องเตรียมเครื่องคอมพิวเตอร์ที่มีหน่วยความจำไม่น้อยกว่า 8 GB มาในการอบรม พร้อมติดตั้ง VirtualBox และ VirtualBox Extension Pack 

## เนื้อหาหลักสูตร
### วันที่ 1

* แนะนําให้รู้จักกับระบบจัดการฐานข้อมูล PostgreSQL 
* การติดตั้ง 
    * PostgreSQL
    * File system layouts
    * Install & Post-Installation setup
    * การเปิดปิดบริการของ PostgreSQL 
* การปรับค่าคอนฟิกกูเรชันที่สําคัญของ PostgreSQL
* การจัดการบัญชีผู้ใช้
    * Role & Privileged Management
* PostgreSQL client application
    * การใช้งาน PostgreSQL ในรูปแบบ command-line (psql) 
    * pgAdmin toots
    * Clients and host base access control
    * การปรับแต่งไฟร์วอลล์ (Firewall) สำหรับ PostgreSQL 
* Create and configure a database
* สกีมา Schemas
* การใช้งานทรานแซคชัน (Transaction)
* สร้างและใช้งาน Tablespace 

### วันที่ 2

* PostgreSQL Architecture
* Index
  * รู้จักกับ Index ประเภทต่าง ๆ การสร้าง การใช้งาน
  * การจัดการและการบำรุงรักษา index
* Backup & Restore 
  * การเขียนสคริปต์เพื่อตั้งเวลาสำรองข้อมูล
  * การบริการตรวจตราระบบด้วย Prometheus & Grafana เพื่อตรวจตรา PostgreSQL และแจ้งเตือน
  * การปรับแต่งประสิทธิภาพ (Performance Tuning) 
  * การใช้งาน pgbench เพื่อวัดประเมินประสิทธิภาพของ PostgreSQL เบื้องต้น
  * PostgreSQL Major version upgrade 

### วันที่ 3

* การทำ replication แบบ Master-Slave
* การทำระบบ PostgreSQL High Availability (Active/Standby) ด้วย Patroni 
  * ติดตั้งและคอนฟิก etcd แบบ 3 โหนด 
  * ติดตั้งและคอนฟิก Patroni เพื่อทำ High Availability
  * ติดตั้ง Keepalived เพื่อจัดการ Virtual IP และการเขียนสคริปต์เพื่อให้งาน failover สมบูรณ์
  * เข้าใจการทำงานของ watchdog และการเปิดใช้งาน
  * ปัญหาการ sequence และการเขียนสคริปต์เพื่อ resync sequence 