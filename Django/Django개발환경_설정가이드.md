# Django 개발 환경 설정 가이드

### 1. git bash창을 아무위치에서 열고나서 cd ~를 입력해서 ~ 홈폴더로 간다

![image-20220921142413763](C:\Users\이준엽\Desktop\DEV\TIL\Django\Django 개발 환경 설정 가이드.assets\image-20220921142413763.png)

### 2. ~ 홈화면에서 서버로 만들 폴더를 mkdir 명령어를 통해 만든다.

![image-20220921142558059](C:\Users\이준엽\Desktop\DEV\TIL\Django\Django 개발 환경 설정 가이드.assets\image-20220921142558059.png)

### 3. cd명령어를 통해서 해당 서버 폴더로 이동한다.

![image-20220921142725467](C:\Users\이준엽\Desktop\DEV\TIL\Django\Django 개발 환경 설정 가이드.assets\image-20220921142725467.png)

### 4. $ python -m venv [일반적으로는 이름-venv 로 생성함] 명령어를통해 파이썬 모듈인 venv를 실행시켜 [가상공간폴더]를 생성한다.![image-20220921143534737](C:\Users\이준엽\Desktop\DEV\TIL\Django\Django 개발 환경 설정 가이드.assets\image-20220921143534737.png)

### 5. $ source [가상 공간 폴더명]/Scripts/activate 명령어로 가상서버를 실행시킨다.

- **그냥 activate파일만 실행 시키면 되므로 만약 최초의 서버 폴더안에 있었다면**

  즉 **~/test 의 위치에 내가 있다면**

  **sourve test-venv/Scripts/activate** 로 입력해서 가상공간을 실행시킨다.

  **만약 생성된 가상공간폴더안에 위치해 있다면**

  즉 **~/test/test-venv/ 의 위치에 내가 있다면**

  **source Scripts/activate** 를 입력해서 가상 공간을 형성한다.

![image-20220921144750525](C:\Users\이준엽\Desktop\DEV\TIL\Django\Django 개발 환경 설정 가이드.assets\image-20220921144750525.png)

 ### 6. 해당 가상공간폴더에 가장 안전한 버전의 django 3.2.13버전을 설치한다.

- **pip install django==3.2.13 명령어를 통해 설치한다.**

![image-20220921145231610](C:\Users\이준엽\Desktop\DEV\TIL\Django\Django 개발 환경 설정 가이드.assets\image-20220921145231610.png)

### 7. django-admin startproject [프로젝트 이름] . 을 통해 장고 기본 프로젝트를 생성합니다.

- 반드시 . 마침표를 입력해서 현재 폴더에 프로젝트를 생성하기로 합니다.

![image-20220921161745179](Django 개발 환경 설정 가이드.assets/image-20220921161745179.png)

### 8. 해당 프로젝트에서 사용할 app을 아래 명령어를 통해 생성합니다.

![image-20220924212049724](Django개발환경_설정가이드.assets/image-20220924212049724.png)

### 9. 프로젝트 폴더안에 settings.py 에 ISTALLED_APPS 에 생성한 app을 추가해줍니다.

![image-20220924212250687](Django개발환경_설정가이드.assets/image-20220924212250687.png)

### 10. 프로젝트 폴더안의 urls.py 안에 from drink import views 를 추가시키고 urlpatterns 안에 views에서 실행할 함수를 views.[함수이름] 으로 추가해줍니다.

![image-20220924212532167](Django개발환경_설정가이드.assets/image-20220924212532167.png)

### 11. 이후 drink 폴더의 views.py 로 돌아가서 drink라는 함수를 생성해줍니다.

![image-20220924212739259](Django개발환경_설정가이드.assets/image-20220924212739259.png)

### 12. 이후 drink 폴더 내에 templates 라는 폴더를 생성한 이후에 templates 폴더 안에 drink.html 이라는 파일을 생성해줍니다.

![image-20220924212903929](Django개발환경_설정가이드.assets/image-20220924212903929.png)

### 13. python manage.py runserver 명령어를 통해 서버를 실행시킵니다.

![image-20220921161949537](Django 개발 환경 설정 가이드.assets/image-20220921161949537.png)

- 기본적으로 웹브라우저에 localhost:8000 을 입력시키면 내가 실행시킨 서버의 django가 나온다.

### 14. 서버를 종료할때

**<kbd>Ctrl</kbd> + <kbd>c</kbd>** 를 입력해서 나가고 **diactivate**를 입력해서 서버를 종료시킨다.야

![image-20220921153448478](Django 개발 환경 설정 가이드.assets/image-20220921153448478.png)

- **<kbd>Ctrl</kbd> + <kbd>c</kbd>** 로 나가게되면 해당 서버는 들어가지지 않는다.

### url을 통한 변수받기

url을 통해서 값을 받기 위해서는 프로젝트폴더 내에 urls.py에서 path의 주소창 안에 <>를 표시하고 그 안에 정의할 수나 문자를 넣는다.

![image-20220926181731695](Django개발환경_설정가이드.assets/image-20220926181731695.png)

이후에 프로젝트앱 폴더내의 views.py에서 함수를 정의할때에 request옆에 처음에 정의했던 number나 혹은 number1 number2 를 입력해서 받고 이를 해당 함수 context안에 넣는다.

![image-20220926181808251](Django개발환경_설정가이드.assets/image-20220926181808251.png)

### form을 통한 변수받기

변수를 보내는 url과 받는 url 모두 프로젝트본체 폴더 안에 urls.py 내에 기록되어야한다.

![image-20220926182120757](Django개발환경_설정가이드.assets/image-20220926182120757.png)

form을 통해서 변수를 받기 위해서는 변수를 보내는쪽과 변수를 받는쪽 총 2개의 페이지가 있어야한다.  

변수를 보내는 쪽의 html에서 form을 정의하고 form 태그 안에서 action 값을 변수를 받을 url을 입력한다. 

이후 변수로 보낼 input 태그 안에 name이라는 속성을 통해 변수이름을 설정해서 보낸다.

![image-20220926181711650](Django개발환경_설정가이드.assets/image-20220926181711650.png)

변수를 보내는 쪽의 함수정의는 딱히 할게없다.

![image-20220926181950797](Django개발환경_설정가이드.assets/image-20220926181950797.png)

변수를 받는쪽의 함수정의에서는 request.GET.get('name')으로 변수를 받아들인다.

변수를 보내는쪽의 form태그에서 name속성으로 정의했던 이름이 변수의 이름이다.

![image-20220926184018721](Django개발환경_설정가이드.assets/image-20220926184018721.png)

변수를 여러개 받을수도있다.

![image-20220926184139016](Django개발환경_설정가이드.assets/image-20220926184139016.png)