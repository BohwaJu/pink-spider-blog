---
title: 'Template'
date: '2021-04-18'
tags: ['css', 'book', 'reflection']
draft: false
author : Rumi
summary: 'The Time Traveller (for so it will be convenient to speak of him) was
expounding a recondite matter to us. His pale grey eyes shone and
twinkled, and his usually pale face was flushed and animated...'
---

# 소제목

_참고자료_: [url](https://www.gutenberg.org/ebooks/35)

### 5. HTML 파일 파싱 및 DOM Tree를 생성한다.

**\* DOM(Document Object Model)은 HTML 문서에 대한 인터페이스이다.**

첫째로 뷰 포트에 무엇을 렌더링 할지 결정하기 위해 사용되며, 둘째로는 페이지의 콘텐츠 및 구조, 그리고 스타일이 자바스크립트 프로그램에 의해 수정되기 위해 사용된다. 항상 유효한 HTML 형식이며, 자바스크립트에 수정될 수 있는 동적 모델이여야 한다. 또한 가상 요소를 포함하지 않으며, 보이지는 않으나 HTML에 존재하는 요소를 포함한다.

## 텍스트 말줄임 (...) 처리

```scss
// 1줄 ... 처리
.ellipsis {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

// 2줄 ... 처리
.ellipsis2 {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  //필요에 따라 line-height를 써야할 수 있다.
}
```