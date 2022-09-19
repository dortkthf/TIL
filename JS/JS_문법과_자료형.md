# 문법과 자료형

### 기본

JS는 문법의 대부부능ㄹ Java와 C, C++로부터 차용하고 있으며 Awk, Perl, Python의 영향도 받았습니다.

JS는 **대소문자를 구별**하며 유니코드 문자셋을 이용합니다.

JS에서는 명령을 명령문 이라고 부르며, 세미콜론으로 구분합니다.

명령문이 한 줄을 다 차지할 경우에는 세미콜론이 필요하지 않습니다. 그러나 한 줄에 두 개 이상의 명령문이 필요하다면 반드시 세미콜론으로 구분해야 합니다.

하지만, 세미콜론이 필요하지 않은 경우라도 항상 세미콜론으로 끝마치는 편이 버그 예방 차원에서 더 좋은 습관이라고 여겨집니다.

JS의 스크립트 소스는 왼쪽에서 오른쪽으로 탐색하면서 토큰, 제어 문자, 줄바꿈 문자, 주석이나 공백으로 이루어진 입력 요소의 시퀀스로 변환됩니다. (스페이스, 탭, 줄바꿈 문자는 공백으로 간주됩니다.)

### 주석

주석의 구문은 C++ 및 다른 많은 언어와 똑같습니다.

```javascript
// 한 줄 주석

/* 이건 더 긴,
 * 여러 줄 주석입니다.
 */

/* 그러나, /* 중첩된 주석은 쓸 수 없습니다 */ SyntaxError */
```

주석은 공백처럼 행동하며 스크립트 실행 시 버려집니다.

### 선언

JS의 선언에는 3가지 방법이 있습니다.

`var`

​	변수를 선언, 추가로 동시에 값을 초기화.

`let`

​	블록 스코피 지역 변수를 선언. 추가로 동시에 값을 초기화.

`const`

​	블록 스코프 읽기 전용 상수를 선언.

### 변수

애플리케이션에서 값에 상징적인 이름으로 변수를 사용합니다. 변수명은 식별자(identifiers).라고 불리며 특정 규칙을 따릅니다.

JS 식별자는 문자, 밑줄(_) 혹은 달러 기호($)로 시작해야 하는 반면 이후는 숫자(0-9)일 수도 있습니다.

JS가 대소문자를 구분하기에, 문자는 'A' 부터 'Z'와 'a' 부터 'z'(소문자)까지 모두 포함합니다.

ISO 8859-1 혹은 Unicode 문자(가령 `å` 나 `ü`)도 식별자에 사용할 수 있습니다. 

적절한 이름으로는 `Number_hits`,`temp99`,`$credit`및`_name`등 입니다.

### 변수 선언

변수 선언은 아래 3가지 방법으로 가능합니다.

- var x = 42 와같이 var 키워드로 변수를 선언할 수 있습니다. 이 구문은 실행 맥락에 따라 지역 및 전역 변수를 선언하는데 모두 사용될 수 있습니다.
- let y = 13 과 같이 const 혹은 let 키워드로 변수를 선언할 수 있습니다. 이 구문은 블록 스코프 지역 변수를 선언하는데 사용될 수 있습니다.

### 변수 할당

지정된 초기 값 없이 var 혹은 let 문을 사용해서 선언된 변수는 undefined 값을 갖습니다.

선언되지 않은 변수에 접근을 시도하는 경우 RefferenceError 예외가 발생합니다.

```javascript
var a;
console.log('a 값은 ' + a); // a 값은 undefined

console.log('b 값은 ' + b); // b 값은 undefined
var b;
// 이것은 아래의 '변수 호이스팅'을 읽기 전에는 혼란스러울 수 있음

console.log('c 값은 ' + c); // Uncaught ReferenceError: c is not defined

let x;
console.log('x 값은 ' + x); // x 값은 undefined

console.log('y 값은 ' + y); // Uncaught ReferenceError: y is not defined
let y;
```

undefined를 사용하여 변수 값이 있는지 확인할 수 있습니다. 아래 코드에서 input 변수는 값이 할당되지 않았고 if 문은 true로 평가합니다.

```javascript
var input;
if(input === undefined) {
  doThis();
} else {
  doThat();
}
```

undefined 값은 불리언 맥락(context)에서 사용될 때 false 로 동작합니다. 예를 들어, 아래 코드는 myArray요소가 undefined 이므로 myFunction 함수를 실행합니다.

```javascript
var myArray = [];
if (!myArray[0]) myFunction();
```

undefinde 값은 수치 맥락에서 사용될 때 NaN 으로 변환됩니다.

```javascript
var a;
a + 2; // NaN으로 평가
```

null 값을 평가할 때, 수치 맥락에서는 0 으로, 불리언 맥락에서는 false로 동작합니다. 예를들면

```javascript
var n = null;
console.log(n * 32); // 콘솔에 0 으로 로그가 남음
```

### 변수 스코프

어떤 함수의 바깥에 변수를 선언하면, 현재 문서의 다른 코드에 해당 변수를 사용할 수 있기에 전역 변수라고 합니다. 만약 함수 내부에 변수를 선언하면, 오직 그 함수 내에서만 사용할 수 있기에 지역 변수라고 부릅니다.

예를 들어서 아래의 코드는 5라는 로그가 남는데. x의 스코프가 전역 맥락 (혹은 코드가 암수의 일부분이라면 함수 맥락)이기 때문입니다. x의 스코프는 if문 블록에 제한되지 않습니다.

```javascript
if (true) {
  var x = 5;
}
console.log(x); // 5
```

이 동작은 let 선언을 사용하면 바뀝니다.

```javascript
if (true) {
  let y = 5;
}
console.log(y); // ReferenceError: y is not defined
```

변수 호이스팅

또 다른 JS 변수의 특이한 점은 예외를 받지 않고도, 나중에 선언된 변수를 참조할 수 있다는 것입니다.

이 개념은 호이스팅(hoisting)으로 알려져 있습니다. 즉 JS 변수가 어떤 의미에서 함수나 문의 최상단으로 올려지는 것을 말합니다. 하지만, 끌어올려진 변수는 undefined 값을 반환합니다. 그래서 변수를 사용 혹은 참조한 후에 선언 및 초기화 하더라도 여전히 undefined를 반환합니다.

```javascript
/**
 * Example 1
 */
console.log(x === undefined); // true
var x = 3;


/**
 * Example 2
 */
// undefined 값을 반환함.
var myvar = "my value";

(function() {
  console.log(myvar); // undefined
  var myvar = "local value";
})();
```

호이스팅 때문에, 함수 내의 모든 var 문은 가능한 함수 상단 근처에 두는 것이 좋습니다. 이 방법은 코드를 더욱 명확하게 만들어줍니다.

let과 const는 변수를 블록의 상단으로 끌어올리지만 초기화하지 않습니다. 변수가 선언되기 전에 블록 안에서 변수를 참조하게 되면 ReferenceError를 발생시키게 되는데, 변수는 블록 시작부터 선언이 처리될 때까지"temporal dead zone"에 위치하게 되기 때문입니다.

```javascript
console.log(x); // ReferenceError
let x = 3;
```

### 함수 호이스팅

함수에서는 함수 선언으로는 호이스팅 되지만 함수 표현식으로는 호이스팅 되지 않습니다.

```javascript
/* 함수 선언 */

foo(); // "bar"

function foo() {
  console.log('bar');
}

/* 함수 표현식 */

baz(); // TypeError: baz is not a function

var baz = function() {
  console.log('bar2');
};
```

### 전역 변수

전역 변수는 사실 전역 객체의 속성 입니다.

웹 페이지에서 전역 객체는 window 이므로 windows.variable 구문을 통해 전역 변수를 설정하고 접근할 수 있습니다.

그 결과, `window` 혹은 `frame`의 이름을 지정하여 한 window 혹은 frame에서 다른 window 혹은 frame에 선언된 전역 변수에 접근할 수 있습니다. 예를 들어, `phoneNumber` 라는 변수가 문서에 선언된 경우, `iframe`에서 `parent.phoneNumber`로 이 변수를 참조할 수 있습니다.

### 상수

const 키워드로 읽기 전용 상수를 만들 수 있습니다.

상수 식별자의 구문은 변수 식별자와 같습니다. 문자, 밑줄이나 달러 기호($)로 시작해야 하고 문자, 숫자나 밑줄을 포함할 수 있습니다.

상수는 스크립트가 실행 중인 동안 대입을 통해 값을 바꾸거나 재선언될 수 없습니다. 값으로 초기화해야 합니다.

상수에 대한 스코프 규칙은 let블록 스코프 변수와 동일합니다. 만약 const 키워드가 생략된 경우에는, 식별자는 변수를 나타내는 것으로 간주됩니다

상수는 같은 스코프에 있는 함수느 변수와 동일한 이름으로 선언할 수 없습니다.

```javascript
// 오류가 발생합니다
function f() {};
const f = 5;

// 역시 오류가 발생합니다
function f() {
  const g = 5;
  var g;

  //statements
}
```

그러나 상수에 할당된 객체의 속성은 보호되지 않아서 다음의 문은 문제없이 실행됩니다.

```javascript
const MY_OBJECT = {'key': 'value'};
MY_OBJECT.key = 'otherValue';
```

배열의 내용도 보호되지 않아서 다음의 문도 문제없이 실행됩니다.

```javascript
const MY_ARRAY = ['HTML','CSS'];
MY_ARRAY.push('JAVASCRIPT');
console.log(MY_ARRAY); //logs ['HTML','CSS','JAVASCRIPT'];
```

### 데이터 구조 및 형

데이터 형

- 7가지 원시 데이터 형
  1. Boolean. `true`와 `false`
  2. null. null 값을 나타내는 특별한 키워드. (JS는 대소문자를 구분하므로, null은 Null,NULL 혹은 다른 변형과도 다릅니다.)
  3. undefined. 값이 정의되어 있지 않은 최상위 속성
  4. Number. 정수 또는 실수형 숫자. 예:42 혹은 3.141592
  5. BigInt. 임의 정밀도의 정수. 예:9007199254740992n
  6. String. 문자열. 예:안녕
  7. Symbol. 인스턴스가 고유하고 불변인 데이터 형
- 그리고 Object

이러한 데이터 형이 비교적 많지 않지만, 애플리게이션에 유용한 기능을  수행할수 있습니다. 객체와 함수는 언어의 다른 기본 요소입니다. 객체는 값을 위한 컨테이너, 함수는 애플리케이션이 수행할 수 있는 절차로 생각할 수 있습니다.

### 자료형 변환

JS는 동적 형지정 언어입니다. 변수를 선언할 때 데이터 형을 지정할 필요가 없음을 의미합니다. 또한 데이터 형이 스크립트 실행 도중 필요에 의해 자동으로 변환됨을 뜻합니다.

그래서 예를 들어 다음과 같이 변수를 정의할 수 있습니다.

```javascript
var answer = 42;
```

그리고 나중에, 동일한 변수에 문자열 값을 할당할 수도 있습니다.

```javascript
answer = 'Thanks for all the fish...';
```

JS는 동적 형지정 언어이므로, 이 할당은 오류 메시지가 발생하지 않습니다.

### 숫자와 '+' 연산자

숫자와 문자열 값 사이에 + 연산자를 포함한 식에서, JS는 숫자 값을 문자열로 변환합니다. 예를 들어 아래와 같은 문이 있습니다.

```javascript
x = 'The answer is ' + 42 // "The answer is 42"
y = 42 + ' is the answer' // "42 is the answer"
'37' + 7 // "377"
```

다른 연산자를 포함한 식의 경우 JS는 숫자 값을 문자열로 반환하지 않습니다.

```javascript
'37' - 7 // 30
```

### 문자열을 숫자로 변환하기

숫자를 나타내는 값이 문자열로 메모리에 있는 경우 변환을 위한 메서드가 있습니다.

- [`parseInt()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
- [`parseFloat()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/parseFloat)

`parseInt`는 오직 정수만 반환하므로, 소수에서는 사용성이 떨어집니다.

**참고:** 게다가 `parseInt`를 잘 사용하기 위해서는 항상 진법(Radix) 매개변수를 포함해야 합니다. 진법 매개변수는 변환에 사용될 진법을 지정하는데 사용됩니다.

```javascript
parseInt('101', 2) // 5
```

문자열을 숫자로 변환하는 대안은 `+` (단항 더하기) 연산자입니다.

```js
'1.1' + '1.1' // '1.11.1'
(+'1.1') + (+'1.1') // 2.2
// 참고: 괄호는 명확성을 위해 추가, 필요한 것은 아닙니다.
```

### 리터럴

JS에서 값을 나타내기 위헤 리터럴을 사용합니다. 이는 말 그대로 스크립트에 부여한 고정 값으로 변수가 아닙니다. 이 구획에서는 다음과 같은 형태의 리터럴을 설명합니다.

- 배열 리터럴
- 불리언 리터럴
- 부동 소수점 리터럴
- 숫자 리터럴
- 객체 리터럴
- 정규식 리터럴
- 문자열 리터럴

### 배열 리터럴

배열 리터럴은 0개 이상의 식 목록입니다. 각 식은 배열 요소를 나타내고 대괄호[]로 묶입니다. 배열 리터럴을 사용하여 배열을 만들 때 그요소로 지정된 값으로 초기화 되고 그 length는 지정된 인수의 갯수로 설정됩니다.

아래 예제는 요소가 3개로 `length`가 3인 `coffees` 배열을 만듭니다.

```js
let coffees = ['French Roast', 'Colombian', 'Kona'];
```

배열이 최상단 스크립트에서 리터럴을 사용하여 만들어진 경우, JavaScript는 배열 리터럴을 포함한 식을 평가할 때마다 배열로 해석합니다. 게다가, 함수에서 사용되는 리터럴은 함수가 호출될 때마다 생성됩니다.

### 배열 리터럴의 추가 쉼표

배열 리터럴에서 모든 요소를 지정할 필요는 없습니다. 만약 잇달아 두 개의 쉼표를 두면, 배열은 지정되지 않은 요소를 `undefined`로 채웁니다. 다음 예제는 `fish` 배열을 만듭니다.

```js
let fish = ['Lion', , 'Angel'];
```

이 배열은 값이 있는 두 요소와 빈 요소 하나를 가집니다.

- `fish[0]`은 "Lion"
- `fish[1]`은 `undefined`
- `fish[2]`는 "Angel"

만약 요소 목록을 후행(trailing) 쉼표로 끝낸다면, 그 쉼표는 무시됩니다.

다음 예제에서, 배열의 `length`는 3입니다. `myList[3]`은 없습니다. 목록의 다른 모든 쉼표는 새로운 요소를 나타냅니다.

```js
var myList = ['home', , 'school', ];
```

아래 예제에서, 배열의 `length`는 4이며, `myList[0]`과 `myList[2]`는 값이 빠졌습니다.

```js
var myList = [ , 'home', , 'school'];
```

아래 예제에서, 배열의 `length`는 4이며, `myList[1]`과 `myList[3]`은 값이 빠졌습니다. **마지막 쉼표는 무시됩니다.**

```js
var myList = ['home', , 'school', , ];
```

추가 쉼표의 동작을 이해하는 것은 JavaScript를 언어로서 이해하는데 중요합니다.

하지만 코드를 작성할 때는 빠진 요소의 값을 명시적으로 `undefined`로 선언하는 것이 코드의 명확성과 유지보수성을 높입니다.

### 불리언 리터럴

불리언 형은 `true`와 `false`의 리터럴 값을 가집니다.

### 숫자 리터럴

JavaScript 숫자 리터럴은 다른 진법의 정수 리터럴과 10진수의 부동 소수점 리터럴이 포함됩니다.

언어 명세서에 따르면 숫자 리터럴에 부호가 없어야 합니다. 그럼에도 불구하고, `-123.4` 와 같은 코드 괜찮습니다. 숫자 리터럴 `123.4` 에 단항 연산자 `-` 가 붙은 것으로 해석됩니다.

### 정수 리터럴

정수와 [`BigInt`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/BigInt) 리터럴은 10진수, 16진수, 8진수 및 2진수로 표현될 수 있습니다

- 10진수 정수 리터럴은 `0`으로 시작(leading zero)하지 않는 숫자열로 이루어집니다.
- 정수 리터럴에서 `0`으로 시작하거나 `0o`(혹은 `0O`)으로 시작하는 숫자열은 8진수임을 나타냅니다. 8진수 정수 리터럴은 오직 숫자 `0`-`7`만 포함할 수 있습니다.
- `0x`(나 `0X`)로 시작하는 숫자열은 16진수 정수 리터럴 임을 나타냅니다. 16진수 정수는 숫자 (`0`-`9`) 및 문자 `a`-`f`, `A`-`F`를 포함할 수 있습니다. (문자의 대소문자는 그 값을 변경하지 않습니다. 그러므로 `0xa` = `0xA` = `10` 그리고 `0xf` = `0xF` = `15` 입니다.)
- `0b` (나 `0B`)로 시작하는 숫자열은 2진수 정수 리터럴 임을 나타냅니다. 2진수 정수 리터럴은 오직 숫자 `0`과 `1`만 포함할 수 있습니다.
- `n`으로 끝나는 숫자열은 [`BigInt`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/BigInt) 리터럴 임을 나타냅니다. 정수 리터럴은 위의 어떤 진수든 사용할 수 있습니다. `0123n`과 같은 `0`으로 시작하는 8진수 구문은 허용되지 않으나, `0o123n`은 허용됩니다.

```js
0, 117, 123456789123456789n             (10진수)
015, 0001, 0o777777777777n              (8진수)
0x1123, 0x00111, 0x123456789ABCDEFn     (16진수)
0b11, 0b0011, 0b11101001010101010101n   (2진수)
```

### 부동 소수점 리터럴

부동 소수점 리터럴은 아래와 같은 부분으로 이루어집니다.

- 부호없는 10진 정수,
- 소수점 ("`.`"),
- 소수 (또 다른 10진수),
- 지수.

지수부는 "`e`"나 "`E`" 다음에 오며 부호("`+`"나 "`-`")가 달릴 수 있는 정수입니다. 부동 소수점 리터럴은 적어도 숫자 하나와 소수점 혹은 "`e`"(나 "`E`")가 있어야 합니다.

```
[digits].[digits][(E|e)[(+|-)]digits]
```

```
3.1415926
.123456789
3.1E+12
.1e-23
```

### 객체 리터럴

객체 리터럴은 중괄호(`{}`)로 묶인 0개 이상인 객체의 속성명과 관련 값 쌍 목록입니다.

아래는 객체 리터럴의 예제입니다. car 객체의 첫째 요소는 myCar 속성을 정의하고 문자열 Saturn을 할당합니다. 반면 둘째 요소인 getCar 속성은 함수 (carTypes('Honda'))을 호출한 결과가 즉시 할당됩니다. 셋쩨 요소 spqcial 속성은 기존 변수 sales를 사용합니다.

```js
var sales = 'Toyota';

function carTypes(name) {
  if (name === 'Honda') {
    return name;
  } else {
    return "Sorry, we don't sell " + name + ".";
  }
}

var car = { myCar: 'Saturn', getCar: carTypes('Honda'), special: sales };

console.log(car.myCar);   // Saturn
console.log(car.getCar);  // Honda
console.log(car.special); // Toyota
```

속성명으로 숫자나 문자열 리터럴을 사용하거나 또다른 객체 리터럴 내부에 객체를 중첩할 수도 있습니다. 아래 예제는 이 옵션을 사용합니다.

```js
var car = { manyCars: {a: 'Saab', b: 'Jeep'}, 7: 'Mazda' };

console.log(car.manyCars.b); // Jeep
console.log(car[7]); // Mazda
```

객체 속성명은 빈 문자열 포함 어떤 문자열도 될 수 있습니다. 속성명이 유효한 JS 식별자나 숫자가 아닌 경우 따옴표로 묶여야 합니다.

또한 유효한 식별자가 아닌 속성명은 점(.) 속성으로 접근할 수 없습니다. 대신 배열 같은 표기법('[]')으로 접근하고 값을 설정할 수 있습니다.

```js
var unusualPropertyNames = {
  '': 'An empty string',
  '!': 'Bang!'
}
console.log(unusualPropertyNames.'');   // SyntaxError: Unexpected string
console.log(unusualPropertyNames['']);  // An empty string
console.log(unusualPropertyNames.!);    // SyntaxError: Unexpected token !
console.log(unusualPropertyNames['!']); // Bang!
```

### 향상된 객체 리터럴??

### 정규식 리터럴

정규식 리터럴은 슬래시 사이에 감싸인 패턴입니다. 다음은 정규식 리터럴 예제입니다.

```js
var re = /ab+c/;
```

### 문자열 리터럴

문자열 리터럴은 큰 따옴표 혹은 작은 따옴표로 묶인 0개 이상의 문자입니다. 문자열은 같은 형 따옴표 (즉 큰 따옴표 쌍이나 작은 따옴표 쌍 ) 로 구분되어야 합니다.

```js
'foo'
"bar"
'1234'
'one line \n another line'
"John's cat"
```

꼭 `String` 객체를 사용할 필요가 없는 경우 문자열 리터럴을 사용해야 합니다. `String` 객체에 대해 자세한 사항은 [`String`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String)을 참고하세요.

문자열 리터럴 값은 String 객체의 모든 메서드를 호출할 수 있습니다. JS는 자동으로 문자열 리터럴을 임시 문자열 객체로 변환, 메서드를 호출하고 나서 임시 문자열 객체를 폐끼합니다. 또한 문자열 리터럴에서도 String.length 속성을 사용할 수 있습니다.

```js
// 공백을 포함한 문자열 내 심볼 갯수가 출력됩니다.
console.log("John's cat".length)// 여기서는, 10.
```

템플릿 리터럴도 사용할 수 있습니다. 템플릿 리터럴은 큰 따옴표나 작은 따옴표 대신 백틱(`) 으로 문자를 감쌉니다.

```js
// 기본적인 문자열 리터럴 생성
`In JavaScript '\n' is a line-feed.`

// 여러 줄 문자열
`In JavaScript, template strings can run
 over multiple lines, but double and single
 quoted strings cannot.`

// 문자열 삽입
var name = 'Bob', time = 'today';
`Hello ${name}, how are you ${time}?`
```

Tagged templates은 구문 분석을 위한 태그 함수에 대한 호출과 함께 템플릿 리터럴을 지정하기 위한 간결한 구문입니다. 템플릿 태그 함수의 이름은 아래 예제에서 myTag가 템플릿 태그 함수 이름인 것과 같이 템플릿 리터럴 앞에 옵니다.

```js
let myTag = (str, name, age) => `${str[0]}${name}${str[1]}${age}${str[2]}`;
let [name, age] = ['Mika', 28];
myTag`Participant "${ name }" is ${ age } years old.`;
// Participant "Mika" is 28 years old.
```

### 문자열에서 특수 문자 사용

보통 문자에 더해서 문자열에 아래 예제와 같이 특수 문자도 포함할 수 있습니다.

```js
'one line \n another line'
```

다음 표는 JS문자열에 사용할 수 있는 특수 문자 목록입니다.

| 문자          | 뜻                                                           |
| :------------ | :----------------------------------------------------------- |
| `\0`          | Null Byte                                                    |
| `\b`          | Backspace                                                    |
| `\f`          | Form feed                                                    |
| `\n`          | New line                                                     |
| `\r`          | Carriage return                                              |
| `\t`          | Tab                                                          |
| `\v`          | Vertical tab                                                 |
| `\'`          | Apostrophe 혹은 작은 따옴표                                  |
| `\"`          | 큰 따옴표                                                    |
| `\\`          | 백슬래시                                                     |
| `\*XXX*`      | Latin-1 인코딩 문자는 `0` - `377` 사이 8진수 3자리 *XXX*까지 지정될 수 있습니다. 예를 들어, `\251`은 copyright 심볼을 표현하는 8진수 시퀀스입니다. |
| `\x*XX*`      | Latin-1 인코딩 문자는 `00` - `FF` 사이의 16진수 2자리 *XX*로 지정될 수 있습니다. 예를 들어, `\xA9`는 copyright 심볼을 표현하는 16진수 시퀀스입니다. |
| `\u*XXXX*`    | 유니코드 문자는 16진수 4자리 *XXXX*로 지정될 수 있습니다. 예를 들어, `\u00A9`는 copyright 심볼을 표현하는 유니코드 시퀀스입니다. [Unicode escape sequences](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Lexical_grammar#string_literals)를 참고하세요. |
| `\u*{XXXXX}*` | 유니코드 코드 포인트 이스케이프. 예를 들어, `\u{2F804}`는 간단한 유니코드 이스케이프 `\uD87E\uDC04`와 같습니다. |