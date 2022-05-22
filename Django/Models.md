# Models

## ORM
* Object Relational Mapping

* 파이썬의 객체를 통해 DB를 조작한다.

* models.py 안에 class로 테이블을 표현한다.

#### 예를들어 

|학번|이름|...|
|------|---|---|
|2021..|김OO|...|
|2019..|최OO|...|
|2020..|박OO|...|

위 테이블은 아래 코드로 표현할 수 있다.
```
from django.db import models

class Student(models.Model):
    studentNumber = models.IntegerField()
    name = models.CharField()
    picture = models.ImageField()
    classes = models.TextField()
    date = models.DateTimeField()
```
### 객체는 models.Model을 상속받아 장고의 모델 기능을 사용한다.
### 각 field들은 위 코드와 같이 타입을 명시해야한다.

## Migration
* 데이터베이스를 초기화해주거나 변경사항을 반영해 주는 일
```
python manage.py migrate
```
```
python manage.py makemigrations
```
### 초기화
* 초기화는 위 코드 중 migrate를 사용한다.
### 변경사항 반영
* 변경사항을 반영할 때 migrate는 데이터베이스 변경사항을 담은 파일을 토대로 DB에 반영한다.
* 그 변경사항을 담은 파일은 makemigrations를 통해 생성한다.
* 따라서 makemigrations 명령어로 변경사항 파일을 생성하고 migrate 명령어로 변경사항을 테이블에 직접 반영한다.
