---
title: 'การใช้งาน ndb_size.pl บน CentOS5'
date: 2010-01-18T08:04:43+07:00
draft: false
---
ถ้ารันคำสั่ง ndb_size.pl แล้วเกิด error เกี่ยวกับ Class-MethodMaker ให้ติดตั้ง  perl-Class-MethodMaker

ถ้ารันคำสั่ง ndb_size.pl แล้วเกิด error เกี่ยวกับ Class-MethodMaker ให้ติดตั้ง  perl-Class-MethodMaker-2.10-1.el5.rf.x86_64.rpm ดังนี้ 
<table class="table table-bordered">
      <td>
        shell> rpm -ivh perl-Class-MethodMaker-2.10-1.el5.rf.x86_64.rpm
      </td>
</table>

การใช้งาน     
<table class="table table-bordered">
      <td>
        shell> ndb_size.pl --database=ชื่อฐานข้อมูล --socket=ที่อยู่ mysql.sock
      </td>
</table>


    ## ndb_size.pl --database=clusterkit --socket=/var/mysql/mysql.sock

