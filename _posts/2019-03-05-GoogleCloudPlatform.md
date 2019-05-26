---
layout: post
title: Google Cloud Platform 적용중.
---

# GCP - SQL

GDG 머신러닝 스터디잼에서 알게된 GCP에 토이프로젝트 올려보는 중인데... 지금은 먼저 Database 먼저 올리고 있다. GCP에서 제공하는 DB는 현재 MySQL, Postgres 두 개 뿐인 듯하다!

일단 리전은 제일 가까운 도쿄로 하고..mySQL(버전 5.7) 올리고!! DB, User 생성했다.. 그리고 Computer Engine 도 생성했는데.. 이러다 과금 폭탄 맞는거 아닌지 모르겠다.. 일단 GCP 가입하면 1년 무료 300$에 수준의 크레딧을 제공한다...

DB생성하고 VM 생성하면 VM에 붙어서 mySQL client를 설치해야한다..

```
sudo apt-get update   

sudo apt-get install mysql-client   

mysql --host=[INSTANCE_IP_ADDR] \   
    --user=root --password
```

위 방법은 실패하여.. gcloud shell 을 사용했다.

```
$ gcloud config set project [클라우드프로젝트명]
$ gcloud beta sql connect [클라우드인스턴스명] —user=root
```
