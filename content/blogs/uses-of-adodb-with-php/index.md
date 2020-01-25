---
title: 'การใช้งาน adodb กับ PHP'
date: 2010-02-24T14:40:41+07:00
draft: false
---
adodb เป็น database wrapper library เพื่อเป็นตัวกลางในการติดต่อระหว่าง PHP และ Database เพื่อให้ PHP เป็นอิสระจาก Database ซึ่งถ้าเราจะเปลี่ยน Database ที่จะใช้ในระบบ อาจเพราะ database เดิมรองรับไม่ไหวแล้ว ซึ่งถ้าไม่มี Database wrapper นั้น จะเป็นเรื่องใหญ่มากในการเปลี่ยน Database เพราะเราต้องมาแก้ code ในการติดต่อกับ Database ทั้งหมด  แต่ถ้าเราใช้ Database wrapper เช่น adodb ก็จะสามารถเปลี่ยน Database ที่ใช้งานได้ทันทีโดยกำหนดที่การติดต่อของ adodb ไปยัง Database ใหม่เท่านั้นเอง


    <?php
    //กำหนดการติดต่อแฟ้มข้อมูล
    $host = "localhost"; // กำหนด hostname
    $user = "user"; // กำหนด user ของ database
    $password = "pass"; // รหัสผ่านของ database
    $dbname = "dbname"; // ชื่อฐานข้อมูล ที่ใช้
    $dbms = "mysql"; // ชื่อ ระบบฐานข้อมูล (Database) ที่ใช้งาน เช่น mysql,postgresql,oracle

    include "adodb/adodb.inc.php"; // include adodb libraly
    $conn = &ADONewConnection($dbms); // adodb connect    
    $conn->Connect($host,$user, $password, $dbname); //Connecting to your DBMS.
    $sql = "SELECT table_id,table_name FROM table"; // ประโยค SQL
    $result = $conn->Execute($sql); // ประมวลผล sql
    	// show result 
    	while (!$result->EOF) {
    		echo $result->fields['table_id'];
    		echo $result->fields['table_name'];
		    $result->MoveNext();
		}
		$result->Close();
    ?>

