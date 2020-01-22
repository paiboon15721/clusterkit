---
title: 'PXE Network Installation'
date: 2010-04-01T10:54:18+07:00
draft: false
---
การ install OS สำหรับเครื่องจำนวนมาก ๆ นั้นเป็นงานที่ต้องใช้เวลานาน กว่าจะ install แต่ละเครื่องเสร็จ  จะดีกว่าใหม ถ้าเราสามารถ install เครื่องทั้งหมดนั้นได้พร้อม ๆ กัน โดยผ่าน network เรามาลองเซ็ตระบบเพื่อ install Linux ผ่าน network กัน

### เริ่มต้นตรวจสอบ package
#### 1. ตรวจสอบ package เหล่านี้ว่ามีในระบบหรือไม่ โดยสั่ง
   <table class="table table-bordered">
         <td>
            # rpm -q syslinux dhcp tftp ftp dhcp httpd 
         </td>
   </table>

ถ้าแพ็คเก็จตัวใดยังไม่ได้ติดตั้งให้ติดตั้งโดยหา package จากแผ่น CentOS หรือ ผ่าน yum

เปิด Firewall

#### 2. เปิด port ที่ iptables โดย (Graphic mode)
1) ไปที่ System → Administration → Security Level and Firewall

2) ที่แท็บ Firewall options คลิกเลือก FTP, NFS4, HTTP เพิ่ม

3) ที่ other ports คลิก add เพื่ออณุญาตให้ port 69 ซึ่งใช้โดย tftp สามารถผ่านได้

4) คลิก apply และ ok

### Config DHCP  
#### คอนฟิกไฟล์ dhcpd.conf โดยตั้งค่าตามนี้
โดยที่ไฟล์จะอยู่ที่ etc/dhcpd.conf
<table class="table table-bordered">
        <td>
            
        # dhcp configuration file
        ddns-update-style none;
        # network 192.168.123.0 range from 192.168.123.151 to 192.168.123.200
        # subnet mask 255.255.255.0
        subnet 192.168.123.0 netmask 255.255.255.0 {
        range 192.168.123.151 192.168.123.200;
        option subnet-mask 255.255.255.0;
        #option broadcast-address 66.13.175.247;
        option routers 192.168.123.1;
        #option domain-name-servers 66.13.175.242, 4.2.2.2, 4.2.2.1;
        #option domain-name "ringofsaturn.com";
        default-lease-time 86400;
        max-lease-time 2592000;
        #server-name "DHCPserver";
        # option root-path "/tftpboot";
        # tftp server ip
        next-server 192.168.123.52;
        #boot loader from tftp
        filename "linux-install/pxelinux.0";         
   </td> 
</table>

กรณีที่ในเครื่องมีการ์ดแลนหลายใบ ให้ระบุการ์ดที่จะทำการแจก dhcp โดยกำหนดที่
กำหนดค่าการ์ดที่จะให้แจก dhcp ในกรณีที่มีการ์ดหลายใบในเครื่อง โดยกำหนดที่ /etc/sysconfig/dhcpd และทำการเปลี่ยนค่าของ Interface DHCPDARGS=ethX โดย ethX เป็นการ์ดที่จะกำหนดให้แจก dhcp
<table class="table table-bordered">
   <td>

        # Command line options here
        DHCPDARGS=eth0
   </td>
</table>

### Start Web Server

สั่ง start service httpd เพื่อให้ web server start ขึ้นมา  และทำการสร้าง directory ขึ้นมาและนำไฟล์ในแผ่น dvd ของ centos มาเก็บไว้ที่ directory นี้ทั้งหมด  หรือไม่ก็ทำการ mount ไฟล์ iso มายัง directory ที่สร้างขึ้น

### Config Service TFTP

1. คอนฟิกไฟล์ tftp โดยไปที่ /etc/xinetd.d/tftp โดยเพิ่ม -u nobody -s /tftpboot ที่บรรทัด server_args
   <table class="table table-bordered">
         <td>

            # default: off
            # description: The tftp server serves files using the trivial file transfer
            # protocol. The tftp protocol is often used to boot diskless
            # workstations, download configuration files to network-aware printers,
            # and to start the installation process for some operating systems.
            service tftp
            {
                socket_type = dgram
                protocol = udp
                wait = yes
                user = root
                server = /usr/sbin/in.tftpd
                server_args = -u nobody -s /tftpboot
                disable = no
                per_source = 11
                cps = 100 2
                flags = IPv4
            }
       </td>
   </table>


 

2. ก๊อปปี้ไฟล์ vmlinuz และ initrd.img จากแผ่น centos ซึ่งจะอยู่ที่ /image/pxeboot/ นำมาวางไว้ที่ /tftpboot/linux-install/

3. สร้างโฟลเดอร์ pxelinux.cfg

4. เข้าโฟลเดอร์ pxelinux.cfg

5. สร้างไฟล์ defaultโดยมีเนื้อหาดังนี้
   <table class="table table-bordered">
       <td>
         
            prompt 1
            label centos
            kernel vmlinuz
            append initrd=initrd.img 
       </td>
   </table>
label 1 // เป็นข้อความที่เมื่อบูทจาก network และพิมพ์ข้อความนี้จะเลือกบูท kernel และ image ที่ระบุไว้  
kernel vmlinuz // kernel ที่ระบุ  
append initrd=initrd.img // image ที่ระบุ  
network ks=http://192.168.123.50/ks.cfg // ระบุไฟล์ path file kickstart for auto install
 
6. สั่ง restart service dhcpd และ xinetd
   <table class="table table-bordered">
         <td>
            # service dhcpd restart  
            # service xinetd restart
         </td>
   </table>

7. นำเครื่องลูก มาต่อ บูตผ่าน pxe เมื่อได้รับ ip และขึ้น prompt แล้ว ให้พิมพ์ centos จะเข้าสู่การ setup ผ่าน network ซึ่งจะมีให้เลือกว่าจะลงผ่านวิธีใด (local CDROM, Harddrive, ,http, ftp, nfs) เลือก http และเลือกการ์ด network ที่เราต่อกับ network ที่รับ dhcp มา การ config ip ให้ใช้ dynamic ip เลย

8. ต่อไปให้กรอก Nameserver ip เป็นเบอร์ ipของ server

9. FTP site name /website name ให้ใส่ ip เครื่อง server

10. centos directory ให้ใส่ centos

11. จะเข้าสู่การลง os ปกติ