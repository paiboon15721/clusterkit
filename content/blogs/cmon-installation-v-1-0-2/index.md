---
title: 'Cmon Installation V.1.0.2'
date: 2010-04-05T17:34:20+07:00
draft: false
---
CMON เป็นซอฟต์แวร์สำหรับเฝ้าดูสถานะการทำงานของระบบ  MySQL Cluster พรัอมยังเก็บ รวบรวมข้อมูลที่เกี่ยวข้องกับเครื่อง Data node และเครื่อง Management node นอกจากนี้ยังสามารถตรวจสอบการทำงานของเครื่องในะระบบได้ เช่น เก็บสถิติการใช้งาน, การแจ้งเตือนกรณีมีปัญหา เกิดขึ้น (อาทิ มีเครื่อง down หรือ เครื่อง Data node ใช้ data memory สูงเกินไป)

CMON เป็นซอฟต์แวร์สำหรับเฝ้าดูสถานะการทำงานของระบบ  MySQL Cluster พรัอมยังเก็บ รวบรวมข้อมูลที่เกี่ยวข้องกับเครื่อง Data node และเครื่อง Management node นอกจากนี้ยังสามารถตรวจสอบการทำงานของเครื่องในะระบบได้ เช่น เก็บสถิติการใช้งาน, การแจ้งเตือนกรณีมีปัญหา เกิดขึ้น (อาทิ มีเครื่อง down หรือ เครื่อง Data node ใช้ data memory สูงเกินไป)
ไฟล์ในการติดตั้งของ CMON มี 2 แบบ คือ source code และ binary
การติดตั้งด้วยไฟล์ source code
 เนื่องจาก CMON เป็นเว็บแอปพลิเคชั่นดังนั้นจะมีซอฟต์แวร์ที่เกี่ยวข้องดังนี้

1. ติดตั้ง Apache Web Server
2. ติดตั้ง PHP ที่สามารถติดต่อกับ mysql ได้
3. ติดตั้ง GNU compiler gcc/g++ สำหรับคอมไพล Source code ของ CMON
4. ติดตั้ง rrdtool เป็นเครื่องมือสำหรับสร้างกราฟบนหน้าเว็บของ CMON
5. เปิด slot ว่าง (SQL node หรือ API node) สำหรับ CMON สร้างเพิ่มเติมได้ในไฟล์ config.ini  

ก่อนติดตั้ง CMON ให้ติดตั้ง rrdtool ซึ่งสามารถใช้ไฟล์ที่มากับแผ่นซีดีได้
<table class="table table-bordered">
      <td>
        # rpm -ivh perl-rrdtool-1.2.23-1.el5.rf.x86_64.rpm  
        # rpm -ivh rrdtool-1.2.23-1.el5.rf.x86_64.rpm      
      </td>
</table>


## ขั้นตอนการติดตั้ง CMON 

## 1. ดาวน์โหลดและคอมไพล์ Source code

1.1 ให้ติดตั้งซอฟต์แวร์ CMON ไว้ที่เครื่อง MGM1 ท่านสามารถดาวน์โหลดไฟล์ติดตั้งได้ที่ http://www.severalnines.com/downloads/cmon/cmon-1.0.2.tar.gz หรือ ใช้ไฟล์ในแผ่นซีดี

1.2 แตกไฟล์ cmon-1.0.2.tar.gz
<table class="table table-bordered">
      <td>
        # tar -xvf cmon-1.0.2.tar.gz
      </td>
</table>
  

1.3 ทำการ configure และคอมไพล์ source code
<table class="table table-bordered">
      <td>
        # cd cmon-1.0.2/  
        # ./configure –prefix=/usr/local/cmon/  
        # make  
        # make install 
      </td>
</table>

1.4 ตรวจสอบว่ามี API slot ว่างสำหรับ cmon หรือไม่ 
<table class="table table-bordered">
      <td>
        # ndb_mgm -e show

    Cluster Configuration
    [ndbd(NDB)] 2 node(s)
    id=3 @10.0.1.3  (mysql-5.1.39 ndb-7.0.9, Nodegroup: 0, Master)
    id=4 @10.0.1.4  (mysql-5.1.39 ndb-7.0.9, Nodegroup: 0)

    [ndb_mgmd(MGM)] 2 node(s)
    id=1 @10.0.1.1  (mysql-5.1.39 ndb-7.0.9)
    id=2 @10.0.1.2  (mysql-5.1.39 ndb-7.0.9)

    [mysqld(API)] 6 node(s)
    id=7 @10.0.1.1  (mysql-5.1.39 ndb-7.0.9)
    id=8 @10.0.1.2  (mysql-5.1.39 ndb-7.0.9)
    id=9 (not connected, accepting connect from any host)
    id=10 (not connected, accepting connect from 10.0.1.5)
   </td>
</table>
    จากตัวอย่างนี้มีว่าง 2 slot สามารถทำขั้นตอนต่อไปได้

## 2. เริ่มต้นการติดตั้ง 

  2.1 ติดตั้ง cmon ด้วยสคลิปไฟล์
  <table class="table table-bordered">
      <td>
        # cd /usr/local/cmon/bin/ <br>
        # ./cmon_install.sh
      </td>
</table>
           
ทำตามขั้นตอนของไฟล์สคลิป โดยกำหนดค่าต่าง ๆ ตามด้านล่างนี้
This script will install cmon, rrd, init.d scripts, and generate SQL scripts for GRANTs
Distribution: CentOS

**** MYSQL CONNECTION ****

    CMON and the  RRD scripts needs a mysql connection to speak mysql server holding the 
    cmon database. <br>
    Specify the BASEDIR where mysql is installed (default /usr/local/mysql/): /usr/

    Specify the hostname of the mysql server having the cmon database (default 'ndb05'): 
    localhost

    Specify the port of the mysql server having the cmon database (default 3306): <return>
    No port specified - using default 3306

    Specify the password for the 'cmon' user (default no password): <return> <br>
    No password specified - using default (no password)

    Specify the ndb-connectstring to the cluster (e.g, host_A;host_B): mgm1;mgm2 <br>
    ## Comment: mgm1;mgm2 are the hostnames of the two management <br>
    ## servers in my cluster. YOU MUST SPECIFY THIS! 

****  WWW interface ****

    ## The www files will be copied to /var/www/html/cmon/
    ## Comment: The installation scripts tries to find the default
    ## location for www used in your distribution
Specify the WWWROOT of your webserver (default /var/www/html):  < return>
Copying files to /var/www/html ..

****  RRD ****

    ## Comment: If you don't have RRD installed then graphs will not be available
    ## from the web client, but there is no other functional impact!
    Specify the full path to 'rrdtool' (default is /usr/bin/): <return>
    No path to rrd specified - using default /usr/bin/

    The rrdtool stores data files in a data directory.
    Specify the full path to the data directory (about 20MB free space will be neeeded).
    RRD data directory (default is /data/rrd/): <return>
    No RRD data directory specified - using default /data/rrd/
    Saving ../etc/cmon.conf

**** INITD SCRIPTS ****

    Do you want to install /etc/init.d/cmon (y/n)? : y
    Specify the directory where CMON should write its pidfile (default /var/run/):<return>
    chkconfig
    Saving configuration to ../etc/init.d/cmon
    Installing /etc/init.d/cmon
    Done - Installed init.d scripts
    Now you can start cmon with '/etc/init.d/cmon start'

**** INSTALL CRONTAB ****

    cron schedules jobs every 5 minutes to update the rrd database and generarate graphs 
    for the web interface. You are recommended to install the cron jobs
    Do you want to install cron jobs for cmon (y/n)? : y
    You need to issue the following GRANTs before starting CMON:

    mysql> GRANT super, replication client ON *.* TO 'cmon'@'localhost';
    mysql> GRANT select,update,insert,delete,create ON cmon.* TO 'cmon'@'localhost';

    Configuration now complete - you can edit the /usr/local/cmon/bin/../etc/cmon.conf 
    manually if you wish.

    Configuration is now complete, but you need to apply the suggest GRANTs to the cmon 
    database:

    ## COMMENT: Connect a mysql client to the cmon database and do
    ## (actual GRANTs are subject to your particular settings):

    GRANT super, replication client ON *.* TO 'cmon'@'localhost';
    GRANT select,update,insert,delete,create ON cmon.* TO 'cmon'@'localhost';

 2.2 สร้างฐานข้อมูล cmon และกำหนดสิทธิ์  
 <table class="table table-bordered">
      <td>
        # mysql -u root  
        mysql> create data base cmon;  
        mysql> GRANT super, replication client ON *.* TO 'cmon'@'localhost';   
        mysql> GRANT select,update,insert,delete,create ON cmon.* TO 'cmon'@'localhost';
      </td>
</table>
            
2.3 เริ่มการทำงานของ cmon
<table class="table table-bordered">
      <td>
        # /usr/local/cmon/sbin/cmon   
        Starting cmon version 1.0.2 with the following parameters:  
        --mysqlpasswd=  
        --mysqlhost=127.0.0.1  
        --mysqlport=3306  
        --ndb-connectstring=127.0.0.1  
        --savetime-clusterlog=48 (hours)  
      </td>
</table>

    If that doesn't look correct, kill cmon and restart with -? for help on the 
    parameters, or change the params in /etc/init.d/cmon

    You need to GRANT (and specify a password if you wish) the following on mysql on 
    127.0.0.1:
<table class="table table-bordered">
      <td>
       mysql> GRANT create,select,update,insert,delete on cmon.* to 'cmon'@'127.0.0.1'  <br>
       mysql> GRANT super on *.* to 'cmon'@'127.0.0.1';
      </td>
</table>
  

    Testing connection to mysqld..
    Connection ok..
    Please wait while cmon is starting up..
    Schema looks complete.
    Registering managed cluster with cluster id=1
    Managed cluster is already registered -  cluster id=1
    cmon has started successfully.
    Going to daemoinze.. - cmon will write a log in syslog from now
                
## 3. ตรวจสอบข้อมูลในฐานข้อมูล CMON
<table class="table table-bordered">
      <td> <pre>
# mysql -u root
mysql> use cmon;     

Database changed

mysql> show tables;
+-------------------------+
| Tables_in_cmon          |
+-------------------------+
| alarm                   |
| alarm_log               |
| backup                  |
| backup_log              |
| cluster                 |
| cluster_log             |
| cluster_state           |
| cluster_statistics      |
| configurator_nodemap    |
| diskdata                |
| email_notification      |
| mailserver              |
| memory_usage            |
| mysql_global_statistics |
| mysql_master_status     |
| mysql_server            |
| mysql_slave_status      |
| mysql_statistics        |
| mysql_variables         |
| node_state              |
| node_statistics         |
| restore                 |
| restore_log             |
| schema_object           |
+-------------------------+
24 rows in set (0.00 sec)

mysql> select status from cluster_state;
+---------+
| status  |
+---------+
| STARTED |
+---------+
1 row in set (0.00 sec)

mysql> select * from node_state;
+-----+--------+------------+-----------+-----------+---------------+---------+-------------+-----------------+---------------------+
| cid | nodeid | status     | node_type | nodegroup | host          | version | disconnects | last_disconnect | report_ts           |
+-----+--------+------------+-----------+-----------+---------------+---------+-------------+-----------------+---------------------+
|   1 |      1 | CONNECTED  | NDB_MGMD  |      NULL | 10.0.1.1      | 7.0.9   |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |      2 | CONNECTED  | NDB_MGMD  |      NULL | 10.0.1.2      | 7.0.9   |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |      3 | STARTED    | NDBD      |         0 | 10.0.1.3      | 7.0.9   |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |      4 | STARTED    | NDBD      |         0 | 10.0.1.4      | 7.0.9   |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |      7 | CONNECTED  | API       |      NULL | 10.0.1.1      | 7.0.9   |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |      8 | CONNECTED  | API       |      NULL | 10.0.1.2      | 7.0.9   |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |     13 | NO_CONTACT | API       |      NULL | 0.0.0.0       | NULL    |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |     12 | NO_CONTACT | API       |      NULL | 0.0.0.0       | NULL    |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |     11 | NO_CONTACT | API       |      NULL | 0.0.0.0       | NULL    |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |     10 | NO_CONTACT | API       |      NULL | 0.0.0.0       | NULL    |           0 | NULL            | 2010-01-13 12:00:56 |
|   1 |      9 | CONNECTED  | API       |      NULL | 10.0.1.5      | 7.0.9   |           0 | NULL            | 2010-01-13 12:00:56 |
+-----+--------+------------+-----------+-----------+---------------+---------+-------------+-----------------+---------------------+</pre>
      </td>
</table>

## 4. การใช้งาน CMON ผ่านเว็บ
 4.1 เปิดบริการของ Apache Web Server
 <table class="table table-bordered">
      <td>
        # service httpd start
      </td>
</table>
              
4.2 เปิดใช้งาน CMON ผ่านทางเว็บบราวเซอร์ http://localhost/cmon/
หมายเหตุ ในการใช้งานครั้งแรก ต้องทำการสร้างไฟล์ config_db1.php ผ่านทางหน้าเว็บโดยคลิกที่เมนู setup และกำหนดค่าของเครื่องที่สร้างฐานข้อมูล cmon ดังนี้\
<table class="table table-bordered">
      <td>
        Hostname : localhost  
        Port : 3306  
        Username : root  
        Password : [password]
      </td>
</table>
    สุดท้ายคลิกปุ่ม Test connection and continue

### การติดตั้งด้วยไฟล์ binary
1. ดาวน์โหลดไฟล์ http://www.severalnines.com/downloads/cmon/cmon-1.0.2-64bit-glibc23-mysqlcluster-709.tar.gz
2. แตกไฟล์
<table class="table table-bordered">
      <td>
        # tar xvfz cmon-1.0.2-64bit-glibc23-mysqlcluster-709.tar.gz
      </td>
</table>

3. เปลี่ยนชื่อไดเรกทอรี่
<table class="table table-bordered">
      <td>
        # mv cmon-1.0.2-64bit-glibc23-mysqlcluster-709 cmon
      </td>
</table>

4. ทำตามตั้งแต่ขั้นตอนที่ 2 จนถึงขั้นตอนที่ 4  ในการติดตั้งด้วยไฟล์ source code