Evernote SASS Structure Boilerplate
=============

[![npm version](https://badge.fury.io/js/evernote-sass.svg)](http://badge.fury.io/js/evernote-sass)

※ 의역 오역 많음, 원문 꼭 읽어볼 것([원문](README-eng.md))

[SMACSS](http://smacss.com/) 책을 읽고 매우 도움이 된다고 생각해서 에버노트의 프런트 엔드 팀은 몇가지 방법을 Sass build에 사용했다.
Sass 파일을 디렉토리(Base, Layout, Modules 및 Views)로 나누면 프로젝트 파일을 구성하고, css를 깨끗하고 논리적인 파일로 컴파일 하는데 도움이 된다.
각 페이지에는 특정 페이지를 작성하는 데 필요한 Base, Layout, Modules 및 Views에서 개별 모듈러 컴포넌트를 가져오는 프로젝트 파일로 작동하는 Sass (.scss)파일이 생성된다.

이 빌드 방법론은 현재 [Evernote.com](https://evernote.com) 에서 사용되고 있다.

## Install (설치)

```js
npm install evernote-sass -g
```

## Use (사용)

Evernote Sass 빌드를 사용하려는 디렉토리에 ```evernotesass```를 실행.

새로 개별적인 Sass 파일을 만드려면 ```evernotesass-page name=filename path=Path-To-Sass-directory```를 실행.
이름이 설정되어 있지 않으면 파일의 이름은 'page'이고 만약 경로가 설정되지 않은 경우 디렉토리는 'sass'로 간주된다.

새로운 Sass 모듈을 만드려면 ```evernotesass-module name=filename path=Path-To-Sass-Modules-directory``` 실행.
이름을 설정하지 않으면 파일의 이름은 'module'로 지정되고 경로가 설정되지 않으면 디렉토리는 'sass/modules'로 간주된다.

SASS Directories
----------

1.  Base

  Base 디렉토리에는 프로젝트를 시작하는 데 도움이 되는 스타일이 있다. 기본 디렉토리에는 다음 유형의 Sass파일이 포함될 수 있다.:
  * Vendor dependancies (Compass, Foundation)
  * Authored dependancies (Mixins, variables, Extends)
  * Fonts
  * Reset

2.  Layout

  Layout 디렉토리는 페이지의 큰 컨테이너인 스타일을 포함한다. 이 디렉토리는 다음과 같은 Sass 파일이 포함될 수 있다.:
  * Responsive Grid
  * Page specific layouts

3.  Modules

  Modules 디렉토리에는 많은 Sass파일이 들어있을 것이다. 페이지는 여러 모듈로 구성 될 수 있으며 개별적으로 스타일을 지정해야한다. 이 모듈에는 다음과 같은 Sass 파일이 포함될 수 있다.:
  * Header
  * Footer
  * Navigation
  * Content Block

4.  Views

  Views 디렉토리에는 페이지가 일반 레이아웃 또는 모듈에서 변경해야하는 특정 스타일이 포함되어 있다. 예를 들어 웹 사이트의 헤더가 웹 사이트나 어플리케이션에서 녹색이더라도 views 파일이 들어오는 특정 페이지에서는 파란색 배경으로 바꿀 수 있다.

## 미사용 Sass 모듈 분리(삭제)

Evernote의 Sass 구조로 빌드에서 많은 Sass 파일을 사용한다. 때로는 더 이상 사용되지 않기 때문에, 미사용 Sass 모듈을 자동으로 제거하는 [Sassyclean](https://github.com/ryanburgess/grunt-sassyclean)이라는 Grunt 작업을 사용하기 시작했다.

## Rules (규칙)
  - 페이지 당 최대 2 개의 CSS 파일 만 있어야합니다 (이렇게하면 HTTP 요청이 방지됩니다)
  - 각 선택자는 규칙을 위한 한줄
  - 관련항목을 함께 나열하시오
  - 중첩은 3단계 까지만
  - 파일을 작은 모듈로 나눈다.(100줄보다 큰 scss 파일을 사용하지 않는다)
  - 사이트에서 ID사용은 지양한다. 상위 요소에 ID를 사용한다 (예: Header, Footer, Main, ), !important를 사용하는 클래스 사용은 지양한다.
  - 주석을 달 것
  - a ```:hover``` 가상 클래스의 스타일이 지정된 경우, ```:focus```도 접근성을 위해 스타일을 지정해야한다.

## Commenting (주석)
  - Sass 파일에서 주석에 "//"을 사용하면 컴파일 된 css에 출력되지 않는다.


## Variables (변수)
  - Sass build 전반에 일반적으로 사용되는 값(글꼴, 컬러, 백분율, z-index)는 변수로 설정해야 한다.
  - 모든 색상은 변수여야한다.


## Order of imports (import 순서)
  - Vendor dependancies (compass)
  - Authored dependancies (Mixins, variables)
  - Base styles ( reset, fonts, typography )
  - Layout styles
  - Modules styles
  - Views styles

## Release History
* 1.2.7: Remove Grunt dependencies.
* 1.2.6: Update documentation.
* 1.2.5: Rename themes directory to views.
* 1.2.4: Add date created to module generator script.
* 1.2.3: Update formatting on default page.scss.
* 1.2.2: Fixed typos [pull #12](https://github.com/evernote/sass-build-structure/pull/12).
* 1.2.1: Update error messages.
* 1.2.0: Updates to page generator script and documentation.
* 1.1.9: Updates to module generator script.
* 1.1.8: Update package.
* 1.1.7: Add Sass module generator script.
* 1.1.6: Change comment dashes to 60.
* 1.1.5: Move mixins into separate modules.
* 1.1.4: Small updates to build script.
* 1.1.3: Added [pull #10](https://github.com/evernote/sass-build-structure/pull/10) add missing "grunt-newer" package.
* 1.1.2: Added [pull #9](https://github.com/evernote/sass-build-structure/pull/9) update grid.
* 1.1.1: Added [pull #8](https://github.com/evernote/sass-build-structure/pull/8) clean up type.
* 1.1.0: Added [pull #7](https://github.com/evernote/sass-build-structure/pull/7) clean up coding style.
* 1.0.9: Added [pull #6](https://github.com/evernote/sass-build-structure/pull/6) missing margin auto mixin.
* 1.0.8: Added [pull #5](https://github.com/evernote/sass-build-structure/pull/6) JSCS support based on google preset.
* 1.0.7: Added [pull #4](https://github.com/evernote/sass-build-structure/pull/4) editorconfig support.
* 1.0.6: Update documentation for individual Sass file.
* 1.0.5: Ability to create new individual Sass file.
* 1.0.4: Set default HTML font size to 62.5% and change REM mixin calculation.
* 1.0.3: Update documentation
* 1.0.2: Remove old shell script
* 1.0.1: Update generator script
* 1.0.0: Add evernotesass generator script
* 0.1.3: Added grunt package with Sass, Watch and Sassyclean.
* 0.1.0: Initial release.

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
