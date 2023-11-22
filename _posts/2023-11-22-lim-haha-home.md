---
title: '임하하 - Home(기존페이지 분석)'
author: channy
categories: [Project, 임하하]
tags: [writing]
pin: true
---
> 임하하 Home 화면 작업 전 실제 침하하 Home 화면의 요소들을 정리해본다.

# 침하하 Home 전체 화면
아래 사진은 침하하 Home 화면이다. 화면이 상/하로 길어 크게 회원가입/로그인 부터 광고영역까지 상단 부분, 아래 게시글 목록 하단 부분으로 정리해본다.
  
<img src="/assets/img/limHaHa/침하하home.png" />
  
# 상단부분
침하하 Home 상단부분에서는 크게 `Header 영역`, `shortcuts 영역`, `최신 업로드 영역`으로 나누고 있다
<img src="/assets/img/limHaHa/home상단.png" />
  
## Header 영역
Header 영역은 최상단에 회원가입과 로그인 중간에 로고 그 아래에는 게시판으로 이동할 수 있는 탭들이 있다.
  
<img src="/assets/img/limHaHa/homeHeader.png" />
  
탭의 경우 hover 할 경우 해당 게시판에 포함되어 있는 상세 게시판들이 보인다. 탭을 클릭을 할 경우 해당 게시판의 전체 게시물 목록 페이지로 가고 상세 게시판을 클릭할 경우 상세 게시판 목록 페이지로 간다.

## Shortcuts 영역
Shortcuts 영역은 사용자가 최근 방문 했던 게시판 목록들을 최대 10개까지 보여준다.
  
<img src="/assets/img/limHaHa/homeShortcuts.png" />

## 최근 업로드 영역
최근 업로드 영역에선 본 채널인 `침투부` 채널과 원본 영상 채널인 `원본 박물관` 채널의 최근 업로드 영상들을 불러오고 재생할 수 있는 영역이다.

<img src="/assets/img/limHaHa/homeRecentUpload.png" />

# 하단 부분
하단 부분은 크게 `타이틀`, `공지`, `게시글 목록`, `페이지네이션`, `검색` 영역으로 이루어져 있다.

<img src="/assets/img/limHaHa/homeList.png" />

# 정리
위 정리한 내용과 실제 [침하하](https://chimhaha.net/) 사이트 마크업을 참고했을 때 아래 처럼 컴포넌트를 구성해보았다. 실제 개발하면서 바뀔 수 도 있지만 우선은 아래 구성으로 개발을 시작해보려고 한다! 그래서 다음 포스팅은 실제 개발에 들어가면서 정리한 내용이 될 거 같다!!
  
```jsx
<Header>
    <TopBar />
    <HeaderTitle />
    <Tabs />
    <RecentVisited />
</Header>
<Main>
    <RecentUploaded />
    <Contents>
        <Notice />
        <Posts />
    </Contents>
    <Pagination />
    <Search />
</Main>
```