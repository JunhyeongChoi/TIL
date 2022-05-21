# Template

## Template 언어
```
{% url 'url name' %}
```
### url로 이동하는 데 그 url은 url name이다.
ex)
```
path('about/', views.about, name='about'),
```
urlpatters에 위와 같이 작성했다고 하고
```
<a href="{% url 'about' %}">about</a>
```
HTML 코드에 이렇게 작성한다면 about을 눌렀을 때 웹주소/about으로 이동된다.

## Template 상속
* HTML 파일을 여러 개 만들고 코드를 작성하다보면 각 HTML마다 꼭 들어가야 하는 코드가 있을 수 있다. 

* HTML을 만들 때마다 그 코드를 쓰면 비효율적이므로 template의 상속의 개념을 사용한다.

### 방법
1. HTML을 하나 만들고 중복되는 코드를 작성한다. (예를들어 example.html)
2. 아래와 같이 코드를 작성한다. 이 block 바깥 코드는 모두 중복되는 코드라는 의미이다.
```
{% block content %}

{% endblock %}
```
3. 이제 원래의 HTML 코드에서 example.html을 상속 받아야 한다. 최상단에 아래와 같은 코드를 작성한다. example.html을 상속받겠다는 의미임
```
{% extends 'base.html' %}
```
4. 아래와 같이 블록안에는 중복되지 않는 각 HTML마다 서로 다른 코드를 작성한다.
```
{% block content %}
<h1>서로 다른 코드</h1>
{% endblock %}
```
