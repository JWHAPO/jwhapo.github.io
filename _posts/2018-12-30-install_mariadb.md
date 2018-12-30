---
layout: post
title: Install Maria DB On CentOS 7
---

### MariaDB 란?  
[Maria DB Wiki](https://ko.wikipedia.org/wiki/MariaDB)  


### repo 설정  

*$ vi /etc/yum.repos.d/MariaDB.repo*  

아래 입력  
*[mariadb]*  
*name = MariaDB*  
*baseurl = http://yum.mariadb.org/10.1/centos7-amd64*  
*gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB*  
*gpgcheck=1*  


### install Maria DB
#1. 설치  
*$ yum install MariaDB-server*  
설치 중 질문이 몇개 나오고 대답(Y/N)을 입력하면 된다.  

#2. 설치확인  
*$ rpm -qa | grep MariaDB*  

![image](https://github.com/JWHAPO/jwhapo.github.io/blob/master/images/install_mariadb/sc2.png?raw=true)

### Database  시작  

#1. MariaDB 서비스를 부팅할 때 자동실행 하도록 설정.  
*$ systemctl enable mariadb*  

#### 작성중...

