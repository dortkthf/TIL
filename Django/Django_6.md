# UPDATE

### 개요

- 수정은 CREATE 로직과 마찬가지로 2개의 view 함수가 필요
- 사용자의 입력을 받을 페이지를 렌더링 하는 함수 1개
  - 'edit' view function
- 사용자가 입력한 데이터를 전송 받아 DB에 저장하는 함수 1개
  - 'update' view function

```python
# articles/urls.py

urlpatterns = [
    ...
    path('<int:pk>/edit',views.edit, name='edit'),
]

# ariticles/views.py

def edit(request, pk):
    article = Article.objects.get(pk=pk)
    context = {
        'article':article,
    }
    return render(request, 'articles/edit.html', context)
```

### Edit - templates

- html 태그의 value 속성을 사용해 기존에 입력 되어 있던 데이터를 출력

```html
<!-- articles/edit.html -->
{% extends 'base.html' %}
{% block content %}
    <h1>EDIT</h1>
    <form action="#" method="POST">
        {% csrf_token %}
        <label for="title">Title: </label>
        <input type="text" name="title" value="{{ article.title }}"><br>
        <label for="content">Content: </label>
        <textarea name="content" cols="30" rows="5">{{ article.content }}</textarea><br>
        <input type="submit">
    </form>
    <hr>
    <a href="{% url 'articles:index' %}">[back]</a>
{% endblock content %}

<!--textarea 태그는 value 속성이 없으므로 태그 내부 값으로 작성해야 한다.-->
```

- Edit 페이지로 이동하기 위한 하이퍼 링크 작성

```html
<!-- articles/detail.html -->
{% extends 'base.html' %}
{% block content %}
<h2>DETAIL</h2>
<h3>{{ article.pk }} 번째 글</h3>
<hr>
<p>제목: {{ article.title }}</p>
<p>내용: {{ article.content }}</p>
<p>작성 시각: {{ article.created_at }}</p>
<p>수정 시각: {{ article.updated_at }}</p>
<hr>
<a href="{% url 'articles:edit' article.pk %}">EDIT</a><br>
<form action="{% url 'articles:delete' article.pk %}" method="POST">
{% csrf_token %}
<input type="submit" value="DELETE">
</form>
<a href="{% url 'articles:index' %}">[back]</a>
{% endblock %}
```

