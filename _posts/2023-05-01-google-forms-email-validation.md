---
layout: post
permalink: /how-to-validate-email-in-Google-forms/
title: '구글 설문지 : 이메일 응답 형식 지정하기(오입력 방지, 응답 확인 기능 설정)'
date: 2023-05-01 15:00:00 +09:00
feature: '/img/posts/16_googleformsemail/googleforms-email_thumb.png'
categories:
  - dmt-note
tags:
  - 구글 설문지
  - 구글 설문지 오입력 방지
  - 구글 폼 이메일 응답 형식 지정
  - 이메일 입력 형태 설정
  - 이메일 입력 방식 고정
description: '구글 폼에서 정확한 이메일 형식대로 응답을 입력하도록 지정해봅시다.'
---

뉴스레터 구독이나 이벤트 참여 등을 위해 고객 정보를 수집할 유용한 구글 폼의 이메일 형식 지정 방법을 알아봅시다. 이메일 형식 지정은 구글 설문지에서 응답 확인 기능을 직접적으로 제공하기 때문에 전화번호 형식 지정보다 훨씬 쉽습니다.

## 구글 폼 응답 확인 기능으로 ‘이메일 형식’ 지정하는 방법

1. 질문의 답변 유형을 **단답형**으로 설정해주세요.

    ![구글 폼 이메일 형식 지정하기 - 단답형 선택](/img/posts/16_googleformsemail/googleforms-email_1.png)*답변 유형 : 단답형*

2. 질문의 오른쪽 하단의 점 3개(케밥 메뉴)를 클릭하여 **응답 확인**을 체크해주세요.

    ![구글 폼 이메일 형식 지정하기 - 응답 확인 선택](/img/posts/16_googleformsemail/googleforms-email_2.png)*응답 확인 설정*

3. 응답 확인 선택 시 나타나는 기능의 토글을 선택하여 [ 텍스트 > 이메일 ]로 차례로 선택해주세요.

    ![구글 폼 이메일 형식 지정하기 - 텍스트 이메일 선택](/img/posts/16_googleformsemail/googleforms-email_3.png)

    ![구글 폼 이메일 형식 지정하기 - 텍스트 이메일 선택](/img/posts/16_googleformsemail/googleforms-email_4.png)*텍스트 > 이메일*


4. 맞춤 오류 텍스트 자리에는 오입력시 나타내고 싶은 문구가 있다면 작성해주세요.

    저는 올바른 형식을 알려주기 위해서 “이메일 형식에 맞춰 입력해주세요. (예시 example@gmail.com)” 라고 작성했습니다. 맞춤 오류 텍스트 값은 꼭 입력하지 않아도 됩니다. 입력하지 않는 경우에는 “유효한 이메일이어야 합니다.”라는 안내 문구가 기본으로 설정되어 있습니다.

        ![구글 폼 이메일 형식 지정하기 - 맞춤 오류 텍스트 입력](/img/posts/16_googleformsemail/googleforms-email_5.png)*맞춤 오류 텍스트 입력*

5. 설문지 링크를 통해 잘 적용되었는지 확인해보세요.

    ![구글 폼 이메일 형식 지정하기 - 설문지 확인](/img/posts/16_googleformsemail/googleforms-email_6.png)*입력한 맞춤 오류 텍스트 노출*

    ![구글 폼 이메일 형식 지정하기 - 설문지 확인](/img/posts/16_googleformsemail/googleforms-email_7.png)*맞춤 오류 텍스트 미입력시 기본 문구 노출*

여러가지 신청서와 설문조사, 이벤트 참여를 위해 고객 정보를 수집할 때 많이 활용하는 구글 설문지의 이메일 질문의 답변 형식 지정 방법을 알아보았습니다. 이메일 문항 외에도 전화번호, 생년월일 문항의 형식을 지정하고 싶다면 아래 포스팅을 확인해보세요.

[구글 설문지 : 정규표현식을 사용하여 전화번호 형식 지정하기](https://hard-carry.com/how-to-validate-mobile-numbers-in-Google-forms-using-regular-expression/)
