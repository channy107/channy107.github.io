---
title: '임하하 - 폴더 구조 및 path 정리'
author: channy
categories: [Project, 임하하]
tags: [writing]
pin: true
---
> 임하하 프로젝트의 폴더 구조 및 path 정리를 정리한다.
  
# 구현 화면
아직은 볼품 없지만 나름 비슷해져가고 있다 ㅎㅎ
<img src="/assets/img/limHaHa/임하하움짤.gif" />
  
<img src="/assets/img/limHaHa/침하하움짤.gif" />

# 폴더 구조 및 path 정리
## app 하위 폴더 구조
next app router 에서는 파일 시스템 기반으로 라우팅을 구현하기 때문에 app 하위의 디렉토리가 곧 라우팅 될 페이지라고 볼 수 있다. 또한 `[디렉토리 이름]`와 같이 디렉토리 이름을 통해 다이나믹 라우팅 등의 기능을 지원하기도 하기 때문에 아래 폴더 구조에서 각각의 폴더가 어떤 역할을 하는 지 적어 보려고 한다.
```
├── [boardname]
│   ├── [board]
│   └── page.tsx
├── _api
│   ├── getBoardMenus.ts
│   └── types.ts
├── _component
│   ├── Content
│   ├── Header
│   ├── HeaderTitle
│   ├── MSWComponent.tsx
│   ├── RQProvider.tsx
│   ├── RecentVisited
│   ├── SubMenus
│   ├── Tabs
│   └── TopBar
├── _remotes
│   └── useGetBoards.ts
├── best
│   ├── [board]
│   └── page.tsx
├── boards
│   └── page.tsx
├── favicon.ico
├── globals.css
├── join
│   └── page.tsx
├── layout.tsx
├── login
│   └── page.tsx
├── new
│   ├── [board]
│   └── page.tsx
├── not-found.tsx
├── page.module.css
└── page.tsx
```
  
## login, new 과 같이 일반적인 폴더 이름
일반적인 폴더는 각각 라우팅 되는 path 라고 볼 수 있다.
  
예를 들어
* login -> `http://example.com/login`
* new -> `http://example.com/new`
  
## [boardname]
위에서 살짝 언급했듯이 `[폴더이름]`과 같은 폴더명은 다이나믹 라우팅을 의미한다. 예를 들어 `http://example.com/게시판1`, `http://example.com/게시판2`, 와 같이 `/` 뒤에 오는 path를 자동으로 해당 폴더에 있는 page로 매칭을 시켜준다.
  
**다만 같은 레벨에서 static 한 디렉토리 명이 있을 경우 해당 라우팅이 우선된다.** 예를 들어 아래 구조에서 `best` 는 static 한 path 이므로 `http://example.com/best`로 접근 시 best 하위에 있는 page를 보여주게 된다.
```
├── [boardname]
│   ├── [board]
│   │   └── page.tsx
│   └── page.tsx
├── best
│   ├── [board]
│   └── page.tsx
```

## _api, _component, _remotes
해당 폴더들 처럼 `_folder` 형태의 경우 private 폴더로 라우팅에 관여하지 않고 내부에서 쓰는 폴더라고 볼 수 있다.
  
```
├── _api
│   ├── getBoardMenus.ts
│   └── types.ts
├── _component
│   ├── Content
│   ├── Header
│   ├── HeaderTitle
│   ├── MSWComponent.tsx
│   ├── RQProvider.tsx
│   ├── RecentVisited
│   ├── SubMenus
│   ├── Tabs
│   └── TopBar
```
  
`_api` 는 api를 호출 하는 코드와 호출에 필요한 request, response 타입을 모아놓은 폴더이다.
  
`_component` 는 해당 계층의 page에서 사용되는 component 들을 모아 놓은 폴더 이다. 각 컴포넌트 들은 `컴포넌트.tsx`, `컴포넌트.module.css`, `index.ts`로 구성하여 파일이 아닌 폴더로 묶어 관리한다.
  
`_remotes` 는 react-query 를 래핑하는 hook 들을 모아놓은 폴더이다.


  
**그 외에도 폴더 이름에 다양한 기능들을 지원하는 데 [이 곳](https://nextjs.org/docs/getting-started/project-structure)을 참고.** 

# 마치며
잇따른 구직활동으로 프로젝트 세팅을 끝내고 이제서야 본격적으로 개발에 들어갔다. 많이 하지는 못했지만 `Header` 부분의 `Tabs` 까지 만들면서 Next JS 가 단순 서버사이드렌더링 만을 위한 도구가 아니라 라우팅 등 다양한 기능들을 지원하는 프레임 워크임을 실감할 수 있었다. 이 전에 개발할 때는 어떻게 폴더 구조를 잡을 지, 페이지가 추가될 때마다 라우팅 관련 내용도 함께 추가하고 그랬었는데 Next를 사용하니 그런 것에 대한 고민을 덜 수 있어서 좋았던 거 같다. 그리고 app router 에서는 `use client`를 통해 client 컴포넌트도 지원하니 적재적소에 필요한 방식을 고를 수 있겠구나 라는 생각도 들었다. 그리고 `Tabs` 부분까지 구현하면서  `폴더 구조 및 path 정리`, `react-query 적용`, `msw 사용` 등등 앞으로 개발에 필요한 도구들을 한번씩 사용한 거 같아 이 각각에 대해서도 한번 정리하고자 한다. 이번 포스팅에선 `폴더 구조 및 path 정리`을 정리하였고, 다음 포스팅에선 `react-query 적용`에 대해 정리를 해보겠다!!!