BACKEND
#1-4. Creating a Virtual Environment
mkdir bsdir2
cd bsdir2
pipenv —three
pipenv shell
pipenv install django
pipenv install requests 
> Pipfile                   가상환경에서 추가되는 패키지 자동으로 입력되는 파일
[packages] 
requests = “*” 	추가되는거 확인
django-admin 명령어 실행되는거 확인

#1-6. Creating our Django Project
django-admin startproject 로 프로젝트를 시작해도 되지만
pipenv install cookiecutter
cookiecutter https://github.com/pydanny/cookiecutter-django
프로젝트 정보 입력 ( 정보 순서와 버전은 조금씩 달라짐 )
timezone [UTC]: Asia/Seoul  데이터베이스랑 연결할때 내용이 다르면 오류가 남
불필요한 파일 삭제
README.md 파일 생성

#1-7. Creating the GitHub Repository
저장소 생성 및  연결
git init
git remote add origin {YOUR_GIHTUB_URL}
git pull origin master
git add .
git commit -m "First commmit"
git push origin master

#1-8. Installing the requirements
pipenv --three
pipenv shell
pipenv install -r requirements/local.txt

In case of an error try this:
pip install -U setuptools
pip install -U pip
pipenv install -r requirements/local.txt

 #1-11. Creating the Databases
CREATE DATABASE nomadgram;

 #1-12. Creating the Apps
django-admin startapp images

#1-18. Creating a super user
python manage.py createsuperuser




@@@@@ 혼돈의 버그 픽싱



#1-70 Setting up JWT
pipenv install djangorestframework-jwt
postman 테스트
localhost:8000/api-token-auth > body에 username: password 입력해서 token값을 받아옴
localhost:8000/users/bill > header에 value: JWT 토큰값 붙여넣기 > 가입 정보가 나옴 

#1-72 Signing Up : Logging In
pipenv install django-rest-auth
facebook 로그인 을 위한 패키지 부분이라서 설치만 하고 적용 안함

prontend
** webpack으로 설정하면 오래 결려서 creat react app을 사용한다
Create React App V2 릴리즈! 10분만에 설명해준다. (Create React App V2.0 Explained in 10 min)
https://youtu.be/w9Zf0hpohQM

install
npx create-react-app crav2

sass 사용하게 설정
crv2>src>App.scss 파일명 변경
crv2>src>App.js import app.scss로 변경 이름도 변경 
yarn add node-sass

module css 사용하게 설정
** class의 이름을 랜덤하게 바꿔줘서 class 명을 추적 안해도 되게 해줌
crv2>src> App.module.scss 파일명 변경
crv2>src>App.js  import styles from './App.module.scss';로 변경
yarn add node-sass
App.module.scss 파일 변경
+ class명 첫 글자 소문자로 변경하고 '-' 삭제 

react fragment syntax 적용
뭔지 모르겠고 당장 안필요 할것 같아서 설정안함

#2-4 Using Create React App
에서 부터 다시 보변서 적용

#2-5 Ejecting from Create React App
yarn eject
webpack을 좀더 커스터 마이징 하기 위한 eject 
package.json에 디펜던시가 추가되는것을 확인


#2-6 Ejection aftermath
eject 이후 2개의 폴더 자동 생성 config, scripts
불필요한 파일 삭제 jest폴더, script>test.js
package.json jest 부분 삭제 0:40초 부분

webpack.config.dev.js
웹사이트 개발시 마다 실행

webpack.config.prod.js
live 웹사이트를 위한 파일

#2-7 Intro to SCSS and Adding SCSS to Webpack
니콜라스 헬프미 ~ ㅎ
Create React App V2
https://youtu.be/w9Zf0hpohQM 

요 동영상 보고 sass, css module 을 적용했는데요 

#2-8
#2-9 

스킵하고 
#2-10 Serving Webpack Bundles with Django
로 넘어가도 문제 없을까요? 

#2-7 Intro to SCSS and Adding SCSS to Webpack 
내용 진행에 대한 댓글남김
2:56초 
webpack.config.dev.js 
파일 수정하는 부분이 당최 이해가 안되고 실제 제가 설치한 파일하고는 모양이 많이 달라서요

webpack 홈페이지에서 참고할 내용이 있을까요? 
https://webpack.js.org/concepts/

문서를 봐도 여전히 잘 모르겠어요
혹시 참고할만한 내용 링크를 주실수 있으면 부탁드려요 

니콜라스 강좌 잘보고 있어요 ~ 짱짱 !!

#2-10 Serving Webpack Bundles with Django
yarn build > fronted 폴더안에 build 폴더가 생성되는 것을 확인
fronted> package.json 수정  "proxy": "http://localhost:8000" 800포트 추가 

:8000 Django 
:3000 React 

리액트앱 (3000)에서 장고 서버로 요청이 오면 자동으로 막아버림 
8000포트 자신에게 오는 것만 허용함
이것을 막지 않게 하기 위해서 설치하는 프로그램

가상환경에설치: pipenv install django-cors-headers
장고에설치: config>base.py Third party apps 항목에 'corsheaders', # To accept requests from React (3000port) 추가

미들웨어 추가
** 장고가 요청을 처리하는 방법
base.py 에 middleware항목에 'corsheaders.middleware.CorsMiddleware', 추가

장고가 번들을 static file로 로딩하게 해야함
base.py 수정 : STATICFILES_DIRS 항목에 str(ROOT.DIR.path('frontend','build','static')) 추가
9:23초

Nomadgram 폴더의 전체  view.py 생성
nomadgram> view.py catch-all-URL설정: request가 url을 매칭하지 못했을때 이동하는곳
path("", include("allauth.urls")), > 오류 생길수도 있는 부분

리덕스 들어가기전 미니 강좌 
리액트, 리덕스로 타이머 앱 만들기 : #6 Installing Redux and React Redux
리덕스 설치
npm install redux react-redux

package-lock.json 파일에 설치 확인

리액트, 리덕스로 타이머 앱 만들기 : #7 Intro to Redux
리덕스 이론 볼 차례

리액트, 리덕스로 타이머 앱 만들기 : #9 Practicing Javascript Switch
볼차례
미니 프로젝트 다봄

#3-0 Creating the User Reducer
** 여러개의 리덕스 만들 뼈대 생성
logo 삭제
파일&폴더생성:redux>modules>users.js 
리덕스 파일 작성 순서 제작 
// imports
// actions
// action creators
// intitial state
// reducer
// reducer functions
// exports
// reducer export
파일 작성
#3-1 Installing Redux in Our Project
redux 설치
fronted 폴더에서 
yarn add redux react-redux

#3-2 Setting Up the Redux Store with Multiple Reducers
*여러개의 리듀서를 합칠 수 있는 스토어 만들기
파일생성: redux> configureStore.js ( 나의 스토어를 설정/ 구성)

#3-3 Connecting the Reducer with the React App
Failed to compile
./src/index.js
Module not found: Can't resolve 'redux/configureStore' in '/Users/bill/Desktop/bsdir2/nomadgram/frontend/src'
This error occurred during the build time and cannot be dismissed.

발생
>> 다음편 비디오에 해결책 나옴

#3-4 Changing the NODE_PATH
fronted>.env 파일 생성
NODE_PATH=src 입력하기
** 모듈 형식으로 불러 오도록 하는 설정

fronted>src index.js, app.js configureStore.js 의 상대경로 변경 ../ 를 삭제 

 #3-5 Redux Middlewares Thunk
 미들웨어 작성
fronted 폴더에서 미들웨어 설치
yarn add redux-thunk
미들웨어 : 엑션을 보낼때까지 기다려서 보내는것

...middlewares 
...는 array 를 unpack 한다는 의미 
configureStore.js 파일 수정

#3-6 Redux Middlewares- Logger
fronted 폴더에서 yarn add redux-logger --dev
--dev 옵션을 넣고 package.json 에서 확인나면 development에만 적용이 됨을 확인 가능

configureStore.js: 미들웨어를 넣기 위한 파일

configureStore.js 파일 수정
https://github.com/nomadcoders/nomadgram/commit/2a95b65ae7e83feeb084d21b43cf12fead364868

#3-7 Contact List App- Creating the Project and Cleaning Up
cd Documents 폴더에 라우터 생성
create-react-app react-router-contact-List
불필요한 파일 정리
https://github.com/nomadcoders/react-router-contact-list/commit/77d42619e06956bebeb1752a2958d69d4076c35a


#3-8 Contact List App- Creating the Router and the Header
** 실제출력되는 화면 만들기
react router 설치
yarn add react-router-dom

#3-9 Contact List App- Created Home page + Contacts
app.js index.js 수정하여 2개의 페이지 만듬
https://github.com/nomadcoders/react-router-contact-list/tree/de3d5fa82aeaf41562da4b913dfecd0359446dc4

#3-10 Contact List App- Contacts Routes and Contact Detail
url 에서 정보를 불러와서 다른 내용을 보여주는 코딩 
한번 다시 보고 적용하기
match를 이용해서 router 생성 
약간 어려움

#3-11 Syncing React Router with Redux
** 리액트 라우터가 리듀서와 함께 작동하게 하는것을 목표 
설치
yarn add react-router-dom react-router-redux history
configureStore.js 수정
index.js 수정

오류 발생
해결
여기 ConnectedRouter쓰시고 에러나시는분들
yarn remove react-router-redux하신다음에 yarn add react-router-redux@next로 5버전 받으셔야 에러 안납니다

#3-12 Debugging Redux like a Pro with Reactotron
yarn add reactotron-react-js

src>ReactotronConfig.js 파일 생성 및 입력 

install reactotron
brew update
Then simply type:

brew cask install reactotron
To update an existing installation of reactotron via brew, type:

brew cask reinstall reactotron
After a successful brew cask install, you can find the app in your Applications folder. Run it like any other application. 

reactotroncongif.js index.js 수정

리덕스 스토어에 싱크 시키기 
yarn add reactotron-redux --dev 입력

reactotroncongif.js 에 플러그인 추가

#3-14 Installing Redux Dev Tools

yarn add redux-devtools-extension --dev

크롬 확장도구 라서 더 편리

reactotron 때문에 오류 생기면 
configureStore.js, index.js 에서 주석 처리


#3-15 Multi Language with Redux
** 언어설정
yarn add redux-i18n

translations.js 에 원하는 언어 추가

#3-16 Moving the App Component and Adding Reset-CSS
파일 삭제 및 정리 
reset css 브라우저 디폴트 세팅을 가져와서 이를 초기화 시킴
yarn add reset-css

#3-17 Adding SCSS Variables
config폴더생성
_variables.scss 파일에서 변수 정의하고
styles.scss 파일에서 적용

>>cra 업데이트후 변경되는 부분 적용 
https://academy.nomadcoders.co/courses/instagram-full-stack-front-end-back-end-ios/lectures/6726442

>>> 글로벌 변수 적용 안시키고 진행

#3-18 Creating the Footer Component
** 글로벌 변수 적용 안시키고 진행 


#3-19 Styling the Footer
font 쉽게 찾는 꿀팁
window에서는 윈도우로 치면 나옴
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

roboto폰트는 구글 폰트에서 추가해야함 

4:56초 동영상 보고 있음

style  적용에 문제가 있어서 frontend 폴더를 삭제하고 nomadgram 폴더에서 cra재설치
https://youtu.be/KZW99D2LuuQ
npx creat-react-app frontend ( nomadgram 폴더에서 설치 )
yarn 버전 업데이트
brew yarn upgrade yarn

파일명 변경 및 설치
yarn add node-sass

정상 작동 확인

git add . > git commit -m ""

eject
yarn eject 
webpack.config.dev.js
webpack.config.prod
파일 변경

global variables
다음동영상에서 진행

https://youtu.be/rZOduIgjKYI

webpack.config.dev.js
webpack.config.prod
파일 변경

yarn build

#3-17 Adding SCSS Variables

cra 업데이트 과정에서는 잘 되었는데 
redux 적용과정에서 router 업데이트 이슈 (#3-11)

글로벌 변수 적용 하는 부분에서 또다시 변수 적용 안됨
지옥 ....

혹시라도 scss 파일 import 에 문제 있으신 분들은 webpack 설정 중 data: `@import ~~~;`작성을 test: sassRegex 가 있는 부분에도 추가해주세요~
댓글 대로 적용

#3-18 Creating the Footer Component

config 폴더 파일 생성 
_sizes.scss
_colors.scss
생성해서 _variablesl.scss파일로 불러옴

App>index.js 파일 편경해서 Footer컴포넌트 파일을 화면에 뿌림

#3-20 Mixins and Responsive Footer
_mixin.scss 파일 생성하고 디스플레이 사이즈에 따라 미디어 쿼리 작성 

#3-21 Making the App container
** 코드를 생성하고 변경하는 패턴을 알려주는 강의
user 리듀서 변경
이름변경
redux>modules> user.js 이름으로 변경

configureStore.js 경로 변경
확장 프로그램에서 이름 변경된것 확인

App>contaner.js presenter.js 생성

App>indes.js 내용을 presenter.js 파일로 옮기기

index.js수정

#3-22 React Design Patterns
react component patten ( 니콜라스 추천 스터디 링크 )
https://levelup.gitconnected.com/react-component-patterns-ab1f09be2c82


#3-23 Handling Authentication with Redux and React Router
할 차례

presenter.js 라우터 설정
switch를 적용해서 url로 접근할때 분기점을 줌

array로 리턴해서 여러개를 switch 하게 만듬

jwt 토큰값이 있는지 없는지에 따라 login hello feed 가 다르게 출력되도록함

#3-24 Auth Component part One
** 로그인 컴포넌트 만들기
App > index.js container.js presenter.js styles.scss 파일 생
성

#3-25 Auth Component part Two
가입해야 할경우 다른 로그인 화면 보여줌

#3-26 Auth Component part Three
AuthForms > index.js styles.scss 파일 생성

아이콘 사용할때 
react-ionicons를 사용 하면 됨 
yarn add react-ionicons

error 발생
Module not found: Can't resolve 'react-ionicons' in '/Users/bill/Desktop/bsdir2/nomadgram/frontend/src/components/AuthForms'

우선 주석처리 하고 진행

해결
package.json 에 설치된 버전이 높아서 안된거였습니다
yarn remove react-ionicons
해서 설치된거 지우고

yarn add react-ionicons@2.0.2
로 설치하니까 잘됩니다 ^ ^

#3-27 Finishing Auth Component and the Auth Forms
버튼 색상은 잘 먹었는데 반응형이 안됨 
다시 복붙해야할 듯 > 해결

> face book 로그인 적용을 위해서 앞에 안한 부분 다시 하기


#1-72 Signing Up : Logging In
nomadgram 폴더에서 pipenv install django-rest-auth
base.py 파일에 내용 추가
urls.py 파일에 내용 추가 

error 발생  
Someone can suffer error because ACCOUNT_EMAIL_VERIFICATION = 'none' is not applied. In my case ACCOUNT_EMAIL_VERIFICATION = 'mandatory', it could make error. So It should be changed to none because email is not required but verify it is weird.

댓글보고 해결

python manage.py makemigrations && python manage.py migrate

#1-73 Uploading a Photo
nomadgram > feed.py 파일 변경


#1-74 Uploading profile image

#1-75 Login in with Facebook
** 장고 어드민 설정 안됨 
** postman으로 확인 안함
** 문제가생길요지 있음
base.py 서드 파이 앱 추가 쿠키커러에 기본기능 
'allauth.socialaccount.providers.facebook', 
소셜 로그인 제공 업체확인은 아래 링크에서 확인 가능
https://django-allauth.readthedocs.io/en/latest/providers.html

python manage.py makemigrations && python manage.py migrate

facebook 개발자 아이디 생성

장고 어드민에 내용 추가 ( 장고 어드민 들어가는 링크 변경 찾아야함 -__-;;)

view변경
https://django-rest-auth.readthedocs.io/en/latest/installation.html#social-authentication-optional

from allauth.socialaccount.providers.facebook.views import FacebookOAuth2Adapter
from rest_auth.registration.views import SocialLoginView

class FacebookLogin(SocialLoginView):
    adapter_class = FacebookOAuth2Adapter

facebook access token 받는 링크  
https://developers.facebook.com/tools/accesstoken/


#3-28 Improving the Responsive Mixin
할차례
디바이스 대응 반응형으로 화면 바뀌도록 _mix 파일 수정

#3-29 React Context And Translating the Footer
리덕스의 언에 스테이트에 따라서 푸터의 내용을 변경하는 이론설명 

#3-30 Stateless Components and Context
번역 숙제
모든 요소 번역
안하고 넘어감 -__-;;
깃헙 복
붙
https://github.com/nomadcoders/nomadgram/commit/8cb3dc939e8e80d0c7240d30ae929b3996ba9454

#3-31 Extracting Translations
package.json 
script 설치 명령에 extreact 항목 설정
>> yarn extract 명령어로 i18 패키지 설치 > 번역파일 추가하면 번역해서 사이트 보여주는 리엑트 패키지 
>> locales/template.pot 파일 생성된거 확인 > 번역을 도와주는 파일  pot을 언어별로 생성해서 파일을 설정해주면 됨

#3-32 Importing Translations
번역 어떻게 하고 불러오는지 알려줌 
파일생성: local>es.po 
local>template.pot 의 내용 복붙

script 설치 명령에 import 항목 설정
>> yarn import 명령어로 i18 패키지 설치 > 번역파일 추가하면 번역해서 사이트 보여주는 리엑트 패키지 
** 언어별로 인코딩 부분 넣어줌  
"import": "i18n_import --encoding=utf-8"
** yarn run import 명령어 실행 ( run명령어가 들어가는 이유는 기본 명령어 중에 import명령어가 있기 때문 )

chrome redux확장프로그램에서
lang:"es"
추가해서 확인
>> 노마드 크롬 확장화면이랑 화면이 달라져서 확인 못하고 넘어감

#3-33 Moving the AuthForm to their own components
** 로그인 회원가입 컴포넌트 정리

로그인 폼을 리덕스와 연결해서 작동하도록 만들기
폴더 생성 및 파일 생성
LoginForm
SignupForm
Shared>formstyles.scss >> css파일을 만들어서 공유하기 위한 폴더

vscode 기능 ctrl+d 동일한 단어 멀티 셀렉팅

내용 복붙해야함 
https://github.com/nomadcoders/nomadgram/commit/d119a5c7a1c5596aa3a06a8bd8db2892962b4548

#3-34 Controlling inputs and submit on LoginForm (코딩 챌린지 #1)
** input의 값을 받아서 api로 보내기
Loginform> container.js presenter.js 파일 변경해서 서버로 가기전에 내용을 저장

container.js > _handleInputChage 함수 : 


** preventDefault : 브라우저에게 디폴트 작업을 하지 말라 라고 이야기하는 함수 
    _handleSubmit = event => {
        event.preventDefault();
    }


redux 넣기 전까지 작업을 loginform 으로 하고 signupform에 직접해보는 코딩챌린지

Sign Up Form Coding Challenge Solution (코딩 챌린지#1: 결과)
https://github.com/nomadcoders/nomadgram/commit/fc0a6af1978966b32c2bfa91e8f35f27540df86d

#3-35 Login In with Facebook (코딩 챌린지 #2)
yarn add react-facebook-login

설치후 불러오기

복붙
https://github.com/nomadcoders/nomadgram/blob/09c455b3bf8a0910473406a176d428aa154bb52c/frontend/src/shared/formStyles.scss

Sign Up with Facebook Coding Challenge Solution (코딩 챌린지 #2: 결과)
복붙
https://github.com/nomadcoders/nomadgram/commit/4b32dee6fc0c465f09b66036dff4b6b7cfade00f


#3-36 Creating Facebook Login Redux Action pt. One
base.py 파일 수정
-> 만료 되지 않는 토큰 만들기

리덕스 모듈 추가
-> ueer.js 에서 변경

redux tunk
디스패치 조절

adapters.py 영상에 없는 것 같은데 깃헙에 수정됨
로그인 연결 문제 발생 
>> 



Nomadclone 앱이 정보를 전송하는 데 보안 연결을 사용하지 않는 것이 확인되었습니다.
오류 해결 동영상 
https://youtu.be/LuSBgKxjmtA
https://ngrok.com

로그인 문제 페이스북 정책이 2018년도 10월달에 https 로 꼭 접속을 해야 하는걸로 바뀌어서 안되는것 같음

일반 로그인으로 접속하고 나중에 실서버 운영할때 적용하고 

https 제공해주는 무료 서비스 업체 
https://www.cloudflare.com/ko-kr/


#3-40으로 넘어가기 > 니콜라스도 오케이함 FB는 퍼킹이다

#3-40 Login In Redux Action
로그인 했을때 반응이 없음 ㅎ