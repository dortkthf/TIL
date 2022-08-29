# HTML 태그및 속성 정리

## 목차

- [**< a > 태그**](# <-a->)
  - [href 속성](# href)
  - [download 속성](# download)
  - [ping 속성](# ping)
  - [rel 속성](# rel)
  - [target 속성](# target)
  - [type 속성](# type)
- [**< abbr > 태그**](# <-abbr->)

# < a > 

HTML < a > 요소(앵커 요소)는 `href` 특성을 통해 다른 페이지나 같은 페이지의 어느 위치, 파일 이메일 주소와 그 외 다른 URL로 연결할 수 있는 하이퍼링크를 만듭니다. `<a>` 안의 콘텐츠는 링크 목적지의 설명을 나타내야 합니다.

 ## 특성

#### `href`

하이퍼링크가 가리키는 URL. 링크는 HRRP 기반 URL 일 필요는 없고, 브라우저가 지원하는 모든 URL 스킴을 사용할 수 있습니다.

- 페이지 구획을 가리키는 프래그먼트 URL
- 미디어 파일 일부를 가리키는 미디어 프래그먼트
- `tel:` URL을 사용하는 전화번호
- `mailto: `URL을 사용하는 메일주소
- 웹 브라우저는 다른 URL 스킴을 지원하지 않지만, 웹사이트는 `Navigator.registerProtocolHandler()`를 통해 지원할수 있습니다.

#### `download`

링크로 이동하는 대신 사용자에게 URL을 저장할지 물어봅니다. 값을 지정할 수도 있고, 지정하지 않을 수도 있습니다.

- 값이 없으면 파일 이름과 확장자는 브라우저가 다양한 인자로부터 생성해 제안합니다.
- 값을 지정하면 저장할 때의 파일 이름으로서 제안합니다. `/`와`\`문자는 `_`로 변환합니다. 파일 시스템에서 다른 문자도 제한 할수 있으므로, 필요한 경우 브라우저가 추가로 이름을 조정할 수 있습니다.

#### `ping`

하나의 스페이스로 구분하는 URL 목록, 링크를 클릭해 따라갈 경우, 브라우저가 URL 각각에 POST 요청을 전송합니다. 대개 추적 용도로 사용합니다.

#### `rel`

하나의 스페이스로 구분하는, 연결한 URL과의 관계를 나타내는 링크 유형 목록

![image-20220829164616805](HTML_요소정리.assets/image-20220829164616805.png)

#### `target`

링크한 URL을 표시할 위치. 기능한 값은 브라우징 맥락으로, 즉 탭,창,`<iframe>`의 이름이나 특정 키워드입니다. 다음 키워드는 특별한 뜻을 가지고 있습니다.

- _self : URL을 현재 브라우징 맥락에 표시합니다. 기본값.
- _blank : URL을 새로운 브라우징 맥락에 표시합니다. 보통 새 탭이지만, 사용자가 브라우저 설정을 통해 새 창으로 바꿀 수 있습니다.
- _parent : URL을 현재 브라우징 맥락의 부모에 표시합니다. 부모가 존재하지 않으면 _self와 동일하게 행동합니다.
- _top : URL을 최상단 브라우징 맥락(현재 맥락의 부모면서 자신의 부모가 존재하지 않는, 제일 높은 맥락)에 표시합니다. 부모가 존재하지 않으면 _self 와 동일하게 행동합니다.

참고

- target 을 사용할 때, `rel="noreferrer"`를 추가해 `window.opener`API의 악의적인 사용을 방지하는걸 고려하세요.

- 최근의 브라우저에서는 target='_blank'를 지정하면 `rel="noopener"`를 적용한 것과 같은 동작을 합니다.

#### `type`

링크 URL의 MIME type에 대한 힌트. 특별한 내장 기능은 없습니다.

*MIME type은 파일의 형식을 나타내는 문자열로 파일과 같이 송신되는데 content의 형식을 나타내기 위해 사용한다. 

# < abbr >

HTML `<abbr>`요소는 준말 또는 머리글자를 나타냅니다. 선택 속성인 `title`을 사용하면 준말의 전체 뜻이나 설명을 제공할 수 있습니다. `title`속성은 전체 설명만을 가져야 하며 다른건 포함할 수 없습니다.

## 특성

`<abbr>` 요소에서의 `title` 특성은 특정한 의미를 가지며, `title`은 준말에 대한 설명 혹은 확장형태를 사람이 읽을 수 있는 형태를 값으로 가져야 합니다. 브라우저는 `title`의 값을 보통 마우스 커서를 올렸을 때 나타나는 툴팁으로 보여줍니다.

각각의 `<abbr>`요소는 서로 독립적입니다. 하나의 요소에 `title`을 제공한다고 나머지에 지정하지 않아도 되는것은 아닙니다.

## 기본 스타일

`<abbr>`의 목적은 오로지 HTML 작성자의 편리함을 위함이며, 모든 브라우저는 기본적으로 인라인으로 렌더링 합니다. 그러나 기본 스타일은 브라우저마다 다를 수 있습니다.

## 예제

**준말임을 나타내기**

설명 없이, 단순히 특정 단어가 준말임을 나타내기만 하고자 하면 `<abbr>`을 다른 특성 없이 사용하세요.

HTML

```python
<p>Using <abbr>HTML</abbr> is fun and easy!</p>
```

결과

![image-20220829174039942](HTML_요소정리.assets/image-20220829174039942.png)

**펼친 형태 보여주기**

`title`특성을 사용하면 준말과 머리글자를 펼친 원래 형태를 보여줄 수 있습니다.

HTML

```html
<p>Ashok's joke made me <abbr title="Laugh Out Loud">LOL</abbr> big
time.</p>
```

결과

![image-20220829174146415](HTML_요소정리.assets/image-20220829174146415.png)

**준말 정의하기**

`<abbr>`과 `<dfn>`을 사용하면 준말을 정식으로 정의할 수 있습니다.

HTML

```html
<p><dfn id="html"><abbr title="HyperText Markup Language">HTML</abbr>
</dfn> is a markup language used to create the semantics and structure
of a web page.</p>

<p>A <dfn id="spec">Specification</dfn>
(<abbr title="Specification">spec</abbr>) is a document that outlines
in detail how a technology or API is intended to function and how it is
accessed.</p>
```

결과

![image-20220829174347728](HTML_요소정리.assets/image-20220829174347728.png)

## 접근성 고려사항

준말과 머리글자가 처음 사용될 때, 그 뜻을 풀어 설명하면 독자가 문서를 이해하기 쉬워집니다. 특히 콘텐츠가 기술이나 산업에 관련된 전문적인 내용인 경우 더욱 그렇습니다.