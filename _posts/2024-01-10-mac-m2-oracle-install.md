---
layout: post
permalink: /way-to-install-oracledb-on-silicon-mac-m2
title: 'M2칩 맥 OS 오라클DB 설치(docker, colima)'
date: 2024-01-10 15:00:00 +09:00
feature: '/img/posts/17_macm2oracleinstall/macm2oracleinstall_thumb.png'
categories:
  - dmt-note
tags:
  - 맥북 m2칩 오라클데이터베이스 설치
  - 도커
  - 맥북 오라클
  - mac os oracle
description: 'M2 Apple Silicon Mac에서 Oracle database를 사용할 수 있도록 설치해보겠습니다.'
---



M2 칩을 사용하는 Mac에서는 아직 Oracle Database 설치를 공식적으로 지원하지 않습니다.

colima와 docker를 통해 M2 칩 Mac에도 설치해보겠습니다.



## 1\. Homebrew install

홈브루가 설치되어 있지 않다면 설치가 필요합니다.

이미 설치되어 있다면 넘어가셔도 됩니다.

1-1. 홈페이지에서 아래 명령어를 복사해서 터미널에 입력합니다.

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

(참고) 홈브루 홈페이지 링크 : [https://brew.sh/](https://brew.sh/)

 

### 2\. colima install

처음에 docker 만으로 시도했다가 실패하고 colima를 사용했습니다. 

2-1. 아래 명령어로 콜리마를 설치하세요

```
brew install colima
```



### 3\. colima를 실행하고 docker를 사용하여 Oracle DB 실행하기

설치한 콜리마를 먼저 실행하고 도커를 사용합니다.

3-1. colima start

```
colima start --memory 4 --arch x86_64
```

3-2. docker로 오라클 이미지 당겨오기

\- deepdiver/docker-oracle-xe-11g 이미지를 당겨옵니다.

```
docker pull deepdiver/docker-oracle-xe-11g
```

3-3. 실행

```
docker run -d --name oracle11g -p 1521:1521 -p 8080:8080  deepdiver/docker-oracle-xe-11g
```

3-4. 도커 상태 확인

```
docker ps
```

실행 결과, deepdiver/docker-oracle-xe-11g 이미지가 추가되었다면 성공입니다.

3-5. docker 컨테이너 안에서 클라이언트 실행하기

```
docker exec -it oracle11g sqlplus
```



\---

자료 찾기에 어려움이 있어서 삽질을 많이 했네요.

멘토님 도움 덕분에 드디어 오라클 db 설치 완료했습니다.

도움되시길 바랍니다.