#### M:N (User-User)

**Profile 구현**

- url 및 view 함수 작성

  ```python
  # accounts/urls.py
  
  urlpatterns = [
      ...,
      path('profile/<username>/', views.profile, name='profile'),
  ]
  
  # accounts/views.py
  
  from django.contrib.auth import get_user_model
  
  def profile(request, username):
      User = get_user_model()
      person = User.objects.get(username=username)
      context = {
          'person' : person,
      }
      return render(request, 'accounts/profile.html', context)
  ```

- profile 템플릿 작성

  ```html
  <!--accounts.profile.html-->
  
  {% extends 'base.html' %}
  
  {% block content %}
  ```

  

