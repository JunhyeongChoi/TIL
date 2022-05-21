# static

### static file이란 CSS, JavaScript, 이미지 등과 같이 개발자가 사전에 미리 서버에 저장 해둔 파일들을 의미한다.

#### static 파일과 관련된 설정은 settings.py에서 진행

* static URL
```
STATIC_URL = '/static/'
```
웹주소/static/파일이름으로 static 파일에 접근할 수 있다.

* static directory
```
STATICFILES_DIRS = [
    BASE_DIR / 'static',
]
```
* 리스트 내부에는 staticfile들이 위치한 경로를 적어준다.

* Django에서 최상위 디렉토리를 BASE DIRECTORY라고 부른다.

* 위 코드와 같이 적으면 프로젝트 폴더 바로 하위에 static 폴더에서 staticfile들을 관리한다.

* 일반적으로 static 폴더안에 바로 css 파일, 이미지 파일 등을 넣지 않고 css 폴더, js 폴더, image 폴더를 만들어 그 안에 저장한다.

## HTML 파일에서 static 파일 불러오기
```
{% load static %}
```
HTML 코드 최상단에 작성
```
<link rel="stylesheet" type="text/css" href="{% static 'css/style.css' %}">
```
head 태그 내부에 작성
```
<img scr="{% static 'img/a.png' %}">
```
body 태그 내부에 작성

* 첫 번째 코드는 위에서 설정한 경로에 있는 static 파일들을 현재 HTML 파일에 load 하겠다는 의미이다.

* 두 번째 코드는 위에서 설정한 경로에서 css/style.css 파일을 가지고 오겠다는 의미이다.

* 세 번째 코드도 마찬가지로 img 폴더안에 a.png를 가지고 오겠다는 의미이다.

* {% %}는 장고의 Template 언어이다.

## 어플리케이션별로 static file 관리하기
* 두 가지 방법이 있다.
* 어플리케이션 폴더안에 static 폴더를 만드는 것까지는 동일

* 첫 번째 방법
os를 imprt 해주고
```
STATICFILES_DIRS = [
    BASE_DIR / 'static',
    os.path.join(BASE_DIR, 'staticapp', 'static')
]
```
위와 같이 작성하면 BASE_DIR/staticapp/static와 같은 의미

* 두 번째 방법
```
STATICFILES_DIRS = [
    BASE_DIR / 'static',
    BASE_DIR / 'staticapp' / 'static'
]
```

### 두 번째 방법을 주로 사용한다.

## STATIC_ROOT
* 개발할 때는 runserver를 통해 자동으로 static file들이 모이지만 배포할 때는 모으는 작업이 필요하다.
* settings.py에 코드 추가
```
STATIC_ROOT = os.path.join('staticfiles')
```
배포를 할 때 staticfiles에 static file들을 모두 모으겠다는 의미이다.

* static file들을 모두 모으는 명령어
```
python manage.py collectstatic
```
위 명령어를 수행하면 staticfiles 폴더가 만들어지고 그 안에 지금까지 만들어둔 모든 static file들이 복사가 된다.
