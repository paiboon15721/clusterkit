---
title: 'HPC design'
date: 2021-03-29T10:48:58+07:00
draft: false
---
{{< image src="../blogs/hpc_design/hpc-architecture.png" title="" >}}

## HPC Cluster Design

ในหลักการออกแบบระบบ HPC ที่ควรจะเป็นนั้น จะเป็นการนำเครื่องคอมพิวเตอร์ความเร็วสูงจำนวนน้อยเครื่องมาติดตั้งเป็นระบบคลัสเตอร์ แทนที่จะใช้มากเครื่องเพื่อลดการติดต่อระหว่างโหนดผ่าน Network เนื่องจาก Network ของระบบมีความเร็วน้อยที่สุด จะเป็นคอขวดของระบบ 

ระบบ HPC นั้น FrontEnd Node จะทำหน้าที่แชร์ไฟล์ และกระจายโหลดงานไปยังเครื่อง Compute Node  โหลดในการประมวลผลต่าง ๆ จะเกิดอยู่ที่เครื่อง Compute Node ซึ่งจะติดต่อกันระหว่างเครื่องโดยผ่าน Network ดังนั้นในการออกแบบระบบ HPC  ส่วนประกอบต่าง ๆ ของระบบจึงควรสอดคล้องกัน โดยตัวอย่างคลัสเตอร์ขนาดเล็ก (8 Compute Node) จะออกแบบแต่ละส่วน ดังนี้

### FrontEnd Node
ทำหน้าทีหลักเป็นเครื่องบริหารจัดการระบบ จัดการคิวในการประมวลผล แชร์ไฟล์ไปยังเครื่อง Compute Node ในระบบ และ Compile Software ซึ่งไม่ต้องการ CPU ที่ต้องแรงมาก โดยใส่ CPUเพียงตัวเดียวก็น่าจะเพียงพอต่อการทำงาน   ส่วน RAM ไม่ต้องใส่เยอะ ซัก 16GB-32GB ก็เพียงพอ โดยโหลดส่วนใหญ่ของ FrontEndจะถูกใช้ในการบริหารจัดการระบบ และการแชร์ดิสก์ ส่วน Storage ของ FrontEnd แบ่งออกเป็น 2 ส่วน ส่วนแรกแบ่งดิสก์เล็ก ๆ 2 ลูก ทำ Raid1 สำหรับติดตั้ง OS  อีกส่วนหนึ่งใช้ดิสก์กลุ่มหนึ่ง ทำ RAID5 หรือ RAID6  สำหรับแชร์ดิสก์ไปยังเครื่อง Compute โดยทุกเครื่องจะเห็นไฟล์ที่เดียวกัน ซึ่งดิสก์ตรงนี้แนะนำใช้เป็น nvme หรือ SSD เพื่อรองรับการอ่านเขียนจากเครื่อง Compute Node หากดิสก์ตรงนี้ช้า ก็จะเป็นคอขวดของระบบ หากระบบมีCompute Node มากขึ้น เช่น 16 Compute Nodes ขึ้นไป แนะนำให้ทำระบบ Parallel File System เพื่อแชร์ไฟล์แยกต่างหาก เพื่อรองรับโหลดการอ่านเขียนจาก Compute Node เช่น Lustreหรือ BeeGFS

{{< image src="../blogs/hpc_design/frontend-node.png" title="" >}}

<table class="table">
  <tbody>
    <tr>
      <td>CPU</td> 
      <td>1 x Intel/AMD  at lease 8Core/16 Thread</td> 
    </tr>
    <tr>
      <td>RAM</td>
      <td>16-32GB</td>
    </tr>
    <tr>
      <td>Storage</td>
      <td>2 x 240GB SSD 7200rpm (OS)<br>
      8 x 3.2 TB MU SSD RAID6 (Data/Share Storage)<br>
      *Depend on data size **nvme prefer</td>
    </tr>
    <tr>
      <td>LAN</td>
      <td>1 x 10/25GbE (Private)<br>
      1 x 1GbE or 1 x 10/25 GbE(Public)<br>
      1 x Management (IPMI)</td>
    </tr>
    <tr>
      <td>PSU</td>
      <td>Redundant hot-swap supplies</td>
    </tr>
    <tr><td></td><td></td></tr>
    </tbody>
</table>


### Compute Node
เป็นส่วนประมวลผลข้อมูล ควรเลือก CPU ที่เร็วที่สุดหรือ Core มากๆ ในงบประมาณที่สามารถจัดหาได้ โดยเลือกใส่ 2 CPU ต่อเครื่อง ขนาดของ RAM ขึ้นอยู่กับ Application ที่รันว่าใช้ RAM เยอะหรือไม่ และเลือกการ์ดเครือข่ายความเร็วสูงสำหรับติดต่อกันระหว่างเครื่อง เพื่อไม่ให้เป็นคอขวดที่ Network 

<table class="table">
  <tbody>
    <tr>
      <td>CPU</td> 
      <td>2 x AMD/Intel CPU</td> 
    </tr>
    <tr>
      <td>RAM</td>
      <td>64-128GB ** Depend on Application</td>
    </tr>
    <tr>
      <td>HDD</td>
      <td>1 x 240 GB SSD</td>
    </tr>
    <tr>
      <td>LAN</td>
      <td>1 x 10/25GbE (Private)<br>
      1 x Management (IPMI)</td>
    </tr>
    <tr>
      <td>PSU</td>
      <td>Redundant hot-swap supplies</td>
    </tr>
    <tr><td></td><td></td></tr>
    </tbody>
</table>

### Compute Node (GPU)
Spec จะเหมือนกับ Compute Node  แต่ต้องดูเครื่องว่ารองการใส่ GPU ได้หรือไม่ สามารถเช็คเครื่อง Server รุ่นที่ Certified สามารถใส่การ์ด GPU ได้ที่

https://www.nvidia.com/en-us/data-center/resources/vgpu-certified-servers/

{{< image src="../blogs/hpc_design/nvidia.png" title="" >}}

### Network

Network ของระบบคลัสเตอร์อย่างน้อยต้องมี 2 วง 
- <b>Public Network :</b> จะอยู่ที่ FrontEnd ไว้เป็น Networkที่ User เข้ามาใช้งานระบบ 
- <b>Private Network :</b> ไว้สำหรับติดต่อระหว่างเครื่องในระบบคลัสเตอร์ แนะนำอย่างน้อย Networkควรมีความเร็ว 10/25GbE

{{< image src="../blogs/hpc_design/hpe-sn2010m-2.png" title="" >}}

หากมีงบประมาณมากพอควรเพิ่ม Network ความเร็วสูงอีกวงหนึ่งเพื่อให้เครื่องติดต่อกันผ่านวงนี้แทนเพื่อให้ติดต่อกันระหว่างเครื่องได้เร็วขึ้น

- <b>Hispeed Network :</b> Infiniband EDR / 100 GbE Ethernet

และหากเครื่องคอมพิวเตอร์มีพอร์ต Management (ILO,IDRAC,BMC) ที่สามารถสั่งคำสั่ง IPMI ไปยังอุปกรณ์ได้ ให้เพิ่ม Network Management อีกวงหนึ่ง

- <b>Management Network :</b> Gigabit Ethernet

## Example Spec

### Frontend spec : HPE DL325 gen10

<table class="table">
  <tbody>
    <tr>
      <td>CPU</td> 
      <td>1 x AMD  Epyc 8Core/16 Thread</td> 
    </tr>
    <tr>
      <td>RAM</td>
      <td>16-32GB</td>
    </tr>
    <tr>
      <td>Storage</td>
      <td>2 x 240GB SSD 7200rpm (OS)<br>
      10 x 3.2 TB MU SSD RAID6 (Data/Share Storage)<br>
      *Depend on data size **nvme prefer</td>
    </tr>
    <tr>
      <td>LAN</td>
      <td>2 x 1GbE (Public,IPMI management)<br>
      1 x 10/25GbE (Private)<br>
      1 x Management (IPMI)</td>
    </tr>
    <tr>
      <td>PSU</td>
      <td>Redundant hot-swap supplies</td>
    </tr>
    <tr><td></td><td></td></tr>
    </tbody>
</table>

### Compute node spec (8 nodes)

### Cpmpute Nodes : HPE DL385 gen10 Plus (6 x Compute Nodes)

<table class="table">
  <tbody>
    <tr>
      <td>CPU</td> 
      <td>2 x AMD 32 Cores</td> 
    </tr>
    <tr>
      <td>RAM</td>
      <td>64-128GB ** Depend on Application</td>
    </tr>
    <tr>
      <td>HDD</td>
      <td>1 x 240 GB SSD</td>
    </tr>
    <tr>
      <td>LAN</td>
      <td>1 x 10/25GbE (Private)<br>
      1 x Management (IPMI)</td>
    </tr>
    <tr>
      <td>PSU</td>
      <td>Redundant hot-swap supplies</td>
    </tr>
    <tr><td></td><td></td></tr>
    </tbody>
</table>

### GPU Nodes : HPE DL385 gen10 Plus ( 2 x GPU Node)

<table class="table">
  <tbody>
    <tr>
      <td>CPU</td> 
      <td>2 x AMD 32 Cores</td> 
    </tr>
    <tr>
      <td>RAM</td>
      <td>64-128GB ** Depend on Application</td>
    </tr>
    <tr>
      <td>HDD</td>
      <td>1 x 240 GB SSD</td>
    </tr>
    <tr>
      <td>LAN</td>
      <td>1 x 10/25GbE (Private)<br>
      1 x Management (IPMI)</td>
    </tr>
    <tr>
      <td>PSU</td>
      <td>Redundant hot-swap supplies</td>
    </tr>
    <tr>
      <td>GPU</td>
      <td>2 x Nvidia RTX8000</td>
    </tr>
    </tbody>
</table>

### Network : HPE SN2010M
- 100GbE Switch (Compute Network)  
- 10 x 3m DAC SFP28

{{< image src="../blogs/hpc_design/hpe-sn2010m.png" title="" >}}

### Network : HPE OfficeConnect 1420 16G Switch 
- 1GbE Switch
- 10 x 3m CAT5E Patch Cable

{{< image src="../blogs/hpc_design/switch.png" title="" >}}