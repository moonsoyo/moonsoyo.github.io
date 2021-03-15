---
title: "Bootstrap Intro"
date: 2021-03-14
categories: daily post
---
부트스트랩은 웹 개발에 있어 널리 쓰이는 구성 요소들을 미리 디자인 해 둔 툴킷이다. 
부트스트랩은 다양한 화면 크기에 대응할 수 있는 반응형 웹을 지향하기 때문에
화면의 크기에 따라 유연하게 변화하는 ux/ui 적용이 가능하다.

부트스트랩 웹사이트에서 코드를 바로 가져오는 방식을 Contents Delivery Network라고 부른다. 
내려받은 압축파일에서 bootstrap.min.js 파일을 활용할 수도 있지만 그럴려면 jQuery, proper.min.js 등도 필요하므로 CDN을 이용해준다. 

부트스트랩을 사용해서 쉽게 navBar을 만들어 줄 수 있다.
페이지에 여백을 주려면 container를 사용해준다.
grid 기능을 사용하면 웹 페이지를 세로 12칸으로 나누어 관리할 수 있다. 
화면 크기를 다양하게 바꾸어도 그 크기에 맞게 웹 페이지 모양도 바뀌어 나타난다.

<div class="row">

이 안에 있는 내용을 행 하나로 보겠다는 의미이다.
그 안에 col-9 과 col-3을 해주면 열로 나누어서 내용물을 넣을 수 있다. 

documentation -> utilities -> colors 로 가면 색깔 예시가 있다. 

부트스트랩에서 마진은 m-숫자 로 줄 수 있다.
mb-숫자 sms dkfodp my-숫자는 위아래 모두에 mt-숫자는 위에 마진을 준다. 

ml-auto 오른쪽 정렬
mr-auto 왼쪽정렬

startbootstrap.com 에서 좋은 예제 많이 제공.
control + u를 누르면 소스 코드를 볼 수 있음.

pagination, footer도 추가 가능.

modal은 브라우저 위에 팝업 형태로 나오는 요소이다. 
btn-block, btn-sm의 역할은?
아이콘은 Font awesome을 사용하면 된다. 