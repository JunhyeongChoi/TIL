## URL 기초 설계
* urls.py 내부 urlpatterns에 작성한다.

* path 첫 번재 인자로는 이름, 두 번째 인자로는 함수를 적는다.
ex)
```
path('first', views.first)
```
/first/로 이동했을 때 views의 first 함수를 실행시킨다.

* Appilcation 내부 views.py에 함수를 작성한다.
ex)
```
def first(request):
    return render(request, 'first.html')
```
first 함수가 실행되면 first.html을 랜더링하고 화면에 띄운다.<br>
first.html은 Application 내부에 templates 폴더를 만들고 그 안에 정의한다.

## URL Mapping
### product라는 Application이 있을 때 /product/1, /product/2 ... 
### 이러한 URL을 project urls.py에 전부 적지 않고 효율적으로 관리할 수 있다.
* product 어플리케이션안에도 urls.py를 만들고 설계한다. 설계는 위에 적은 내용과 동일
* urls.py에서 include를 import (path, 뒤에 include만 적어주면 된다.)
```
from django.urls import path, include
```
* path의 두 번째 인자로 include('product.urls')
ex)
```
path('product', 'product.urls')
```
이렇게 적었다면 /product/는 product.urls에서 관리할 수 있게 된다.<br>
product.urls에
```
path('1', views.first)
```
 적었다면 /product/1 로 이동했을 때 views.first 함수가 실행된다.
