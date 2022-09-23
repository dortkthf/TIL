# 제어 흐름과 오류 처리

JS 는 애플리케이션에 다양한 상호작용을 추가하기 위한 일련의 명령문, 특히 제어 흐름 명령문을 지원합니다.

### 블록문

가장 기본적인 명령문은, 명령문들을 그룹으로 묶을 수 있는 블록문 입니다. 블록문의 블록은 한 쌍의 중괄호로 감싼느 것으로 나타냅니다.

```js
{
  statement_1;
  statement_2;
  ⋮
  statement_n;
}
```

블록문은 제어 프름 명령문과 많이 사용합니다. (if, for, while)

```js
while (x < 10) {
  x++;
}
```

여기서 `{x++;}`가 블록문 입니다.

### 조건문

조건문은 지정한 조건이 참인 경우에 실행하는 명령 집합입니다. JS는 `if...else`와 `switch` 두 종류의 조건문을 지원합니다.

`if...else`문

명령문을 논리 조건이 참일 때 실행하려면 `if` 문을 사용하세요. 선택적으로, `else` 절을 추가해서 조건이 거짓인 경우에 실행할 명령문을 지정할 수 있습니다.

`if` 문의 형태는 다음과 같습니다.

```js
if (condition) {
    statement_1;
} else {
    statement_2;
}
```

위 코드에서, `condition`에는 `true`나 `false`로 평가할 수 있는 아무 표현식이나 대입할 수 있습니다.

`condition`이 `true`로 평가되면 `statement_1`을 실행합니다. 그렇지 않으면 `statement_2`를 실행합니다. `statement_1`과 `statement_2`에는 다른 `if` 문을 포함해 아무 명령문이나 사용할 수 있습니다.

`else if`를 사용해서 다수의 조건을 순차적으로 검사할 수도 있습니다.

```js 
if (condition_1) {
	statement_1;
} else if (conditiond_2) {
    statemend_2;
} else if (condition_n) {
    statement_n;
} else {
    statement_last;
}
```

이 경우, 처음으로 `true`로 평가되는 조건의 명령문들만 실행됩니다.

### 거짓 값

다음 값은 `false`로 평가됩니다.

- `false`
- `undefined`
- `null`
- `0`
- `NaN`
- 빈 문자열 (`""`)

객체를 포함해 다른 모든 값은 조건문에 전달했을 때 `true`로 평가됩니다.

### 예제

다음 예제에서, 함수 `checkData`는 `Text` 객체에 포함된 문자의 수가 3이면 `true`를 반환합니다. 그렇지 않으면 경고를 표시한 후 `false`를 반환합니다.

```js
function checkData() {
    if (document.form1.threeChar.value.length == 3) {
        return true;
    } else {
        alert(
        	'정확히 세 글자를 입력하세요. ' +
            '${document.form1.threeChar.value}은(는) 유효하지 않습니다.');
        return false;
    }
}
```

### `switch`문

`switch`문은 프로그램이 표현식을 평가한 후, 그 값과 `case` 레이블의 값을 비교해 일치하는 `case`의 명령문을 실행합니다.

`switch`문의 모습은 다음과 같습니다.

```js
switch (expression) {
    case label_1:
        statements_1;
        break;
    case label_2:
        statements_2;
        break;
        ...
        default:
        statements_default;
}
```

JS는 위의 `switch`문을 다음의 과정으로 평가합니다.

- 우선 표현식(expression)의 결과와 일치하는 레이블을 가진 `case` 절을 찾아, 관련된 명령문을 실행합니다.
- 일치하는 레이블을 찾지 못했으면 `default` 절을 탐색합니다.
  - `default`절을 찾았으면 관련된 명령문을 실행합니다.
  - `default`절을 찾지 못했으면 `switch`문 바깥의 다음 명령문을 실행합니다.
  - (`default`를 마지막에 배치하는 것은 관습적인 것으로, 사실 위치는 상관 없습니다.)

### break 문

각각의 `case`에는 선택적으로 `break`문을 추가할 수 있습니다. `break`는 `case`의 명령문을 실행한 후에 프로그램이 `switch`의 밖으로 나가도록 합니다.`break`를 생략하면 프로그램은 `switch`문을 탈출하지 않고, 다음 `case`의 명령문을 실행합니다.

### 예제

이 예제에서는 `fruitType`이 `'바나나'`라면 `'바나나'`레이블을 가진 `case`의 명령문을 실행합니다. `break`를 마주치면 프로그램이 `switch`밖으로 나가서 바로 다음 명령문을 실행합니다. `'바나나'`에 `break`가 없었다면 `case '체리'`아래의 명령문도 실행했을 것입니다.

```js
switch (fruittype) {
  case '오렌지':
    console.log('오렌지는 파운드 당 $0.59입니다.');
    break;
  case '사과':
    console.log('사과는 파운드 당 $0.32입니다.');
    break;
  case '바나나':
    console.log('바나나는 파운드 당 $0.48입니다.');
    break;
  case '체리':
    console.log('체리는 파운드 당 $3.00입니다.');
    break;
  case '망고':
    console.log('망고는 파운드 당 $0.56입니다.');
    break;
  case '파파야':
    console.log('망고와 파파야는 파운드 당 $2.79입니다.');
    break;
  default:
    console.log(`죄송합니다. ${fruitType}은 품절입니다.`);
}
console.log('더 필요한게 있으신가요?');
```

### 예외 처리 명령문

`throw`문을 사용하면 예외를 던질 수 있고, 던진 예외는 `try...catch`문으로 처리할 수 있습니다.

- `throw`문
- `try...catch`문

### 예외 유형

JS 에서는 모든 것을 `throw`로 던질 수 있습니다. 그래서 숫자나 문자열을 오류로 던지는 경우도 많지만, 예외를 나타내기 위해 사전에 정의된 예외 유형을 쓰는 것이 보통 더 효과적입니다.

- ECAMAScript예외
- DOMException (en-US), DOMError (en-US)

`throw` 문

예외를 던질 땐 `throw`문을 사용하세요. `throw`에 던질 값을 지정하면 됩니다.

```js
throw expression;
```

특정 타입의 표현식이 아니라 무엇이든 던질 수 있습니다. 아래 코드에서 다양한 타입을 예외로 던지는 모습을 볼 수 있습니다.

```js
throw 'Error2'; //String
throw 42; // Number
throw true; // Boolean
throw {
    toString: function () {
        return '저는 객체예요';
    },
};
```

`try..catch` 문

`try...catch` 문은 실행을 시도할 블록을 표시하고, 그 안에서 예외가 발생할 경우 처리를 맡을 하나 이상의 반응 명령문을 지정합니다. 예외가 발생하면, `try...catch` 문이 잡아냅니다.

`try...catch`문은 하나 이상의 명령문을 포함하는 `try` 블록, 그리고 `try` 에서 예외가 발생할 경우 그 예외를 처리할 명령문을 담은 하나의 `catch`블록으로 구성합니다.

다르게 설명해보면, `try...catch`는 성공하길 바라는 코드(`try` 블록)가 만약 실패하면 `catch`로 제어권을 넘겨야 할 때 사용합니다. `try` 블록의 명령문 중 하나에서 예외를 던지면, 실행 제어권은 그 즉시 `catch`블록으로 넘어갑니다. `try` 블록 내에서 예외가 발생하지 않았으면 `catch`블록은 실행되지 않습니다.

다음은 `try...catch`의 사용 모습을 보이는 예제입니다. `getMonthName()`은 매개변수의 값을 사용해 `months`배열에서 영어 월 이름을 가져옵니다. 그런데 유효한 월(`1`-`12`)범위의 숫자 값을 받은 것이 아니라면 `'InvalidMonthNo'`를 값으로 한 예외를 던집니다. 그러면 `catch`블록의 명령문이 `monthName`변수를 `'unknown'`으로 설정합니다.

```js
function getMonthName(mo) {
  mo = mo - 1; // 배열 인덱스에 맞춰 월 조절 (1 = Jan, 12 = Dec)
  let months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
  if (months[mo]) {
    return months[mo];
  } else {
    throw 'InvalidMonthNo'; // 여기서 throw 키워드 사용
  }
}

try {
  // 시도할 명령문
  monthName = getMonthName(myMonth); // 예외가 발생할 수 있는 함수
} catch (e) {
  monthName = 'unknown';
  logMyErrors(e); // 오류 처리기에 예외 객체 전달
}
```

`catch` 블록

`try`블록에서 발생할 수 있는 모든 예외는 `catch`블록에서 처리할 수 있습니다.

```js
catch (catchID) {
  statements;
}
```

`catch`블록은 `throw`명령문이 던진 예외의 값을 담을 식별자(위 코드 블록에서는 `catchID`)를 지정합니다. 이 식별자를 통해, 발생한 예외의 정보를 알아낼 수 있습니다.

JS는 `catch`블록에 진입해야 예외의 식별자를 생성하고, `catch`블록의 밖으로 나가면 식별자를 더 이상 유지하지 않습니다. 즉, `catch` 블록의 실행이 끝나면 예외 식별자에 접근할 수 없습니다.

아래는 예외를 던지고 잡는 예제 코드입니다. 예외를 던지면 그 순간 제어권이 `catch`블록으로 넘어갑니다.

```
try {
  throw 'myException'; // 예외 생성
} catch (e) {
  // 모든 예외를 처리하기 위한 명령문
  logMyErrors(e); // 오류 처리기에 예외 객체 전달
}
```