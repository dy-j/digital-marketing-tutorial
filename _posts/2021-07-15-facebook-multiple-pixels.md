---
layout: post
permalink: /facebook-multiple-pixel/
title: '여러개의 페이스북 픽셀에 개별 이벤트 설정하는 방법'
date: 2021-07-15 18:00:00 +09:00
feature: '/img/posts/07_multiplepixel/multiplepixel_thumb.png'
categories:
  - tutorial
tags:
  - 페이스북 픽셀
  - 다중픽셀
description: '여러개의 페이스북 픽셀을 사용할 때, 특정 픽셀에만 수집되는 이벤트를 설정하는 방법을 알아봅시다.'
---

* 픽셀 설치 방법은 이전 게시물을 참고해주세요. 👉 [페이스북 픽셀 설치 및 작동 확인 방법 - 픽셀 헬퍼](https://hard-carry.com/facebook-pixel-connect/)

# 여러개의 픽셀이 필요한 경우

픽셀을 사용하는 목적과 관리하는 방법에 따라 여러개의 픽셀을 사용해야하는 경우가 있습니다.

최근 페이스북 픽셀을 설치할 일이 있었는데, 기존에 사용하던 픽셀은 두고 별도의 픽셀을 생성하여 새롭게 생성한 픽셀에만 수집되는 이벤트가 필요했습니다. 이벤트에 픽셀 아이디를 특정해주고, 다른 픽셀에 이벤트가 수집되는 것을 막는 코드를 사용할 수 있습니다.

외에도 여러개의 에이전시에서 각각 관리하는 픽셀이 있는 경우 등을 위해 특정 픽셀에만 수집되는 이벤트를 세팅하는 방법을 알아봅시다.

# 페이스북 픽셀ID 확인 방법

1. 페이스북 기본 코드에서 확인하기

페이스북 픽셀 기본 코드는 아래와 같이 생겼습니다. 아래 기본 코드에서 ```픽셀ID``` 부분에는 각 픽셀의 고유 ID가 들어갑니다.

```javascript
  <!-- Facebook Pixel Code -->
  <script>
    !function(f,b,e,v,n,t,s)
    {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
    n.callMethod.apply(n,arguments):n.queue.push(arguments)};
    if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
    n.queue=[];t=b.createElement(e);t.async=!0;
    t.src=v;s=b.getElementsByTagName(e)[0];
    s.parentNode.insertBefore(t,s)}(window, document,'script',
    'https://connect.facebook.net/en_US/fbevents.js');
    fbq('init', '픽셀ID');
    fbq('track', 'PageView');
  </script>
  <noscript><img height="1" width="1" style="display:none"
    src="https://www.facebook.com/tr?id=픽셀ID&ev=PageView&noscript=1"
  /></noscript>
  <!-- End Facebook Pixel Code -->
```

2. 페이스북 이벤트 관리자에서 확인하기

[페이스북 비즈니스 - 이벤트 관리자 - 데이터 소스]로 이동하면 왼쪽 리스트에서 픽셀 ID를 확인할 수 있습니다.

![이벤트 관리자에서 픽셀 ID 위치](/img/posts/07_multiplepixel/fbpixelid.png)*표시 부분이 픽셀ID입니다.*


# fbq('trackSingle') 함수와 fbq('trackSingleCustom') 함수

표준 이벤트 코드에서 사용되는 `fbq('track')` 함수 대신 `fbq('trackSingle')`함수를 사용하면 해당 이벤트를 수집할 픽셀을 특정할 수 있습니다.

`fbq('trackSingle')` 함수의 형태

```javascript
fbq('trackSingle', '픽셀ID', '이벤트명',{
    //매개변수
  });
```

* 참고 [표준 이벤트 리스트](https://developers.facebook.com/docs/facebook-pixel/reference#standard-events)

맞춤 이벤트는 `fbq('trackSingleCustom')`를 같은 방법으로 사용합니다.

```javascript
fbq('trackSingleCustom', '픽셀ID', '이벤트명',{
    //매개변수
  });
```




#### 참고자료

* [Accurate Event Tracking with Multiple Pixels](https://developers.facebook.com/ads/blog/post/v2/2017/11/28/event-tracking-with-multiple-pixels-tracksingle/)
