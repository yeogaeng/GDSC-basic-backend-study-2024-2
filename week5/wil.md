# wil

# 이론

### 장고 ORM 사용법

클래스명.objects로 DB에 저장된 값에 접근

클래스명.objects.all() 함수를 사용해 모든 테이블 정보를 객체로 만들어 리스트로 반환

클래스명.objects.get(id = 2) : 조건에 맞는 데이터를 객체로 만들어 하나만 반환한다.

클래스명.objects.filter() : 조건에 맞는 정보들을 객체로 만들어 여러 개 반환하는데 리스트로 반환.

### 템플릿으로 넘기는 과정

request : HTTP Request를 장고에서 객체로 만들어서 request로 넘김

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image.png)

- request는 view 함수, render 함수 인자에 넣어줘야함
- `render(request, ‘html이름’, 넘겨줄 dictionary)`

dictionary에 그대로 보내고 접근할 때는 

context = {’student’ : student}

객체 내부 데이터 접근하려면 객체이름.필드 이런식으로 찾아쓴다

ex. {{student.address}}

+장고 템플릿이 지원하는 html에서 사용가능한 if, for문

{%%} 안에 사용

```java
<ol>
{% for student in student_list %}
<li>{{[student.name](http://student.name/)}}</li>
{% endfor %}
</ol>
{% if student %}
<p>{{[student.name](http://student.name/)}}</p>
{% endif %}
```

{% %} 안에 if, for과 같은 파이썬의 제어문을 넣는 것도 가능하다.

# 실습

질문을 만들자

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%201.png)

이 질문 내용을 html에 띄워주는 작업이 이번 실습

### views.py

이전에 만든 kim 이런 것들 지우고 get함수를 통해 객체를 가져오자.

`from questions.models import Question`

`question = Question.objects.get(id=1)` 

`context = {'question' : question}`

추가

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%202.png)

### index.html

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%203.png)

이렇게 바꿔준다.

위의 애들은 우리가 모델 만들었을 때 자동으로 만들어준 models.py에 있는 컬럼값들이다.

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%204.png)

실행하면

created_time에 맞게 잘 나온다.

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%205.png)

근데 이건 실습 캡처한거 ㅎ

### urls.py

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%206.png)

경로 index.html → view.question_List로 변경

### views.py

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%207.png)

장고 orm으로 db 정보 받아와

딕셔너리에 넣어

render함수로 html에 정보 넘겨

question_list.html 생성

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%208.png)

돌려\

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%209.png)

굿티비

제목 누르면 상세 페이지가 뜨게 만들어보자.

하이퍼링크 달아서 그 페이지로 갈 수 있게 만들자.

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2010.png)

여기서는 이동은 가능하지만 그 페이지에 내용은 없다.

내용 추가하기

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2011.png)

내용 보여주는애가 사실 index.html과 같은 내용이니까

index.html 을 정의한 [views.py](http://views.py) 에서의 함수 이름을 바꾸자.

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2012.png)

그리고 돌려

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2013.png)

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2014.png)

questions/1 로 이동해서 내용이 보이게 된다.

근데 질문1만 보이니 다른 것도 보이게 id값을 넘겨주자

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2015.png)

이렇게 변경해주고

[urls.py](http://urls.py) 코드에서도 questions/1로 되어있던 걸 id를 변수로 받아둘 수 있게 바꿔준다.

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2016.png)

view에서 인자 넘겨주게 바꿔주자.

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2017.png)

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2018.png)

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2019.png)

![image.png](wil%20119ff3cfbdea8078a652df285229dc39/image%2020.png)

1,2,3 page 다 잘 보인다~