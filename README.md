## [T아카데미] 토크ON 세미나 Javascript 디버깅 및 테스트 방법

#### http://bit.ly/t-js-debug> <- 여기로 접속하여 준비하자.



#### 디버깅이란 ?

디버그, 디버깅은 컴퓨터 프로그램의 정확성이나 논리적인 오류를 찾아내는 테스트 과정을 뜻한다.

#### 개발 플로우

문제정의 - 분석- 개발 - 코딩 - 디버깅 - 유지보수

#### 디버깅 도구

크롬 개발자도구, Visual Studio Code, Debugger for chrome 플러그인, End- to-End 프레임 워크, Saucelabs 등

#### 디버깅하기 쉬운 코드 작성

분명하고 확실하게 작성하자. 

즉 이해하기 쉬운 코드를 작성합니다. 변수명은 의미있는 이름으로, 전역변수 X - 모듈화 / Class 

함수는 한가지일을 잘하는 것으로 작성하자.



### 1. 크롬 개발자 도구 실습하기

먼저 form-sample 폴더에서 시작하자.

```
$ npm install
$ npm start
```

localhost:8080에 접속하자 !

이후 크롬 개발자 도구를 열자. ctrl + shift + j 

![1.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/1.PNG?raw=true)

Submit 버튼에 break 포인트를 걸어보자.

![2.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/2.PNG?raw=true)

현재 이름과 내용의 위치가 바껴서 결과물이 출력되고 있다 ! 이걸 디버깅을 통해 수정하자 !

#### 하지만 크롬개발자 도구에서 수정하고 새로고침을 누르면 수정한 코드가 적용되지 않는다 ! 그럼 어떻게 해야될까?

크롬 개발자도구 Sources 탭에서 Filesystem Add floder를 클릭하여 프로젝트를 올리자 !

![3.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/3.PNG?raw=true)

이후 코드를 수정하게 되면 !

![4.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/4.PNG?raw=true)

새로고침을 해도 수정한 코드가 적용이 된다 !

### 2. 크롬 개발자 도구 살펴보기

#### Elements 

- 모든 DOM 트리를 보여준다.
- CSS 스타일과 리스너, 속성등을 보여준다.
- 바로 수정하고 실시간으로 확인 가능

![5.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/5.PNG?raw=true)

#### Console

- 로그를 보여줌
- 코드를 실시간으로 입력할 수 있다.

![6.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/6.PNG?raw=true)

monitor 사용하기

![6-2.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/6-2.PNG?raw=true)

#### Sources 

- 디버깅, 브레이크포인트와 관련된 작업
- 워크스페이스 설정
- 스니펫을 작성하고 사용

![7.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/7.PNG?raw=true)

에러가 난 부분에서 바로 코드 수정하는 방법

Puse on exception 클릭

![7-1.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/7-1.PNG?raw=true)

블랙 박스로 불 필요한 벤더 제외하기

![7-2.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/7-2.PNG?raw=true)

XHR breakpoint 사용하기

이것은 ajax 사용 시 브레이크 포인트가 걸리는 부분이다.

![7-3.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/7-3.PNG?raw=true)

#### Snippets

자주 사용하는 스크립트를 스니펫에 저장하여 간편하게 사용할 수 있다.

#### Network

- 네트워크 분석

![8.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/8.PNG?raw=true)

Capture screenshots 사용하기

![8-2.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/8-2.PNG?raw=true)

#### Performance

- 퍼포먼스 분석

https://googlechrome.github.io/devtools-samples/jank/ 접속

![9.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/9.PNG?raw=true)

#### Memory

- 메모리 분석

![10.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/10.PNG?raw=true)

### 2. Visual Studio Code

debugger for chrome 설치하자 !

![11.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/11.PNG?raw=true)

브라우저에서 로드하는 파일과 실제 소스 파일이 다른 경우는 어떻게 해야되나요 ?

- webpack과 같은 번들러는 새로운 js 파일을 생성.

react-app-sample을 실행하자 !

![12.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/12.PNG?raw=true)

#### 크롬 연동하기

launch.json 추가하기

디버깅 셋팅하기

![13.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/13.PNG?raw=true)

크롬과 비슷한 디버깅 환경이 보인다.

![13-2.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/13-2.PNG?raw=true)



#### NodeJS도 디버깅이 되나요?

launch.json 추가하기

디버깅 셋팅하기

![14.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/14.PNG?raw=true)

#### 동작은 하는데 좋은 코드일까?

같은 팀 / 같은 동료는 같은 스타일로 작성하는 것이 효과적입니다.

코드 스타일을 가이드해주는 도구입니다.

- JSLint, JSHint, ESLint, TSLint 등등

#### ESLint 설치하기

![15.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/15.PNG?raw=true)

코드 수정하기

![16.PNG](https://github.com/Sung-hee/Javascript-debugger/blob/master/image/16.PNG?raw=true)



### 3. E2E Test

nightwatch.js 테스트를 도와주는 친구

```javascript
// Demo test

module.exports = {
  'Demo test Google' : function (client) {
    client
      .url('http://www.google.com')
      .waitForElementVisible('body', 1000)
      .assert.title('Google')
      .assert.visible('input[type=text]')
      .setValue('input[type=text]', 'rembrandt van rijn')
      .waitForElementVisible('button[name=btnG]', 1000)
      .click('button[name=btnG]')
      .pause(1000)
      .assert.containsText('ol#rso li:first-child',
        'Rembrandt - Wikipedia')
      .end();
  }
};
```

Run local Test

```
$ npm run selenium
$ npm run e2e-test
```

#### 원격 테스트하기

https://saucelabs.com/ 회원가입하기 







