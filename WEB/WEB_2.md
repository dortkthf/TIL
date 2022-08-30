# CSS 기본 스타일

## 크기 단위

- px (픽셀)
  - 모니터 해상도의 한 화소인 '픽셀' 기준
  - 픽셀의 크기는 변하지 않기 때문에 고정적인 단위
- %
  - 백분율 단위
  - 가변적인 레이아웃에서 자주 사용
- em
  - (바로 위, 부모 요소에 대한) 상속의 영향을 받음
  - 배수 단위, 요소에 지정된 사이즈에 상대적인 사이즈를 가짐
- rem
  - (바로 위, 부모 요소에 대한) 상속의 영향을 받지 않음
  - 최상위 요소(hrml)의 사이즈를 기준으로 배수 단위를 가짐

vscode 에서 직접해보기

```html
<head>
    <style>
        .font-big {
            font-size: 36px;
        }
        .em {
            font-size: 2em;
        }
        .rem {
            font-size: 2rem;
        }
    </style>
</head>

<body>
    <ul class="font-big">
    	<li class="em">2em</li>
        <li class="rem">2rem</li>
        <li>no class</li>
    </ul>
</body>
```

크기 단위 em vs rem

![image-20220830134949285](WEB_2.assets/image-20220830134949285.png)

## 크기 단위 (viewport)

- 웹 페이지를 방문한 유저에게 바로 보이게 되는 웹 컨텐츠의 영역 (디바이스 화면)
- 디바이스의 viewport를 기준으로 상대적인 사이즈가 결정된
- 예) vw, vh, vmin, vmax

```html
<head>
    <style>
        h1 {
            color: black;
            background-color: pink;
        }
        .px {
            width: 200px;
        }
        .vw {
            width: 50vw;
        }
    </style>
</head>
<body>
    <h1 class="px">
        px사용
    </h1>
    <h1 class"vw">
        vw사용
    </h1>
</body>
```

## 색상 단위

- 색상 키워드(background-color: red;)
  - 대소문자를 구분하지 않음
  - red, blue, black 과 같은 특정 색을 직접 글자로 나타냄
- RGB 색상(background-color: reg(0, 255, 0);)
  - 16진수 표기법 혹은 함수형 표기법을 사용해서 특정 색을 표현하는 방식
- HSL 색상(background-color: hsl(0, 100%, 50%);)
  - 색상, 채도, 명도를 통해 특정 색을 표현하는 방식

```html
p { color: black;}
p { color: #000;}
p { color: #000000;}
p { color: rgb(0, 0, 0);}
p { color: hsl(120, 100%, 0);}

p { color: rgba(0, 0, 0, 0.5);}
p { color: hsla(120. 100% 0.5);}
```

모두 black!

- 색상 키워드
- RGB 색상
  - '#' + 16진수 표기법
  - rgb() 함수형 표기법
- HSL 색상
  - 색상, 채도, 명도
- a는 alpha(투명도)

## CSS 문서 표현

- 텍스트
  - 서체(font-family), 서체 스타일(font-style, gont-weight 등)
  - 자간(letter-spacing), 단어 간격(word-spacing), 행간(line-height) 등
- 컬러(color), 배경(background-image, backgound-color)
- 기타 HTML 태그별 스타일링
  - 목록(li), 표(table)

# CSS Selectors

## 선택자(Selector) 유형

- 기본 선택자
  - 전체 선택자, 요소 선택자
  - 클래스 선택자, 아이디 선택자, 속성 선택자
- 결합자(Combinators)
  - 자손 결합자, 자식 결합자
  - 일반 형제 결합자, 인접 형제 결합자
- 의사 클래스/요소(Pseudo Class)
  - 링크, 동적 의사 클래스
  - 구조적 의사 클래스. 기타 의사 클래스, 의사 엘리먼트, 속성 선택자

## CSS 선택자 정리

- 요소 선택자
  - HTML 태그를 직접 선택
- 클래스(class) 선택자
  - 마침표(.)문자로 시작하며, 해당 클래스가 적용된 항목을 선택
- 아이디(id) 선택자
  - #문자로 시작하며, 해당 아이디가 적용된 항목을 선택
  - 일반적으로 하나의 문서에 1번만 사용
  - 여러 번 사용해도 동작하지만, 단일 id를 사용하는 것을 권장

## CSS 적용 우선순위 (cascading order)

1. 중요도 (Importance) : 사용시 주의
   - !important
2. 우선 순위 (Specificity)
   - 인라인 > id > class, thrtjd, pseudo-class > 요소, pseudo-element
3. CSS 파일 로딩 순서

## CSS 상속

- CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속한다.

  - 속성(프로퍼티) 중에는 상속이 되는 것과 되지 않는 것들이 있다.

  - 상속 되는 것 예시

    예) Text 관련 요소(font, color, text-align), opacity, visibility 등

  - 상속 되지 않는 것 예시

    예) Box model 관련 요소(width, height, margin, padding, border, box-sizing, display)

    position 관련 요소(position, top/right/bottom/left, z-index)등

```html
<head>
    <style>
        p {
            /* 상속됨 */
            color: red;
            /* 상속 안됨 */
            border: 3px solid black;
        }
        span {
            
        }
    </style>
</head>
<body>
    <p>
        안녕하세요! <span>테스트</span> 입니다.
    </p>
</body>
```

![image-20220830141417447](WEB_2.assets/image-20220830141417447.png)

# CSS Box model

![image-20220830141435322](WEB_2.assets/image-20220830141435322.png)

![image-20220830141442801](WEB_2.assets/image-20220830141442801.png)

## Box model

- 모든 HTML 요소는 box 형태로 되어있음
- 하나의 박스는 네 부분(영역)으로 이루어짐
  - margin
  - border
  - padding
  - content

![image-20220830141548401](WEB_2.assets/image-20220830141548401.png)

## Box model 구성 (padding)

![image-20220830141706195](WEB_2.assets/image-20220830141706195.png)

![image-20220830141710775](WEB_2.assets/image-20220830141710775.png)

# Box model 구성 (border)

![image-20220830141816562](WEB_2.assets/image-20220830141816562.png)

## vscode 에서 직접해보기 - box model

```html
<head>
    <style>
        .box1 {
            width: 500px;
            border-width: 2px;
            border-color: black;
            border-style: dashed;
            padding-left: 20px
            magin-bottom: 30px
        }
        . box2 {
            width: 500px;
            border: 2px solid black;
            padding: 20px 30px;
        }
    </style>
</head>
<body>
    <div class="box1">
        div
    </div>
    <div class="box2">
        div
    </div>
</body>
```

![image-20220830142505080](WEB_2.assets/image-20220830142505080.png)

```html
<head>
    <style>
        .box {
            width: 100px
            margin: 10px auto;
            padding: 20px;
            border: 1px solid black;
            color: white;
            text-slign: center;
            background-color: blueviolet;
        }
        
        .box-sizing {
            box-sizing: border-box;
            margin-top: 50px
        }
    </style>
</head>
<body>
    <div class="box">
        content-box
    </div>
    <div class="box box-sizing">
        border-box
    </div>
</body>
```

![image-20220830142837246](WEB_2.assets/image-20220830142837246.png)

![image-20220830142841628](WEB_2.assets/image-20220830142841628.png)

## box-sizing

- 기본적으로 모든 요소의 box-sizing은 content-box
  - padding을 제외한 순수 contents 영역만을 box로 지정

- 다만, 우리가 일반적으로 영역을 볼 떄는 border까지의 너비를 100px 보는 것을 원함
  - 그 경우 box-sizing을 border-box로 설정

![image-20220830143124184](WEB_2.assets/image-20220830143124184.png)

# CSS Display

- 모든 요소는 네모(박스모델)이고, 좌측상단에 배치.
- display에 따라 크기와 배치가 달라진다.

## 대표적으로 활용되는 display

- display: block
  - 줄 바꿈이 일어나는 요소
  - 화면 크기 전체의 가로 폭을 차지한다.
  - 블록 레벨 요소 안에 인라인 레벨 요소가 들어갈 수 있음.
- display: inline
  - 줄 바꿈이 일어나지 않는 행의 일부 요소
  - content 너비만큼 가로폭을 차지한다.
  - width, height, margin-top, margin-bottom을 지정할 수 없다.
  - 상하 여백은 line-height로 지정한다.
- display: inline-block
  - block과 inline 레벨 요소의 특징을 모두 가짐
  - inline처럼 한 줄에 표시할 수 있고, block처럼 width, height, margin 속성을 모두 지정할 수 있음
- display: none
  - 해당 요소를 화면에 표시하지 않고, 공간조차 부여되지 않음
  - 이와 바슷한 visibility: hidden은 해당 요소가 공간은 차지하나 화면에 표시만 되지 않는다.
- 이외 다양한 display 속성은 https://developer.mozilla.org/ko/docs/Web/CSS/display

## 블록 레벨 요소와 인라인 레벨 요소

- 블록 레벨 요소와 인라인 레벨 요소 구분 (HTML 4.1 까지)

- 대표적인 블록 레벨 요소

  div / ul, ol, li / p / hr / form 등

- 대표적인 인라인 레벨 요소

  span / a / img / input, label / b, em, i, stron 등

## block

![image-20220830143648839](WEB_2.assets/image-20220830143648839.png)

block의 기본 너비는 가질 수 있는 너비의 100%

![image-20220830143702367](WEB_2.assets/image-20220830143702367.png)

너비를 가질 수 없다면 자동으로 부여되는 margin

## inline

![image-20220830143724146](WEB_2.assets/image-20220830143724146.png)

inline의 기본 너비는 컨텐츠 영역만큼

## 속성에 따른 수평 정렬

![image-20220830143808196](WEB_2.assets/image-20220830143808196.png)