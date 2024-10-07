# wil.md

DB 이론

유행에 따라가기위해 RDB를 쓴다

PK FK

우린 장고 모델을 통해 DB관리할거다

DB를 바꾸는 경우 : models.py를 통해 코드 변경없이 DB만 변경 가능하다. 

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image.png)

[models.py](http://models.py) 파일에 클래스 하나 만들면 테이블을 하나 생성해줄건데 그 전에 명령어를 하나 작성햇

python [manage.py](http://manage.py) makemigrations : models.py를 돌려 뭐가 바뀐지 알아냄

python [manage.py](http://manage.py) migrate : migration의 클래스 찾아서 테이블로 만들어줌

config/settings.py를 통해 어떤 db를 사용하는지 보고 db 생성해준다.

view.py에서 만든 db를 사용할건데 

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%201.png)

이렇게 model 파일의 Student 를 불러들여 접근한다.

# 실습

open folder 로 저번 시간에 작업한 폴더(gdsc_basic_backend)를 열어준다.

```java
cd venv/bin
yeogaeng@mac bin % source activate
(venv) yeogaeng@mac bin % cd ../../project
(venv) yeogaeng@mac project % 
```

## [settings.py](http://settings.py/) 앱 등록

settings.py에 우리가 만든 questions app을 등록해줘야한다.

INSTALLED_APPS 에 `questions.apps.QuestionsConfig`를 추가했었다.

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%202.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%203.png)

urls.py에 from question import views 를 추가하여 questions 안의 views 파일을 읽을 수 있게됨

urlpattern에 경로 추가

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%204.png)

그리고 view 파일에서 index 생성하자

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%205.png)

다음은 index.html 파일을 만들건데 questions안의 templates폴더를 생성하고 helloworld를 h1 태그로 만들자

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%206.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%207.png)

저장 후 run server

`python3 [manage.py](http://manage.py/) runserver`

계속 안되던데 그 이유는 내가 questions를 project 안에 안 만들었던 잘못;;

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%208.png)

드디어 돌아간다;;;

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%209.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2010.png)

## 동적 html 생성

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2011.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2012.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2013.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2014.png)

터미널 : 
python3 manage.py makemigrations

python3 [manage.py](http://manage.py/) migrate

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2015.png)

테이블이 만들어져있는지 확인하기위해

## 어드민 계정 생성

터미널에 python3 manage.py createsuperuser 입력

사용자 이름: admin
이메일 주소: (그냥 Enter)
Password: 1111
Password (again): 1111
Pypass password validation and create user anyway? [y/N]: y

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2016.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2017.png)

![image.png](wil%20md%20118ff3cfbdea80c9a36dd4088d1934e9/image%2018.png)