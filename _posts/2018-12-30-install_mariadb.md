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

#2. MariaDB 시작  
*$ systemctl start mariadb*  
  
#3. MariaDB root 암호 및 기본 보안설정  
*$ mysql_secure_installation*  

### Database 접속   
*$ mysql -u root -p*  

### Port 변경방법
*$ vi /etc/my.cnf.d/server.cnf*  
*$ systemctl restart mariadb* (변경 안되면... 재부팅...)  

### Port 확인방법  
*Maria DB> SHOW GLOBAL VARIABLES LIKE 'PORT';* 

### 설정한 PORT 방화벽 OPEN 방법  
*firewall-cmd --permanent --add-port=3456/tcp*  
*firewall-cmd --reload*   

### Maria DB 계정 생성  
# root 접속  
*$ mysql -u root -p* ( 패스워드 입력  )  
  
# database 목록 확인  
*Maria DB> SHOW DATABASES';*  

# 사용할 database 선택  
*Maria DB> USE mysql;*  (선택하고자 하는 database가 없다면 *CREATE DATABASE DB명;*)  

# 선택한 database에 user 확인  
*Maria DB> SELECT host,user,password from user;*  

# User 생성 (mysql 보안상 외부접속을 허용하지 않음, 계정 생성 시 특정 IP 혹은 %를 지정하여 외부접속을 허용한다.)  
*Maria DB> CREATE USER 'ID'@'IP or %' identified by 'PASSWORD';*  

# 권한 주기  
*Maria DB> GRANT ALL PRIVILEGES ON DB명.테이블명(*가능) to 'USER ID'@'IP or %';*  

# 권한 확인  
*Maria DB> SHOW GRANTS FOR 'USER ID'@'IP or %';*  

# User 삭제  
*Maria DB> DROP USER 'USER ID'@'IP or %';*  

# 권한 삭제  
*Maria DB> REVOKE ALL ON DB명.테이블명(* 가능) FROM 'USER ID'@'IP or %';* 



