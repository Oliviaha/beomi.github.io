---
title: "키노트로 고화질 타이틀 이미지 만들기"
date: 2017-11-10
layout: post
categories:
- macOS
- Tips
published: true
image: /img/2017-11-10-Export-HighQuality-Image-with-KeyNote.jpg
---

> 이번 글은 애플 키노트를 다루니 당연히 macOS가 대상입니다 :)

## 들어가며

블로그 글을 맥에서 작성하다보면 자연스럽게 키노트로 메인 타이틀이나 설명을 만드는 경우가 많습니다. 아래 화면처럼 이미지와 글자를 조금 배치하는 방식으로 깔끔한 이미지 하나를 만들게 됩니다. (이번 글 대표 이미지도 이 방식으로 만들었습니다.)

![](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.24.09.png?dl=1)

하지만 문제가 있습니다.

애플 키노트에서 기본적으로 제공하는 Export to Image, "다음으로 보내기 -> 이미지.."를 사용하는 방법도 물론 있습니다. 하지만 사실 이렇게 작업하면...

![](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.25.10.png?dl=1)

화면에서 바라볼때는 고해상도의 레티나 결과물이 나왔지만, 실제로 Export된 이미지 파일을 보면 이미지 픽셀은 `1920*1080`으로 충분히 고화질이지만 ppi가 72밖에 되지 않는 것을 볼 수 있습니다. 

![](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.29.35.png?dl=1)

(아니 왜 레티나를 샀는데 보여주지를 못하니 ㅠㅠ)

## 해결방법

해결방법은 한 단계를 더 거치는데, 다른 프로그램을 사용하는 것이 아니라 맥에 내장되어있는 '미리보기'를 이용하는 방법입니다.

단계는 다음과 같습니다.

- 키노트에서 PDF로 내보내기
- PDF파일을 '미리보기'로 열기
- 미리보기에서 '내보내기' 기능으로 고해상도 이미지 만들기

네, 귀찮습니다. 하지만 레티나 이미지를 포기할 수는 없으니까요. 요즘은 특히 모바일 기기도 해상도가 굉장히 높으니 그에 맞춰 높은 해상도를 제공해주는 것도 좋지 않을까 생각합니다.

그러면 이제 진행해 봅시다.

## 만들어봅시다!

### PDF로 내보내기

우선 위처럼 키노트를 만들어주세요. 그리고 아래 사진처럼 파일 > 다음으로 보내기 > PDF... 순서대로 클릭을 해주시면 됩니다.

![](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.36.07.png?dl=1)

클릭을 해주면 다음과 같은 창이 하나 뜹니다. 여기서 유의하셔야되는 점은 '이미지 품질'을 '최상'으로 해 두셔야 300ppi로 내보내기가 이루어집니다.

![](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.38.15.png?dl=1)

> NOTE: 여러분이 글자만 있는 상태라면 (아이콘/사진이 없다면) 굳이 이미지 품질을 신경쓰지는 않으셔도 됩니다. PDF에서 글자는 폰트를 내장해 글자 정보 자체로 읽고 쓰기 때문에 이미지 품질로 인한 차이가 발생하지 않습니다.

### 미리보기로 PDF 열기

앞서 내보내기로 만든 PDF 파일을 아래처럼 열어줍시다. 보기만해도 높은 해상도인것을 느낄 수 있습니다.

![미리보기로 PDF 열어본 모습](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.41.54.png?dl=1)

이제 상단 메뉴바 '파일'에서 '보내기'를 눌러봅시다.

![미리보기에서 내보내기](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.41.18.png?dl=1)

이제 아래와 같은 화면이 보일텐데요, PDF가 아니라 JPEG로 바꿔준 뒤 해상도를 150정도로 맞춰준 뒤 저장을 해줍시다.

![미리보기 내보내기에서 JPEG, 150PPI로 저장하기](/img/dropbox/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202017-11-09%2023.46.24.png?dl=1)

## 끝났습니다!

이제 여러분은 여러분이 원하는 해상도의 고해상도 이미지를 얻게 되었습니다! 

파일 사이즈를 조절하거나 무손실 압축 프로그램등을 사용한다면 좀 더 트래픽량이 줄어 사이트 로딩속도가 빨라질 수 있습니다.

> macOS에서는 ImageOptim을 이용해보세요. 이미지가 단순한 경우 용량이 절반으로 줄어들기도 합니다.