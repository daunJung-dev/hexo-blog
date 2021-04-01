---
title: hexo로 블로그 만들었으니 github에 배포하기
date: 2021-03-31 23:49:38
tags: hexo github 배포 deploy
---

hexo로 블로그를 어제 로컬에서 띄우는걸 성공했다!

그러나 실제로 올리기까지 해야 성공했다고 말할 수 있으니, 이제 배포하는 방법을 포스팅 해보자.

# Hexo는 두개의 Repository가 필요하다.

[hexo][hexo_link]는 두개의 repository를 필요로 한다.
static 으로 생성된 페이지가 저장되어있는 repository와 외부에서 접속할 수 있게끔 deploy 되어진 `[사용자이름].github.io` 라는 명칭의 repository 가 필요하다.
따라서 먼저 두개의 repository 를 만들어준다.

> [사용자이름].github.io

> hexo-blog

# 초기 세팅

`npm`을 이용하여 전역으로 hexo를 설치해주자.

```terminal
npm install hexo-cli -g
```

아까 만든 repository 중 `hexo-blog`를 로컬 컴퓨터로 클론하여
아래와 같이 초기 패키지를 설치해주자.

```terminal
hexo init ./
npm install
```

설치 후에 터미널에서

```terminal
hexo server
```

명령어를 실행해주면 [localhost:4000][local_server]에 나만의 블로그가 개설이 되는것을 확인할 수 있다.

## 깃허브 페이지에 배포하기

아까 만들어둔 repository에서 배포를 하기 위해서는 `_config.yml`파일을 수정해주어야 한다. 파일을 열어 `deploy`부분을 찾아주면 아래와 같이 타입이 비어있다.

```yml
deploy:
  type: ""
```

이 부분을 다음과 같이 수정하여주자.

```yml
deploy:
  type: "git"
  repo: "https://github.com/[사용자이름]/[사용자이름].github.io.git"
  branch: "master"
```

## 배포 플러그인 설치

깃허브 페이지를 배포하기 위해선 `hexo-deployer-git` 플러그인을 설치해줘야 한다. 아래 명령어를 통해 설치해주자.

```terminal
npm install --save hexo-deployer-git
```

## 정적 리소스 생성하기

배포를 하기 전 정적리소스를 생성해주고 배포를 한다.

```terminal
hexo generate
```

## 배포하기

이제 끝났다. 아래 명령어만 실행해주자.

```terminal
hexo deploy
```

`https://[사용자이름].github.io`로 접속이 잘 되는걸 확인해보자.

글을 추가후 배포를 했거나 했을때 혹 업데이트가 되지 않는다면 캐쉬의 문제일 가능성이 있다. 그런 경우에는

```terminal
hexo clean
```

을 사용해서 캐시를 초기화해주면 되겠다.

## 마무리

여기까지 정말 간략하게 hexo로 블로그 만든 후 배포하는 과정을 기록해봤는데, 일단 블로그는 만드는것보단 얼마나 글을 잘남기느냐가 중요한거 같다. 이제 곧 회사가 이사를 가게 되어 뭔가 마음이 기대감에 차있다. 좋은 기대감과 함께 블로그도 잘 작성해봐야지. :)

[hexo_link]: https://hexo.io
[local_server]: http://localhost:4000
