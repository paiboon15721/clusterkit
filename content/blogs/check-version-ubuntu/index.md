---
title: 'Check Version ของ Ubuntu'
date: 2010-04-07T15:25:58+07:00
draft: false
---
Ubuntu นั้นเป็น linux distribution ที่มีการออก distribution ใหม่ที่เร็วมาก ๆ คือ ประมาณ 6 เดือน ซึ่งผู้ใช้งานบางทีก็อาจสับสนไม่แน่ใจว่า distribution ที่ใช้อยู่นั้นเป็นเวอร์ชั่นอะไร

ดังนั้นถ้าเราต้องการรู้เวอร์ชั่นของ Ubuntu ให้สั่ง lsb_release -a จะเป็นการสั่งให้แสดงเวอร์ชั่นของ ubuntu ออกมา
<table class="table table-bordered">
      <td>
        clusterkit@clusterkitNB:~$ lsb_release -a  
        LSB Version:  core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch  
        Distributor ID:    Ubuntu  
        Description:    Ubuntu 9.10  
        Release:    9.10  
        Codename:    karmic
      </td>
</table>


ซึ่งเราจะใช้คำสั่ง cat /etc/issue เพื่อให้แสดง version ได้เหมือนกัน
<table class="table table-bordered">
      <td>
        clusterkit@clusterkitNB:~$ cat /etc/issue  
        Ubuntu 9.10
      </td>
</table>

ซึ่งถ้าเป็นทาง Distribution อื่น ๆ ที่เป็นที่นิยมจะสั่งคล้าย ๆ กันคือ ตระกูล RedHat นั้นจะใช้คำสั่ง  cat /etc/redhat-release ตระกูล Slackware จะใช้คำสั่ง cat /etc/slackware-version