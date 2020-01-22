---
title: 'แก้ไขชื่อ network interface สำหรับ CentOS 6 และ Fedora'
date: 2013-02-13T11:03:23+07:00
draft: false
---

ในบางครั้งการติดตั้ง CentOS ในบางเครื่อง อาจจะเจอว่าเครื่อง detect network card เป็น em1 แทนที่จะเป็น eth0 ตามปกติ ซึ่งจะมีปัญหาสำหรับการคอนฟิกกับบางโปรแกรมที่ต้องใช้ชื่อ network interface เหมือนกันทั้งสองเครื่อง แต่เครื่องหนึ่ง detect เป็น eth0 ดัน detect เป็น em1 ดังนั้นเราจะเปลี่ยนให้ชื่อ interface ให้ตรงกัน โดยเปลี่ยน eth0 เป็น em1
โดยการเปลี่ยนชื่อขั้นแรกให้เข้าไปแก้ไขไฟล์ /etc/udev/rules.d/70-persistent-net.rule ให้แก้ชื่อ interface การ์ดที่ต้องการแก้ไข เช่น แก้จาก NAME="eth0" เป็น NAME="em1"

    # PCI device 0x8086:0x100e (e1000)
    SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?_", ATTR{address}=="08:00:27:34:69:35",  ATTR{type}  =="1", KERNEL=="eth_", NAME="em1"

    # PCI device 0x8086:0x100e (e1000)
    SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?_", ATTR{address}=="08:00:27:aa:ff:53", ATTR{type} =="1", KERNEL=="eth_", NAME="eth1"

จากนั้น copy ไฟล์ ifcfg-eth* ที่ต้องการแก้ ไปเป็นไฟล์ ifcfg-em* ที่ต้องการ เช่นจาก eth0 ไปเป็น em1
 <table class="table table-bordered">
         <td>
           # cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-em1
         </td>
   </table>


และเข้าไปแก้ไขไฟล์ ifcfg-em1 แก้บรรทัด DEVICE เป็นชื่อ interface ที่ต้องการ

    DEVICE="em1"
    BOOTPROTO="static"
    NM_CONTROLLED="yes"
    ONBOOT="yes"
    TYPE="Ethernet"
    IPADDR=192.168.1.10
    NETMASK=255.255.255.0

เมื่อแก้ค่าเรียบร้อยแล้ว ทำการ reboot เมื่อ boot ขึ้นมาใหม่ interface จะเปลี่ยนเป็นชื่อที่แก้แล้ว ถ้าต้องการเปลี่ยนชื่อจาก em1 เป็น eth0 ก็ให้ทำแบบเดียวกันเช่นกัน

