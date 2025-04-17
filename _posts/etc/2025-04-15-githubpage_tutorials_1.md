---
title:  "[Github Pages] Setup Tutorials"
date : 2025-04-15 15:00:00 +0900
last_modified_at : 2025-04-15 15:30:00 +0900
toc: true
toc_sticky: true
header:
categories: 
  - etc
  - Github Pages
tags:
  - Github Pages
excerpt: "github page seup"
use_math: true
classes: wide
---


논문 정리 및 공부한거 정리해서 올려놓으려고 만드는 github page 입니다.

## 1. Install Jekyll

[github-pages docs](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll) 공식 문서를 참고하여 테마를 만들어봅시다.

총 3가지를 설치해야 합니다.

1. Ruby
2. Jekyll
3. Bundler

[Ruby](https://www.ruby-lang.org/en/documentation/installation/)공식 홈페이지를를 참고. 맥에서는 homebrew를 이용하여 설치합니다.

```bash
### Ruby install
brew install ruby
```
설치 후
```bash
which ruby
ruby -v
```
를 통해 ruby 경로를 확인합니다.
만약 결과가 `usr/bin/ruby` (시스템 루비) 등으로 나온다면, 아직 Homebrew 루비를 사용하도록 설정되지 않은 것입니다.

결과가 `/opt/homebrew/opt/ruby/bin/ruby` (apple silicon) 등으로 나온다면, 이미 설정된 것입니다.

`usr/bin/ruby` 경로로 나온다면 아래 명령어를 통해 설정합니다.

```bash
### Add path in .zshrc
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
export PATH="/opt/homebrew/lib/ruby/gems/$(ruby -e 'print RUBY_VERSION.split(".").slice(0,2).join(".")').0/bin:$PATH"
```

이제 설정된 ruby를 통해 bundler, jekyll을 설치합니다.

```bash
### bundler jekyll install 
gem install bundler jekyll
```
설치가 끝났습니다~


## 2. Apply Minimal Mistakes Theme

기본 명령어로 템플릿 프로젝트를 만들기보다는 바로 필요한 테마를 찾아서 적용해봅시다.

- [Jekyll Themes](http://jekyllthemes.org/)
- [Free Jekyll themes](https://jekyllthemes.io/free)

등등 검색해보면 쉽게 찾을 수 있을겁니다.

- [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/)
- [chirpy](https://github.com/cotes2020/jekyll-theme-chirpy/)

를 많이 사용한다고 하는군요. 저는 minimal mistakes 적용하였습니다

먼저 [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) 를 git clone 혹은 zip으로 다운받습니다.

![theme download](/assets/img/github_pages/250415_githubpage_1/0.png)

폴더 명을 `@githhubID.github.io` 로 변경합니다.

이때 전부 사용하느 것이 아니라, 아래의 것들은 지웁니다.

```bash
- .github
- test
- .editorconfig
- .gitattributes
- .travis.yml
- CHANGELOG.md
- README.md
- screenshot.png
- screenshot-layout.png
```

docs는 따로 남겨두셨다가, 포스팅 양식 등을 확인할 수 있는 내용입니다.
docs 내부의 _pages 폴더는 추후 상단의 카테고리를 선택할 수 있는 양식이라, 최상단으로 이동해두었습니다.

README.md 는 바로 수정하시거나, 삭제 후 이후 과정에서 만드셔도 됩니다.

## 3. Create a new repository and push

![저장소 생성](/assets/img/github_pages/250415_githubpage_1/1.png)

`@githhubID.github.io` 로 새 repository 생성합니다.
이렇게 작성하면 따로 설정할 필요 없이 자동으로 github pages로 설정됩니다.

다른 이름으로 생성시 가능은 하지만, 나중에 바꿔야하는 등 귀찮아지니 그냥 본인 id로 만듭시다.


앞선 과정에서 README.md를 수정하지 않고 지웠다면, Add a README file도 체크해줍시다.

이후에 local에서 만든 folder를 연동합니다.
```bash
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/github_id/github_id.github.io.git
git push -u origin main
```


## 4. Set Page

깃허브 저장소에서 Setting - Page 로 들어가서 설정을 해주고, `Github-pages`로 보여줄 `branch`를 선택.

![page setting](/assets/img/github_pages/250415_githubpage_1/2.png)

저는 그냥 master로 했습니다.

## 5. Check Web Page

주소창에 생성한 `@my_github_id.github.io`로 접속해보면 기본으로 적혀있는 tutorial 페이지가 보여집니다.

![page preview](/assets/img/github_pages/250415_githubpage_1/3.png)

만약 바로 안나온다면 페이지 생성까지 최대 10분 정도의 시간이 필요할 수 있으니 조금만 기다려보세요

## 6. Customization

기본적으로 `_config.yml` 파일을 수정합시다.

[eona1301 님의 블로그](https://velog.io/@eona1301/Github-Blog-Jekyll-minimal-mistakes) 와 [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) 를 참고하여 수정하였습니다.