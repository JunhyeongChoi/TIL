# Template language

## 기본 틀
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

