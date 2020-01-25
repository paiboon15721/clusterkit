---
title: 'กู้ grub เมื่อ grub พัง'
date: 2010-03-09T18:04:30+07:00
draft: false
---
grub เป็น bootloader ทำหน้าที่เลือกบูท os ต่าง ๆ ที่เรา install อยู่ในเครื่อง ถ้าวันดีคืนดี grub พังขึ้นมาเราจะทำยังไง ?

ดังนั้นเรามา reinstall grub กัน

1. Boot Linux จาก Live CD Distro ต่าง ๆ เช่น Ubuntu Live, Knoppix, Mepis, etc.
 
2. เมื่อบูตแล้วให้เปิด terminal ขึ้นมา แล้วเปลี่ยนสิทธิ์ให้เป็น root ("su" for non-Ubuntu distro หรือ "sudo -i" for Ubuntu).

3. พิมพ์ "grub" เพื่อเข้าโปรแกรม grub
   <table class="table table-bordered">
         <td>
            # grub  
         </td>
   </table>

4. จากนั้นใช้คำสั่ง "find /boot/grub/stage1" เพื่อค้นหา grub bootloader จาก harddisk จะเจอผลลัพธ์ประมาณว่า "(hd0,1)"
  <table class="table table-bordered">
         <td>
            grub > find /boot/grub/stage1  
            grub > (hd0,3) 
         </td>
   </table>
 
5. พิมพ์ "root (hd0,3)" .
grub > root (hd0,3)

6. จากนั้นก็พิมพ์ "setup (hd0,3)" เพื่อ reinstall grub กลับเข้าไป
grub > setup (hd0,3)

7. ออกจาก grub โดยพิมพ์ "quit"
  <table class="table table-bordered">
         <td>
            grub> quit
         </td>
   </table>
 
8. Restart เครื่อง แล้วเอาแผ่น CD ออกด้วย เพียงเท่านี้เราก็จะได้ grub กลับมา