---
title: '브라우저 렌더링 과정을 간단하게 알아보자'
date: '2021-04-19'
tags: ['Computer', 'Rendering']
draft: false
author: Rumi
summary: '렌더링 과정을 간단하게 설명한다. 주소창에 URL을 입력하고, DNS를 조회한다. HTTP메시지를 만들어 서버에 요청을 보내고, 서버로부터 응답을 받는다. HTML 파싱 및 DOM Tree를 생성한다.CSS파싱 및 CSSOM Tree를 생성한다. DOM + CSSOM 으로 Render Tree를 생성하고, Layout Paint 과정을 거친다.'
---

# 소제목

_원문링크_: [notion](https://www.notion.so/9f0795fd07324209bb982ac243edee66)

### 1. 주소창에 URL을 입력한다.

![image](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F40092fe7-bb46-4c5f-93f6-6179f58bed43%2FFrame_132.png?table=block&id=79a45de2-9e97-453c-94ed-4ba2d866c7cc&width=4110&userId=&cache=v2)

### 2. URL을 분석하여 DNS를 조회한다.

**\*DNS(domain name server)**

- PC는 미리 설정되어 있는 Local DNS에게 **www.notion.so이라는 host**에 대한 IP 주소를 물어본다.
- Local DNS가 노션의 IP주소를 모르면, 다른 DNS 서버들과 통신(DNS 메시지)을 시작한다.
- 먼저 Root DNS 서버에게 물어본다. Root DNS 서버는 전세계에 13대가 구축되어 있다. (한국은 없다)
  [https://한국인터넷정보센터.한국/jsp/statboard/dns/dnsRoot/currentWorld.jsp](https://xn--3e0bx5euxnjje69i70af08bea817g.xn--3e0b707e/jsp/statboard/dns/dnsRoot/currentWorld.jsp)
- Root도 노션의 IP주소를 모르면, .so DNS서버에 물어본다. 얘도 모르면 notion.so DNS 서버에 물어본다.
- Local DNS 서버가 여러 DNS 서버를 차례대로 (Root DNS 서버 → so DNS 서버 → notion.so DNS 서버) 물어봐서 그 답을 찾는 과정을 **Recursive Query**라고 한다.
- 이렇게 해서 www.notion.so의 IP를 Local DNS가 알게되면, IP 주소를 캐싱 하고(다른사람이 이 주소를 찾는다면 바로 알려 줄 수 있도록) 그 IP 주소 정보를 내 PC에 전달해 준다.

### 3. HTTP Request(요청)

- HTTP 메시지를 만들어 서버에 요청을 보낸다.
- "이 URL의 파일조각을 줘."

### 4. HTTP Response(수신)

- 서버로부터 HTML CSS 파일을 받는다.

### 5. HTML 파일 파싱 및 DOM Tree를 생성한다.

**\* DOM(Document Object Model)은 HTML 문서에 대한 인터페이스이다.**

첫째로 뷰 포트에 무엇을 렌더링 할지 결정하기 위해 사용되며, 둘째로는 페이지의 콘텐츠 및 구조, 그리고 스타일이 자바스크립트 프로그램에 의해 수정되기 위해 사용된다. 항상 유효한 HTML 형식이며, 자바스크립트에 수정될 수 있는 동적 모델이여야 한다. 또한 가상 요소를 포함하지 않으며, 보이지는 않으나 HTML에 존재하는 요소를 포함한다.

### 6. CSS 파싱 및 CSSOM Tree를 생성한다.

### 7. DOM , CSSOM 합쳐 Render Tree를 생성한다.

- 실제 화면에 보여지는 노드들로 구성된다.

### 8. Layout 및 Paint

- 정확한 위치값과 크기를 계산한다.
- 계산이 완료되면 화면에 그린다.

### 9. JS 엔진실행 및 JS코드 파싱
