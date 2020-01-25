---
title: 'เปลี่ยน subnet/netmask บน Rocks Cluster ที่จะใช้ในวง compute'
date: 2013-02-15T11:45:57+07:00
draft: false
---
ถ้าต้องการเปลี่ยนวง ip address ที่ใช้ เช่นวง compute นั้น เราสามารถเปลี่ยนค่าในฐานข้อมูลโดยใช้คำสั่ง rocks set network ซึ่งมีการใช้งานดังนี้
ขั้นแรกสั่ง rocks list network เพื่อดูค่า network ปัจจุบัน ว่าชื่อ network อะไร มีค่าอะไรบ้าง
<table class="table table-bordered">
    <td>
        [root@test ~]# rocks list network  
        NETWORK  SUBNET        NETMASK       MTU   DNSZONE          SERVEDNS  
        private: 172.16.0.0    255.255.0.0   1500  local            True  
        public:  192.168.123.0 255.255.255.0 1500  clusterkit.co.th False  
   </td>
</table>

จากนั้นสั่งคำสั่ง rocks set network subnet <network name> <ip address> เพื่อเปลี่ยนค่าใน ฐานข้อมูล จากตัวอย่าง จะเปลี่ยนค่า network private  
<table class="table table-bordered">
    <td>
        [root@test ~]# rocks set network subnet private 10.1.1.0
    </td>
</table>

ทดลองสั่ง rocks list network จะเห็นค่า network ของ private เปลี่ยนไป
<table class="table table-bordered">
    <td>
        [root@test ~]# rocks list network private  
        SUBNET   NETMASK     MTU   DNSZONE SERVEDNS  
        10.1.1.0 255.255.0.0 1500  local   True 
   </td>
</table>
  

เปลี่ยน subnet โดยใช้คำสั่ง rocks set network netmask <network name> <subnet> เพื่อเปลี่ยน subnet
<table class="table table-bordered">
    <td>
        [root@test ~]# rocks set network netmask private 255.0.0.0
    </td>
</table>


ทดลองสั่ง rocks list network จะเห็นค่า network ของ private เปลี่ยนไป
<table class="table table-bordered">
    <td>
        [root@test ~]# rocks list network private  
        SUBNET   NETMASK   MTU   DNSZONE SERVEDNS  
        10.1.1.0 255.0.0.0 1500  local   True   
   </td>
</table>

เท่านี้ก็เปลี่ยน network private เรียบร้อยแล้ว อย่าลืมไปแก้ไขค่า network card ของเครื่อง frontend ให้เป็นเบอร์ในวงเดียวกับ subnet ที่เซ็ตใหม่นะครับ เดี๋ยวจะใช้ไม่ได้