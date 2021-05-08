---
layout: post
permalink: /facebook-domain-verification-imweb/
title: "페이스북 도메인 인증하는 방법 - 아임웹"
date: 2021-05-04 10:35:00 +09:00
feature: '/img/posts/facebookdomain/post3_thumb.png'
categories:
  - tutorial
tags:
  - 페이스북 마케팅
  - 페이스북 도메인 인증
  - 페이스북 픽셀
description: '웹사이트 솔루션 중 아임웹의 페이스북 도메인 인증 방법을 알아봅시다.'
---

애플의 iOS 14 릴리즈로 인해 페이스북 픽셀이 전환 이벤트를 수신하고 처리하는 데에 영향을 받게 되어, 페이스북은 이에 대응하기 위해 몇 가지 조치를 권장하고 있습니다. 도메인 인증은 그 중 하나이며, 인증 후에는 페이스북의 '취합된 이벤트 측정'을 사용해 이벤트를 수집할 수 있습니다.

이번 글에서는 웹사이트 솔루션 중 **아임웹**의 페이스북 도메인 인증 방법을 알아보겠습니다. 3가지 인증 방법 중 아임웹 관리자 페이지에서 간단하게 할 수 있는 **메타 태그 인증** 방식으로 해보겠습니다.

1. [페이스북 비즈니스] - [비즈니스 설정]으로 이동합니다.
![페이스북 비즈니스 홈 좌측하단의 '비즈니스 설정'](/img/posts/facebookdomain/facebookbusinesshome.PNG)*페이스북 비즈니스 홈 좌측하단의 '비즈니스 설정'으로 이동*

2. 왼쪽 목록 중 [브랜드 가치 보호] - [도메인]으로 이동합니다.
![페이스북 도메인 인증탭](/img/posts/facebookdomain/addnewdomain.PNG)*페이스북 도메인 인증탭 선택*

3. [추가]를 누르고 나타나는 창에 도메인을 입력한 후 [도메인 추가]를 누르세요. 저는 제 도메인 "hard-carry.com"으로 인증해보겠습니다.
![페이스북 도메인 추가](/img/posts/facebookdomain/adddomain.PNG)

4. 도메인이 리스트에 추가된 것을 확인하고, 도메인 인증 방법 세 가지 중 [메타 태그 인증]을 선택합니다. 인증 단계 1번의 ```<meta name=``` 으로 시작하는 코드를 클릭하면 자동으로 클립보드에 복사가 됩니다.
![페이스북 도메인 인증 메타 태그 인증](/img/posts/facebookdomain/domainvalidmetatag.PNG)*페이스북 도메인 인증 메타 태그 인증*

5. 아임웹 관리자 페이지의 왼쪽 메뉴에서 [환경설정]-[SEO, 헤더설정]으로 이동합니다. Meta Code 라는 제목 아래의 코드 입력창에 복사한 코드를 붙여넣고 오른쪽 상단의 **[저장]을 눌러 설정을 저장하세요.** 다른 서비스에서 도메인 소유권을 확인할 때에도 메타 태그를 여기에 삽입하면 인증할 수 있습니다.
![아임웹 메타 태그 삽입](/img/posts/facebookdomain/metatag.PNG)*아임웹 [SEO, 헤더설정]의 Meta Code에 메타 태그 입력*

6. 다시 페이스북 비즈니스의 도메인 탭으로 돌아와 인증을 클릭하면 인증이 완료됐다는 팝업이 뜨면서 도메인 옆에 "인증됨"이라는 문구를 확인할 수 있습니다. 만약 인증이 실패되었다면 잠시 후에 다시 인증을 눌러보세요.
![페이스북 도메인 인증 성공](/img/posts/facebookdomain/domainvalidsuccess.PNG)

다른 웹사이트 솔루션에서도 메타 태그를 삽입할 위치를 잘 찾는다면 같은 방법으로 페이스북 도메인 인증이 가능합니다. 페이스북 도메인 인증에 대한 더 많은 정보는 [Facebook for Developers](https://developers.facebook.com/docs/sharing/domain-verification){:target="_blank"}에서 확인할 수 있습니다.
