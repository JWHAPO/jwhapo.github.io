---
layout: post
title: GitHub commit 잔디가 심어지는 조건..
---
  
    
    
  
  
 ## 현상..  
 퇴근 후 공부 또는 개인프로젝트를 조금씩 하고 있는데,  
 조금 더 규칙적으로 하자는 생각에 우선 일주일을 목표로 **1일 1잔디**를 다짐했다.  
 ~~내 정수리마냥~~ 듬성듬성했던 잔디밭이 채워지는 것을 보면서 코딩에 박차를 가할 때 쯤  
 어제 내가 분명히 심었던! 잔디가 보이지 않는다..  
   
 ![count of my contributions](https://github.com/JWHAPO/jwhapo.github.io/blob/master/images/the_condition_of_GitHub_commit_count/jandi.png?raw=true)
     
 ## 원인..  
 Git은 커밋을 할 때 설정된 사용자 정보를 가지고 하는데, 이 부분이 없으면 Contribution 카운트를 하지 않는다..  
 내가 작업하는 컴퓨터#2에는 이 설정을 빼먹은 것이다...  
 Git 설치하고 바로 했었어야했는데..  
 GitHub에서 명시한 [Contribution Count 조건](https:help.github.com/articles/why-are-my-contributions-not-showing-up-on-my-profile/)을 참조!  
  

  

 ## 조치..  
 Git repository에 가서 아래와 같이 사용자 정보를 입력한다.  
 git config &#45;&#45;global user.name "enter your name"  
 git config &#45;&#45;global user.email youremail@email.com  
 &#40; &#45;&#45;global 은 자신의 시스템 전체 유저정보를 설정하는 키워드다. repository별로 하려면 &#45;&#45;global을 뺀 후 입력!&#41;  
   
 결국 이 문제는.. Git 설치후 해야될 설정들을 안한 나의 잘못...ㅠㅠ  
 새로 잔디심기를 시작해야겠다..  

 ## GitHub 잔디심기란?  
 GitHub 자신의 페이지에 들어가보면 아래의 사진과 같이 자신이 Contribution한 수를 일자별로 표시해준다.  
 Contribution한 수에 따라 회색(0),연한 초록색부터 짙은 초록색까지 5가지 색으로 표시된다.  
 이 표를 초록색으로 채우는 행위를 **잔디심기**라 칭하는 듯하다.   
   
 
  
