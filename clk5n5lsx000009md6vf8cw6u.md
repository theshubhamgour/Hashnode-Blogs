---
title: "Linux  -'Find' Knowledge Base - Exercise Bank"
seoTitle: "Linux  -'Find' Knowledge Base - Exercise Bank"
datePublished: Sun Jul 16 2023 16:18:36 GMT+0000 (Coordinated Universal Time)
cuid: clk5n5lsx000009md6vf8cw6u
slug: linux-find-knowledge-base-exercise-bank
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/YG8rZ323UsU/upload/153c4157a72e1c170a027a9661b857c2.png
tags: linux, aws

---

1\. Find all the files under /home directory with name passwd :

First you have to create a file in the home directory here we created passwd

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689513038631/04f8ab74-ef58-451d-920c-e6c2a1807372.png align="center")

```plaintext
[root@192 Desktop]# find /home -name passwd -type f
```

2\. Find all the files whose name is shadow in a /etc directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689513097801/8027244c-1f92-4828-af6f-762f3420ebeb.png align="center")

```plaintext
[root@192 Desktop]# find /etc -name shadow -type f
```

3\. Find all the files whose name is fstab and contains both capital and small letters in /directory.

In this case we created fstab files with the {} operator

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689513428512/7cefca4c-3784-43ba-8729-5aecd9cc41b0.png align="center")

```plaintext
[root@192 Desktop]# find /directory/ -type f -name [A-Za-z]*fstab
```

4\. Find all directories whose name is anaconda-ks.cfg in /directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689513723644/038cd061-e7a5-4737-a10f-ed702a1b8a57.png align="center")

```plaintext
[root@192 Desktop]# find /directory/ -type f -name anaconda-ks.cfg
```

5\. Find all php files in your system and copy them to the /backup directory

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689513943284/676a4eb3-388e-4697-8623-300eddd2c6b6.png align="center")

```plaintext
[root@192 Desktop]# find /directory/ -type f -name *php -exec cp {} /backup/ \;
```

6\. Find Files With 777 Permissions in system

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689514165101/15365473-9872-4235-ab2b-56a2a5c6b848.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -perm 777
```

7\. Find all the SGID bit files whose permissions set to 644.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689514326698/3544e904-70a2-433b-af46-8ae6e70f903b.png align="center")

```plaintext
[root@192 Desktop]# find / -perm 2644 -type f
```

8\. Find all the Sticky Bit set files whose permission are 551.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689514476490/0f688fea-b6b8-4905-9997-16a7688dd193.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -perm 1551
```

9\. Find all SUID set files.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689514555125/b29b686a-8410-42e3-ba9a-1ed5edb1c480.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -perm 4000
```

10\. Find all SGID set files.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689514648397/72dea666-3509-4185-a5b0-f4fd2628a100.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -perm 2000
```

11\. Find all 777 permission files and use chmod command to set permissions to 644.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689514760359/039d0aec-ca1b-44d4-91bd-f52fa995bbfa.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -perm 777 -exec chmod 644 {} \;
```

12\. Find all 777 permission directories and use chmod command to set permissions to 755.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689517111084/7240dcf6-5627-492c-8f5c-0d62995d2870.png align="center")

```plaintext
[root@192 Desktop]# find /testing/ -type d -perm 777 -exec chmod 755 {} \;
```

13\. To find a single directory called “yp” and remove it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689517456664/ac9549fc-893f-40d4-8efa-7ab3f027d2b8.png align="center")

```plaintext
[root@192 Desktop]# find / -type d -name yp -exec rm -rf {} \;
```

14\. To find and remove multiple files such as .mp3 or .txt, then delete this files using rm command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689518570804/21d97883-5aac-494d-869d-3f5fe49e253b.png align="center")

```plaintext
[root@192 Desktop]# find /file/ -type f -name *.mp3 -exec rm {} \;
```

15\. To find all empty files under /tmp directory

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689518794434/d1ab4694-4250-4903-9a16-ce6ed2f1a647.png align="center")

```plaintext
[root@192 Desktop]# find /tmp/ -type f -empty
```

16\. To find all empty directories under /tmp directory

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689518997494/c3e8f3af-17d0-4210-8f59-b711d7d5e131.png align="center")

```plaintext
[root@192 Desktop]# find /tmp/ -type d -empty
```

17\. To find all hidden files in /tmp

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689519653726/36646556-20a7-4f75-bebd-be3911746408.png align="center")

```plaintext
[root@192 Desktop]# find /tmp/ -type f -name '.*'
```

18\. To find all files that belong to user student under /home directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689519895623/02088db7-d8e2-4d5f-abeb-1369b1b21cd8.png align="center")

```plaintext
[root@192 Desktop]# find /home/ -type f -user student
```

19\. To find all or single file called student under / directory of owner student

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689521027698/73dab801-703a-47b7-a082-a10b9dc215c9.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -user student -name student
```

20\. To find all the files which are modified 50 days back.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689521303161/cedc7f5a-df03-4249-ac4f-ff9986aab65c.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -mtime +50
```

21\. To find all the files which are accessed 63 days back.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689521390441/15bac60c-d895-410c-ba71-e1b3d9ff7dc1.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -atime +63
```

22\. To find all the files which are modified more than 50 days back and less than 100 days.

```plaintext
[root@192 Desktop]# find / -type f -mtime +50 -mtime -100
```

23\. To find all the files which are changed in the last 1 hour.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689523835688/2359d1fd-881b-47ec-baa1-f446f69351cc.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -cmin -60
```

24\. To find all the files which are modified in the last 1 hour

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689523959580/c80088f9-1c83-4a17-94d5-91557a956267.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -mmin -60
```

25\. To find all the files which are accessed in the last 2 hour.

```plaintext
[root@192 Desktop]# find / -type f -amin -120
```

26\. To find all 50MB files, use.

```plaintext
find / -type f -size 50M
```

27\. To find all the files which are greater than 50MB and less than 100MB.

```plaintext
find / -type f -size +50M -size -100M
```

28\. To find all 100MB files and delete them using one single command.

```plaintext
find / -type f -size 100M -delete
```

29\. Find all .mp3 files with more than 10MB and delete them using one single command.

```plaintext
find / -type f -name "*.mp3" -size +10M -delete
```

30\. Find the files which are owned by (local user) natasha and copy it to /backup directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689524183462/c1d0bce7-9c5d-406e-b4b4-9d084ad99a88.png align="center")

```plaintext
[root@192 Desktop]# find / -type f -user natasha -exec cp {} /backup/ \;
```