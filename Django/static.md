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
    BASE_DIR / 'static'
]
```
* 리스트 내부에는 staticfile들이 위치한 경로를 적어준다.

* Django에서 최상위 디렉토리를 BASE DIRECTORY라고 부른다.

* 위 코드와 같이 적으면 프로젝트 폴더 바로 하위에 static 폴더에서 staticfile들을 관리한다.

* 일반적으로 static 폴더안에 바로 css 파일, 이미지 파일 등을 넣지 않고 css 폴더, js 폴더, image 폴더를 만들어 그 안에 저장한다.

