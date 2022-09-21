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

### 8. python manage.py runserver 명령어를 통해 서버를 실행시킵니다.

![image-20220921161949537](Django 개발 환경 설정 가이드.assets/image-20220921161949537.png)

- 기본적으로 웹브라우저에 localhost:8000 을 입력시키면 내가 실행시킨 서버의 django가 나온다.

### 9. 서버를 종료할때

**<kbd>Ctrl</kbd> + <kbd>c</kbd>** 를 입력해서 나가고 **diactivate**를 입력해서 서버를 종료시킨다.야

![image-20220921153448478](Django 개발 환경 설정 가이드.assets/image-20220921153448478.png)

- **<kbd>Ctrl</kbd> + <kbd>c</kbd>** 로 나가게되면 해당 서버는 들어가지지 않는다.