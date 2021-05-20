---
layout: post
permalink: /how-to-change-syntax-highlighter-in-jekyll/
title: 'Jekyll 블로그 : Syntax highlighter 테마 설정으로 코드블럭 꾸미기'
date: 2021-05-21 07:35:00 +09:00
feature: '/img/posts/06_syntaxhighlighter/syntaxhighlighter_thumb.png'
categories:
  - dmt-note
tags:
  - 지킬 블로그 css
  - 지킬 코드블럭
  - 코드블럭 테마 css
  - 신택스 하이라이터
  - 코드블럭 꾸미기
description: '코드 블럭 테마를 설정해보겠습니다.'
---

제 블로그의 지킬 테마에서는 기본 코드블럭이 매우 심심합니다. 코드블럭은 자고로 알록달록한 것이 매력이라고 생각하는 마개터이기 때문에, 저의 무채색 코드블럭을 알록달록하게 해주는 테마를 적용해보겠습니다.

아래의 [Rouge 테마 미리보기 사이트](https://spsarolkar.github.io/rouge-theme-preview/){:target="_blank"}로 이동해서 마음에 드는 테마를 찾아보고 선택하세요. 저는 어두운 배경에 구분 잘 되는 알록달록을 좋아하기 때문에 `base16.monokai.dark`로 선택했습니다.

👉 [Rouge 테마 미리보기 사이트](https://spsarolkar.github.io/rouge-theme-preview/){:target="_blank"}

🔻 `base16.monokai.dark` 테마 javascript 예시 모습

``` javascript
var hello = function(){
  var radio = document.getElementsByName('gender');
  for(i=0; i < radio.length; i++){
    if(radio[i].checked){
      var result = radio[i].value;
    }
  }
  return result;
}
```

원하는 테마를 선택하셨다면, 이름을 잘 기억해두세요.

![rouge theme preview](/img/posts/06_syntaxhighlighter/syntax_preview.PNG)*표시 부분이 선택한 테마 이름입니다.*

---

## 지킬 블로그 신택스하이라이터 적용 방법

##### 1. 명령 프롬프트에서 블로그가 있는 폴더에 아래와 같이 입력해서 테마를 설치합니다.

```ruby
gem install kramdown rouge
```

##### 2. 지킬 블로그 폴더 내 `_config.yml` 파일에 아래 내용을 추가합니다.

```ruby
markdown: kramdown
kramdown:
  input: GFM
  syntax_highlighter: rouge
```

저는 `markdown: kramdown` 은 이미 있었기 때문에 아래 세 줄만 추가했습니다. 기존의 내용을 확인해보고 추가하세요.

##### 3. 아래 내용을 입력하면 `base16.monokai.dark` 테마를 담은 `syntax.css`파일이 `assets/css` 경로에 생성됩니다.

```ruby
rougify style base16.monokai.dark > assets/css/syntax.css
```

위 내용에서 `base16.monokai.dark` 대신 원하는 테마 이름을 넣으면 해당 테마의 css 파일이 생성됩니다.

저는 assets 폴더 내부에 css 폴더가 없었기 때문에 css 폴더부터 만들고 실행했습니다. 본인에게 맞는 파일 경로를 확인하고 필요하다면 경로를 생성해서 설정하세요.

##### 4. 코드블럭을 만들고 확인해보세요.

코드블럭을 여는 ``` 뒤에 언어를 입력하면 해당 언어에 맞는 syntax highlighter가 적용됩니다.

```ruby
    ```javascript
    (여기에 코드를 입력하세요)
    ```
```

##### 참고 내용

* [Add syntax highlighting to your Jekyll site with Rouge](https://bnhr.xyz/2017/03/25/add-syntax-highlighting-to-your-jekyll-site-with-rouge.html)

* [Rouge Theme Preview Page](https://spsarolkar.github.io/rouge-theme-preview/)

* [Pygments CSS Theme Builder](http://jwarby.github.io/jekyll-pygments-themes/builder.html)
