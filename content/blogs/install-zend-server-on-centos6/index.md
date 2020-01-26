---
title: 'Install Zend Server on CentOS6'
date: 2012-11-07T14:13:44+07:00
draft: false
---
Zend Server  นั้นเป็น PHP Server ที่ไว้แปลภาษา php ซึ่งพัฒนามาจากบริษัท zend ซึ่งเป็นผู้พัฒนาภาษา php 
สิ่งที่ Zend Server ต่างกับ PHP Interpreter Server ทั่วไปก็คือ ตัว Zend Server จะได้รับการพัฒนาให้ทำงานได้มีประสิทธิภาพที่ดีกว่า
ซึ่งเราสามารถติดตั้งใช้งาน Zend Server ได้บนระบบ CenOS6 ดังนี้

#### ขั้นตอนการติดตั้ง

1. Download Zend Server community version จาก
http://www.zend.com/en/products/server-ce/downloads

2. แตกไฟล์ที่ download ออกมา
<table class="table table-bordered">
      <td>
       # tar zxvf http://www.zend.com/en/products/server-ce/downloads
      </td>
</table>

3. เข้าไปยังไดเรกทอรี่ที่แตกออกมา และรันสคริปต์ install_zs.sh
<table class="table table-bordered">
      <td>
       # cd ZendServer-RepositoryInstaller-linux  
       # ./install_zs.sh       
      </td>
</table>
ซึ่งจะทำการเพิ่ม repository ของ zend server เข้าไป เพื่อให้ติดตั้งจาก repository ของ zend ได้

4. ติดตั้ง Zend Server โดยผ่าน คำสั่ง yum ระบบจะทำการติดตั้ง zend server ผ่านอินเทอร์เน็ต โดยดึงไฟล์ติดตั้งจาก repository ของ zend
<table class="table table-bordered">
      <td>
       # yum install php-5.3 httpd php-cli
      </td>
</table>
   

เมื่อติดตั้งเสร็จก็จะจบขั้นตอนการติดตั้ง

