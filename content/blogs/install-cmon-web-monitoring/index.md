---
title: 'การติดตั้ง CMON Web Monitoring'
date: 2010-01-17T15:06:26+07:00
draft: false
---

CMON เป็นเว็บแอพพลิเคชั่น ซึ่งเป็นซอฟต์แวร์ open source ใช้สำหรับตรวจดูสถานะการทำงานของระบบ MySQL Cluster โดยการติดตั้งแนะนำให้ติดตั้งที่เครื่อง management โดยให้เพิ่ม slot ของ sql node ให้กับเครื่อง management ด้วย อ้างอิงจาก http://johanandersson.blogspot.com/2008/08/cluster-monitoring-cmon.html



## 1. ขั้นตอนการติดตั้งซอฟต์แวร์

1.1 ดาวน์โหลด cmon ที่ http://www.severalnines.com/downloads/cmon/cmon.tgz

1.2 แตกไฟล์ cmon.tgz

<table class="table table-bordered">
      <td>
        shell> tar xvfz cmon.tgz 
      </td>
</table>
             
1.3 ก่อนติดตั้งต้องแน่ใจก่อนได้กำหนด mysql_config บน path 
<table class="table table-bordered">
      <td>
        shell> export PATH=/usr/local/mysql/mysql/bin:$PATH
      </td>
</table>
            
1.4 เริ่มการติดตั้ง
<table class="table table-bordered">
      <td>
        shell> cd cmon  
        shell> sh autogen.sh   
        shell> ./configure --with-www=/var/www/html/   
        shell> make   
        shell> make install   
        shell> export LD_LIBRARY_PATH=/usr/local/lib/mysql:/usr/local/lib64/mysql
      </td>
</table>
            
1.5 สร้างฐานข้อมูลของ CMON โดยใช้สคริปต์ cmon.sql 
<table class="table table-bordered">
      <td>
        shell> mysql -u root -p  
        mysql> source sql/cmon.sql
      </td>
</table>


## 2. ลำดับการคอนฟิก

2.1 แก้ไขไฟล์ cmon_db_conf.inc.php ใน /var/www/html/cmon/config/

<table class="table table-bordered">
      <td>
        shell> vi /var/www/html/cmon/config/cmon_db_conf.inc.php
      </td>
</table>


2.2 แก้ไขค่าตัวแปรต่าง ๆ สำหร้บเชื่อมต่อกับ MySQL Server

<table class="table table-bordered">
      <td>
        $mysql_username = "root";  
        $mysql_password = "";   
        $mysql_hostname = "localhost";
      </td>
</table>


2.3 แตกไฟล์ jpgraph-1.26.tar.gz ใน /var/www/html/cmon/

<table class="table table-bordered">
      <td>
        shell> tar -xvf jpgraph-1.26.tar.gz
      </td>
</table>


## 3. ทำการสร้างกราฟสำหรับ Data Memory,Index Memory

3.1 เข้าไปที่ /path/cmon-0.14/scripts/rrd/

<table class="table table-bordered">
      <td>
        shell> cd /root/cmon-0.14/scripts/rrd/
      </td>
</table>
                  
3.2 แก้ไขไฟล์ rrd.conf
<table class="table table-bordered">
      <td>
        shell> vi rrd.conf
      </td>
</table>
                  
3.3 สร้าง rrd 
<table class="table table-bordered">
      <td>
        shell> ./create_rrd_cmon.sh rrd.conf
      </td>
</table>
                   
3.4 สร้างกราฟ
<table class="table table-bordered">
      <td>
        shell> create_graphs_cmon.sh rrd.conf
      </td>
</table>
                   
3.5 อัพเดทข้อมูล
<table class="table table-bordered">
      <td>
        shell> update_graphs_cmon.sh rrd.conf
      </td>
</table>


## 4. การรันโปรแกรมเพื่อเริ่มต้นทำงาน

4.1 สั่งรันคำสั่ง cmon ใน /cmon-0.14/bin/

 <table class="table table-bordered">
      <td>
        shell> cmon –ndb-connectstring=mgm1.local   
        --mysqlhost=localhost   
        --mysqlport=3306  
        --mysqluser=root  
        --mysqlpasswd=< passwd >  
        --mysqlsocket=/var/lib/mysql/mysql.sockcmon
      </td>
</table>
                   
4.2 เปิดบริการเว็บเซิร์ฟเวอร์
<table class="table table-bordered">
      <td>
        shell> service httpd start  
      </td>
</table>
                   
4.3 เปิดใช้งาน CMON ผ่านทางเว็บบราวเซอร์ http://localhost/cmon/

## 5. ปัญหาที่อาจจะพบ

5.1 กรณีในส่วนของ statisties ไม่แสดงกราฟเหมือนดังภาพด้านล่าง เนื่องจากในเครื่องไม่ได้ติดตั้ง GD library สำหรับ PHP ไว้ ให้ทำการติดตั้งเพ็คเกจ php-gd-5.1.6-23.el5.x86_64

 <table class="table table-bordered">
      <td>
        shell> rpm -ivh php-gd-5.1.6-23.el5.x86_64.rpm 
      </td>
</table>
