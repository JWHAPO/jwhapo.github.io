---
layout: post
title: Install Maria DB On CentOS 7
---

### MariaDB 란?
[Maria DB Wiki]: https://ko.wikipedia.org/wiki/MariaDB


### repo 설정

$ vi /etc/yum.repos.d/MariaDB.repo

```
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.1/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
```

### install Maria DB

$ yum install MariaDB-server
설치 중 질문이 몇개 나오고 대답(Y/N)을 입력하면 된다.

결과 사진.
![https://github.com/JWHAPO/jwhapo.github.io/blob/master/images/install_mariadb/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7,%202018-12-30%2017-47-40.png?raw=true
