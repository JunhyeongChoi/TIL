# MTV 패턴

# Model
* DB와 관련된 부분을 다루는 영역

* DB에 저장될 데이터의 모양을 정의하고 관련된 일부 기능들을 설정해 주는 영역

* 현실 세상을 코드로 옮기는 과정

* 예를 들어 "사람"이라는 개체를 코드로 옮긴다면 아래와 같이 만들 수 있다.
```
사람
- 이름
- 나이
- 성별
- 키
```
* 이렇게 현실에 있는 개체의 특징들을 뽑아 이를 구성요소(속성)로 하는 것을 모델링이라고 한다.

* 우리가 만든 모델 형태의 데이터들을 DB에 쌓으면 테이블 형태가 된다.

* 모델을 DB에 적용시키는 과정을 마이그레이션(migration)이라고 한다. 

* 처음에 발생하는 DB 관련 에러가 Django가 가지고 있는 기본적인 모델을 DB에 적용시키지 않았기 때문에 발생하는 것이다.

<br>

```
from django.db import models

class Photo (models.Model):
    title = models.CharField(max_length=50)
    author = models.CharField(max_length=50)
    image = models.CharField(max_length=200)
    description = models.TextField()
    price = models.IntegerField()
```
* models.py에 위와 같이 모델을 정의할 수 있다.

<br>

```
CharField : 문자열(길이제한 필요)
IntegerField : 정수
TextField : 문자열(길이제한 필요 없음)
DateField : 날짜
DateTimeField : 날짜 + 시간
FileField : 파일
ImageField : 이미지 파일
ForeignKey : 외래키
OneToOneField : 1대1 관계
ManyToManyField : 다대다 관계
```
( 위는 자주 쓰이는 필드 종류 )

<br>

* 모델을 만들거나 수정하거나 삭제할 때 등 모델에 변화가 생겼을 때 마이그레이션 과정을 통해 변경사항을 적용시켜야 한다.

* 그리고 admin.py에 우리의 모델을 등록해 어드민 페이지에서 간단히 확인할 수 있다.
```
from django.contrib import admin
from .models import Photo

admin.site.register(Photo)
```

# Template
* 사용자에게 보이는 부분, 즉 웹 페이지의 골격, HTML로 작성된 부분이다. 따라서 프론트 개발 영역에 포함된다고 볼 수 있다.

## Django Template의 특징
* Django의 Template은 일반적인 HTML 작성과 거의 비슷한데 Django만의 장점인 템플릿 태그라는 것이 존재한다.

* 이 템플릿 태그는 HTML이 파이썬 코드로부터 데이터를 바로 넘겨받아서 손쉽게 처리할 수 있는 도구이다.

* HTML은 그저 마크업 언어이므로 정적인 웹 페이지만을 보여준다. 그래서 데이터를 넘겨받아 웹 페이지에 띄우려면 자바스크립트 같은 도구가 필요한데 Django에서는 템플릿 태그가 있어 아주 편리하게 데이터를 넘겨받을 수 있다.

# View
* Django의 view는 템플릿과 모델 사이를 이어주는 다리같은 역할을 한다.

* 프론트엔드가 백엔드에 데이터를 요청했을 때, 백엔드에서 데이터를 뽑아 프론트엔드에게 제공해주는 과정을 view가 처리한다.

* 뷰를 만드는 방법은 다양한데 크게 함수형 뷰와 클래스형 뷰로 나눌 수 있다.

##  모델 -> 템플릿 -> 뷰 -> URL 순으로 작업한다.
