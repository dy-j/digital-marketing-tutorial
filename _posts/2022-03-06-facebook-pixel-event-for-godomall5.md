---
layout: post
permalink: /facebook-pixel-event-for-godomall5/
title: '고도몰5에 페이스북 픽셀 전환 이벤트 설정하기'
date: 2022-03-12 18:00:00 +09:00
feature: '/img/posts/12_facebookpixel2/facebookpixel2_thumb.png'
categories:
  - tutorial
tags:
  - 고도몰 페이스북 픽셀
  - 고도몰 메타 픽셀
  - 페이스북 전환 이벤트
description: '고도몰5에 페이스북 픽셀 전환 이벤트를 설정해봅시다.'

---

고도몰5로 운영 중인 쇼핑몰을 페이스북에 광고를 하기 위해서는 페이스북(메타) 픽셀 설치가 필요합니다. 페이스북 픽셀 설치 방법은 이전 게시물을 참고해주세요.

​	👉 [페이스북 픽셀 설치 및 작동 확인 방법 - 픽셀 헬퍼](https://hard-carry.com/facebook-pixel-connect/){:target="_blank"}

쇼핑몰 사이트에 페이스북 픽셀을 설치했다면, 전환 광고의 목표로 설정할 수 있는 이벤트를 설정해봅시다. 이벤트를 설정한다면 쇼핑몰에서 해당하는 이벤트(고객 액션)가 발생했을 때 페이스북 픽셀에서 데이터를 수집합니다. 이를 바탕으로 광고 성과를 측정하고, 타겟 그룹을 생성하거나 리타겟팅 광고에 활용할 수 있습니다.

# 1. 표준 이벤트

표준 이벤트는 페이스북이 이미 정의해둔 방문자의 행동입니다. 일반적으로 웹사이트에서 발생할 수 있는 '상세정보 조회, 구매 등'과 같은 공통적인 전환 액션입니다. 표준 이벤트는 매개변수를 지원하기 때문에 매개변수를 통해 이벤트에 대한 추가 정보(예: 제품 ID, 카테고리, 구매한 제품 수)가 포함된 개체를 포함할 수 있습니다.

일반적인 쇼핑몰에서 필요한 아래 행동들을 표준 이벤트로 수집하도록 세팅해봅시다.

* 제품 상세 보기(ViewContent)
* 장바구니 담기(AddToCart)
* 주문서 작성(InitiateCheckout)
* 주문 완료(Purchase)

> 출처 [페이스북(메타) 픽셀의 표준 이벤트](https://developers.facebook.com/docs/meta-pixel/implementation/conversion-tracking#standard-events){:target="_blank"}_
> 참고 [표준 이벤트 리스트](https://developers.facebook.com/docs/facebook-pixel/reference#standard-events){:target="_blank"}

# 2. 고도몰 관리자에서 각 스크립트 추가하기

이벤트 수집을 위한 스크립트는 고도몰 관리자 페이지에서 [디자인] - [디자인 관리]에서 각 페이지에 삽입합니다. 아래 설명을 통해 차근차근 따라해보세요.

### 1) 제품 상세 보기(ViewContent) 이벤트

'제품 상세 보기 이벤트'의 스크립트는 [상품 > 상품상세화면]파일의 가장 아래에 추가합니다. 아래 스크립트를 복사하여 추가하고 저장을 누릅니다.

```html
<script type="text/javascript">
  //페이스북(메타) 픽셀 이벤트 - 제품 상세 보기
  fbq('track', 'ViewContent', {
    content_ids : '{goodsView.goodsNo}',
    content_category : '{=goodsView['cateCd']}' ,
    content_name : '{=goodsView['goodsNm']}' ,
    content_type : 'product',
    currency : 'KRW',
    value : '{=gd_isset(goodsView['goodsPrice'],0)}'
  });
</script>
```

### 2) 장바구니 담기(AddToCart) 이벤트

'장바구니 담기 이벤트'도 '제품 상세 보기'와 같은 페이지에서 발생하는 이벤트이기 때문에 [상품 > 상품상세화면]파일의 가장 아래에 추가합니다. 아래 스크립트를 복사하여 추가하고 저장을 누릅니다.

```html
<script type="text/javascript">
  //페이스북(메타) 픽셀 이벤트 - 장바구니 담기
  var add_to_cart_btn = document.querySelector('#cartBtn');
  add_to_cart_btn.addEventListener('click', function(){
    fbq('track', 'AddToCart', {
      content_name : '{=goodsView['goodsNm']}' ,
      content_type : 'product',
      contents : [{
        'id' : '{goodsView.goodsNo}',
        'quantity' : goodsTotalCnt
      }],
      currency : 'KRW',
      value : '{=gd_isset(goodsView['goodsPrice'],0)}'
    });
  })
</script>
```

### 3) 주문서 작성(InitiateCheckout) 이벤트

'주문서 작성 이벤트'의 스크립트는 [주문 > 주문서 작성 / 결제]파일의 가장 아래에 추가합니다. 아래 스크립트를 복사하여 추가하고 저장을 누릅니다.

```html
<script type="text/javascript">
  //페이스북(메타) 픽셀 이벤트 - 주문서 작성
  var contentsInfo = [
    <!--{ @ cartInfo }-->
      <!--{ @ .value_ }-->
        <!--{ @ ..value_ }-->
          {
            id:'{=...goodsNo}',
            name:'{=...goodsNm}',
            category:'{=...cateCd}',
            variant:'{=...option[0]['optionValue']}',
            price:'{=...price['goodsPrice']}',
            quantity:'{=...goodsCnt}'
          },
      <!--{ / }-->
      <!--{ / }-->
    <!--{ / }-->
  ];
  fbq('track', 'InitiateCheckout', {
    contents : contentsInfo,
    currency : "KRW",
    value : '{=gd_global_money_format(totalSettlePrice)}'
  });
</script>
```

### 4) 주문 완료(Purchase) 이벤트

'주문 완료 이벤트'스크립트는 [주문 > 주문 완료]파일의 가장 아래에 추가합니다. 아래 스크립트를 복사하여 추가하고 저장을 누릅니다.

```html
<script type="text/javascript">
  //페이스북(메타) 픽셀 이벤트 - 주문 완료
  var contentsInfo = [
  <!--{ @ orderInfo.goods }-->
    {
      id:'{=.goodsNo}',
      name:'{=.goodsNm}',
      category:'{=.cateCd}',
      variant:'{=.optionInfo[0]['optionValue']}',
      price:'{=.goodsPrice}',
      quantity:'{=.goodsCnt}'
    },
  <!--{ / }-->
];
  fbq('track', 'Purchase', {
    content_type : 'product',
    contents : contentsInfo,
    currency : 'KRW',
    value : '{=orderInfo.settlePrice}'
  });
</script>
```

# 3. 이벤트 테스트를 통해 확인하기

모든 스크립트를 각 파일에 추가했다면, 이벤트 테스트를 통해 잘 작동하는지 확인해봅시다.

1. 페이스북 비즈니스 관리자에서 [이벤트 관리자](https://business.facebook.com/events_manager2/list/pixel/){:target="_blank"}로 이동해 고도몰에 설치한 픽셀을 선택하고 "이벤트 테스트" 탭을 누릅니다.

2. 웹사이트 URL 입력란에 고도몰 쇼핑몰 주소를 입력하고 '웹사이트 열기'를 누릅니다. 새 창으로 쇼핑몰 사이트가 열린 후, 이벤트 테스트에 *PageView 이벤트*가 정상적으로 실행되는지 확인하세요. (*PageView 이벤트*가 실행되지 않으면 기본 픽셀 태그가 제대로 설치되었는지 다시 확인하세요.)
   ![이벤트 관리자의 이벤트 테스트](/img/posts/12_facebookpixel2/eventtest.png)*이벤트 관리자의 이벤트 테스트*

3. 열린 쇼핑몰 사이트에서 표준 이벤트로 세팅한 액션들을 하나하나 실행해봅니다. 이벤트 테스트 페이지에서 각 액션별 세부 내용이 제대로 트래킹 되는지, 누락된 내용은 없는지 꼼꼼히 확인하세요.




* 제품 상세 보기(ViewContent)

![제품 상세 보기(ViewContent) 이벤트 테스트 결과](/img/posts/12_facebookpixel2/viewcontenttest.png)*제품 상세 보기(ViewContent) 이벤트 테스트 결과*

* 장바구니 담기(AddToCart)

![장바구니 담기(AddToCart) 이벤트 테스트 결과](/img/posts/12_facebookpixel2/addtocarttest.png)*장바구니 담기(AddToCart) 이벤트 테스트 결과*

* 주문서 작성(InitiateCheckout)

![주문서 작성(InitiateCheckout) 이벤트 테스트 결과](/img/posts/12_facebookpixel2/initiatecheckouttest.png)*주문서 작성(InitiateCheckout) 이벤트 테스트 결과*

* 주문 완료(Purchase)

![주문 완료(Purchase) 이벤트 테스트 결과](/img/posts/12_facebookpixel2/purchasetest.png)*주문 완료(Purchase) 이벤트 테스트 결과*


------

# 마치며

이렇게 세팅한 표준 이벤트는 정상적으로 수집되기 시작하면 이벤트 우선순위 세팅을 통해, 페이스북 광고 운영시 전환 목표로 설정할 수 있습니다. 전환 목표를 통해 페이스북 광고를 효율적으로 운영해보세요.
