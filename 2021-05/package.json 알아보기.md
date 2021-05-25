# Package.json의 모든것

## Package.json
### 1. 정의

`package.json`은 각종 npm 패키지들에 대한 정보 및 의존하고 있는 버전, 프로젝트의 정보를 명시하고 있는 파일이다.

때문에 해당 프로젝트 파일의 root 디렉토리에 위치한다.

작성되는 정보는 2가지 파트로 나눌 수 있다.

1. 프로젝트의 정보 - name, version 영역
2. 패키지 정보 - dependencies, devDependencies

### 2. 프로젝트 정보

`package.json` 파일은 반드시 name과 version 항목을 포함해야한다.

- name : 소문자인 한 단어로 작성해야한다. (대문자 X)
- version : 0.0.0 형식을 따른다. 이러한 작성 규칙을 `시맨틱 버저닝`이라고 부른다.

### 3. 패키지 정보

#### Do I need to know the contents of the library at compile time?

패키지 정보는 dependencies 또는 devDependencies 로 나눠진다.

- dependencies : **프로덕션 환경** 에 필요한 패키지
- devDependencies : **로컬 개발 및 테스트** 에 필요한 패키지

즉, devDependencies는 개발 , 컴파일 (빌드) 시 필요한 라이브러리(테스트 도구, 웹팩, 바벨 등)들을 보관하고
dependencies는 런타임에도 계속 사용되면서 기술 스펙으로 사용될 라이브러리(어플리케이션에 필요한 라이브러리들)들을 보관한다.

#### 두가지를 나눠야하는 이유!
devDependencies 항목을 나누지 않을 경우 publishing 과정에서 빌드해야되는 패키지들이 불필요하게 많아지기 때문에 빌드 과정의 소요시간이 길어진다. dependencies 항목은 runtime과정에 포함되기 때문에 나누는 것이 좋다.

---

## Package & Module

### 1. 패키지
패키지는 package.json 으로 설명되는 파일 또는 디렉토리를 뜻한다.
각각의 프로젝트들은 npm 레지스트리에 공개되기 위해 반드시 package.json 파일을 가지고 있어야한다.

### 2. 모듈
모듈은 require(), import 등으로 로드될 수 있는 node_modules 디렉토리안의 파일 또는 디렉토리이다.

> 주의: 모듈은 package.json 파일을 가질 필요가 없다. 모든 모듈들이 패키지는 아니다. package.json을 가진 모듈만이 패키지이다.

모듈이 패키지 보다 조금 더 큰 개념이라고 이해할 수 있다.

### 3. 패키지 지정하기
패키지를 지정하기 위해서는 패키지의 package.json 파일의 "dependencies" 또는 "devDependencies" 에 패키지를 명시해야한다.

만약 npm install 을 실행하면, npm 은 package.json에 나열된 각각의 시맨틱 버전 요구 사항을 충족하는 dependencies" 와 "devDependencies"를 다운받는다.

"dependencies": 프로덕션 환경에서 응용 프로그램에 필요한 패키지.
"devDependencies": 로컬 개발 및 테스트에만 필요한 패키지.

### 4. 시맨틱 버저닝
버전은 . dot을 기준으로 3영역 Major, minor, patch 로 구분됩니다.

시맨틱 버저닝 에 따라 버전을 작성하고, 그 규칙은 다음과 같습니다.

참고로 2020.05.11 Vue.js의 버전은 2.6.11입니다. 2020년 이내에 vue 3가 나온다는 의미는 제일 앞의 숫자가 3, 가운데와 마지막 숫자가 0이 되는 메이저 업데이트를 의미합니다.

5. 틸드(~) 와 캐럿(^)
패키지의 버전에는 ^ 와 ~ 이 적혀있습니다. ~는 틸드(tilde), ^는 캐럿(caret)이라고 읽습니다.

틸드와 캐럿의 사용에는 시맨틱 버저닝 규칙이 사용됩니다.

1) 틸드(~)
해당 패키지의 패치 레벨 변경을 허용하겠다는 의미입니다.

~4.3.0 은 >= 4.3.0 이상, < 4.4.0 미만 과 같은 의미입니다.

즉, 4.4.0 미만의 패치 레벨 변경을 허용하겠다는 의미입니다.

"devDependencies": {
  "@vue/cli-service": "~4.3.0",
},
2) 캐럿(^)
해당 패캐지의 마이너, 패치 변경을 허용하겠다는 의미입니다.

~2.6.11 은 >= 2.6.11 이상, < 3.0.0 미만 과 같은 의미입니다.

즉, 3.0.0 미만의 마이너, 패치 변경을 허용하겠다는 의미입니다.

"dependencies": {
  "vue": "^2.6.11"
}


다시 돌아와서 package-lock.json이란?
자, 서론이 길었는데요! 이제 package-lock.json이란 무엇인지 적어보겠습니다.
우리가 npm install 명령을 실행할 시, package.json(= Input)을 통해 node_modules 폴더(트리 = Output)를 생성하게 됩니다.
package.json에 명시된 의존성 패키지들을 폴더 안에 설치하며, 생성된 node_modules 폴더의 정보를 package-lock.json 안에 담습니다.

이상적인 npm install은 동일한 package.json에 동일한 node_modules가 작성되는 것인데 크게
현재 사용하고 있는 npm의 버전이 다른 경우
의존성을 가진 패키지의 버전이 업데이트 됐을 경우
의존성을 가진 패키지가 의존하는 패키지의 버전이 업데이트 됐을 경우
다음과 같은 이유들로 실현되지 못하는 경우가 많습니다.


https://pewww.tistory.com/11
https://c17an.netlify.app/blog/node.js/npm-install-%EC%A0%95%EB%A6%AC/article/