---
title: "Django frontend"
date: 2021-03-13
categories: daily post
---
방문자가 웹사이트의 서버에 요청을 보내면 서버는 필요한 정보를 방문자에게 보냄.
클라이언트가 하는 행동은 request, 서버가 요청에 응하는 동작은 response.

요청의 종류에는 서버의 정보를 가져오는 것, 서버에 내용 저장, 삭제 등이 있음. 
사용자는 웹 브라우저에 URL을 입력해서 서버로 요청을 전달.
서버는 규칙에 따라 URL을 해석하여 응답. 

웹 프레임워크는 방문자의 다양한 요청을 서버에서 처리하고 그 결과를 방문자가 볼 수 있는 형태로 만들어서
다시 보내주는 기능을 쉽게 만들 수 있게 도와주는 도구이다.

아파치, Nginx는 컴퓨터가 서버로서 기능을 할 수 있도록 하는 웹 서버 소프트웨어.

장고의 장점
서버 프로그램을 설치하지 않고 파이썬 명렁어로 서버 실행 가능.
데이터베이스를 따로 설치할 필요 없음.

관리자 페이지를 자동으로 만들어줌.
보안 가이드에 따라 개발을 진행하게 되므로 큰 보안 실수를 하지 않게 됨.

플라스크는 장고에 비해 자유도가 높고 프레임워크에 덜 의존적으로 개발을 진행할 수 있음.

장고 -> 인스타그램, 유튜브, Spotify, washington post
플라스크 -> 넷플릭스, 우버, 링크드인

Cmder - DOS 명령어와 리눅스 명령어를 그대로 사용할 수 있음.

HTML과 CSS는 사용자가 서버에 특정 페이지를 요청하면 서버는 html과 css파일을 넘겨주고 사용자의
컴퓨터 브라우저는 이 파일을 렌더링해서 화면에 보여주는 방식이다.
이 방법은 정적인 페이지를 보여줄 때 적합한 형태이다. 화면 내용 중 아무리 작은 요소만
바꾸려고 해도 서버에 다시 요청해서 새 html파일과 css파일 전체를 다시 받아와야 한다. 

웹 브라우저 안에 동적인 부분을 만들 땐 자바스크립트를 사용한다.
```html
<!DOCTYPE html>
<html>
    <head>
        <title>soSmall's Homepage!</title>
        <link href="./practice.css" rel="stylesheet" type="text/css">

        <script type="text/javascript">
            function doSomething() {
                let a = document.getElementById('inputA').value;
                let b = document.getElementById('inputB').value;
                document.getElementById("valueA").innerHTML = a;
                document.getElementById("valueB").innerHTML = b;
                document.getElementById("valueC").innerHTML = Number(a) + Number(b);
            }

            function whatTimeIsIt() {
                alert(new Date());
            }

        </script>
    </head>
    <body>
        <nav>
            <a href="./index.html">Home</a>
            <a href="./blog_list.html">Blog</a>
            <a href="./about_me.html">About Me</a>
        </nav>

        <button onclick="whatTimeIsIt()">Current Time</button>
        <hr />

        <label for="inputA">a</label>
        <input id="inputA" value=1 onkeyup="doSomething()">
        <label for="inputB">b</label>
        <input id="inputB" value=2 onkeyup="doSomething()">

        <p><span id="valueA">1</span> + <span id="valueB">2</span> = <span id="valueC">3</span></p>

    </body>
</html>
```
