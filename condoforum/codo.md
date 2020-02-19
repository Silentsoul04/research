# XSS

---

# Stored XSS via ``custom profile field``

> Position : Field name , Field title/labe

1. Create Custom field

![image-20200217141650537](assets/image-20200217141650537.png)

2. XSS execute :

- Admin page: 

![image-20200217141526610](assets/image-20200217141526610.png)

- User page: 

![image-20200217141709351](assets/image-20200217141709351.png)

---

# Unrestricted File Upload

In function create ``categories`` , upload file dont check extension , attacker can exploit it to upload webshell in admin role

> admin\modules\categories.php

![image-20200217145412546](assets/image-20200217145412546.png)

Demo :

1. Login and access link ``http://localhost:8081/codoforum.v.4.8.8/admin/index.php?page=categories``
2. Create Category and upload file .php

![image-20200217145930564](assets/image-20200217145930564.png)

3. Shell upload successfull : shell was stored in web server:

![image-20200217150146191](assets/image-20200217150146191.png)

- Although the function is for admin role , it can be a prerequisite to attack later