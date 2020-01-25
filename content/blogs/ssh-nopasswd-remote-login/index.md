---
title: 'การ login ข้ามเครื่องผ่าน ssh โดยไม่ต้องกรอก password'
date: 2010-08-30T15:01:37+07:00
draft: false
---
การ remote login โดยไม่ต้องใส่ password นี้สามารถทำได้โดยการใช้ PKI (Public Key Infrastruture) เข้าช่วยในการทำ เพื่ออำนวยความสะดวกในการทำงาน ที่จะต้อง remote ระหว่างเครื่อง การ remote ไปยังเครื่องปลายทางโดยไม่ต้องใส่ password สามารถทำได้โดย

### เครื่องต้นทาง  
1. ทำการสร้ายคีย์ขึ้นมาโดยใช้คำสั่ง ssh-keygen
<table class="table table-bordered">
         <td>
            root@clusterkit:~# ssh-keygen  
            Generating public/private rsa key pair.  
            Enter file in which to save the key (/root/.ssh/id_rsa):  
            Created directory '/root/.ssh'.  
            Enter passphrase (empty for no passphrase):  
            Enter same passphrase again:  
            Your identification has been saved in /root/.ssh/id_rsa.  
            Your public key has been saved in /root/.ssh/id_rsa.pub.  
            The key fingerprint is:  
            d3:75:67:fe:d9:8d:1a:fe:a8:33:71:c1:45:48:b0:08 root@clusterkit-desktop  
            The key's randomart image is:  
            +--[ RSA 2048]----+  
            | ........................++......... |  
            +-------------------------+
         </td>
</table>

2. ทำการ copy คีย์ไปวางยังเครื่องปลายทาง และเปลี่ยนชื่อคีย์เป็น authorized_keys
<table class="table table-bordered">
         <td>
            root@clusterkit:~# scp /root/.ssh/id_rsa.pub  dest-ip:/root/.ssh/authorized_keys
         </td>
</table>

3. ทดลองทำการ ssh ไปยังเครื่องที่วางคีย์ไว้ จะสามารถเข้าได้โดยไม่ต้องใส่ password