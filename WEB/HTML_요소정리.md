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
- [**< address > 태그**](# <-address->)
- [**< area >**](# <-area->)

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

# < address >

HTML `<address>`요소는 가까운 HTML 요소의 사람, 단체, 조직 등에 대한 연락처 정보를 나타냅니다.

`<address>`요소의 콘텐츠가 제공하는 연락처 정보는 현재 맥락에 적절한 아무 형태나 취할수 있으며, 물리적 주소, URL, 이메일 주소, 전화번호, SNS 식별자, 좌표 등 어떠한 정보라도 포함할 수 있습니다. 반드시 포함해야 하는 정보는 연락처가 가리키는 개인, 조직, 단체의 이름입니다.

`<address>`는 다양한 맥락에서 사용할 수 있습니다. 사업체 연락 방법을 페이지 헤더에 배치할 때도 쓸 수 있고,`<article>`내부에 배치해서 글의 작성자를 나타낼 수도 있습니다.

**예제**

```html
<address>
  You can contact author at <a href="http://www.somedomain.com/contact">
  www.somedomain.com</a>.<br>
  If you see any bugs, please <a href="mailto:webmaster@somedomain.com">
  contact webmaster</a>.<br>
  You may also want to visit us:<br>
  Mozilla Foundation<br>
  331 E Evelyn Ave<br>
  Mountain View, CA 94041<br>
  USA
</address>
```

**결과**

*You can contact author at* [www.somedomain.com](http://www.somedomain.com/contact)*.*
*If you see any bugs, please* [contact webmaster](mailto:webmaster@somedomain.com)*.*
*You may also want to visit us:*
*Mozilla Foundation*
*331 E Evelyn Ave*
*Mountain View, CA 94041*
*USA*

비록 겉보기는 `<i>` 나 `<em>` 요소와 같지만, `<address>` 요소는 자체적인 의미를 갖고 있으므로 연락처 표기에는 `<address>`가 더 적합합니다.

# < area >

HTML `<area>`요소는 이미지의 핫스팟 영역을 정의하고 하이퍼링크를 `<map>`요소 안에서만 사용할 수 있습니다.

**예제**

```html
<map name="infographic">
    <area shape="rect" coords="184,6,253,27"
          href="https://mozilla.org"
          target="_blank" alt="Mozilla" />
    <area shape="circle" coords="130,136,60"
          href="https://developer.mozilla.org/"
          target="_blank" alt="MDN" />
    <area shape="poly" coords="130,6,253,96,223,106,130,39"
          href="https://developer.mozilla.org/docs/Web/Guide/Graphics"
          target="_blank" alt="Graphics" />
    <area shape="poly" coords="253,96,207,241,189,217,223,103"
          href="https://developer.mozilla.org/docs/Web/HTML"
          target="_blank" alt="HTML" />
    <area shape="poly" coords="207,241,54,241,72,217,189,217"
          href="https://developer.mozilla.org/docs/Web/JavaScript"
          target="_blank" alt="JavaScript" />
    <area shape="poly" coords="54,241,6,97,36,107,72,217"
          href="https://developer.mozilla.org/docs/Web/API"
          target="_blank" alt="Web APIs" />
    <area shape="poly" coords="6,97,130,6,130,39,36,107"
          href="https://developer.mozilla.org/docs/Web/CSS"
          target="_blank" alt="CSS" />
</map>
<img usemap="#infographic" src="/media/examples/mdn-info.png" alt="MDN infographic" />
```

**결과**

![MDN infographic](https://interactive-examples.mdn.mozilla.net/media/examples/mdn-info.png)

**특성**

#### `alt`

이미지를 출력하지 않는 브라우저에서 대신 표시할 대안 텍스트입니다. 텍스트의 내용은 대안 텍스트 없이 이미지만 표시할 때와 동일한 수준의 선택지를 나타낼 수 있어야 합니다. `href`특성이 존재할 경우 필수 사항입니다.

#### `coords`

핫스팟 영역을 지정하는 일련의 좌표입니다. 값의 수와 의미는 `shape`특성의 값에 따라 달라집니다.

- `rect`: 좌상단과 우하단을 나타내는 두 개의 x, y 쌍입니다.
- `circle`: `x,y,r`로서 `x,y`는 원의 중심 좌표이며 `r`은 반지름 입니다.
- `poly`: 다각형의 꼭지점을 나타내는 다수의 x, y 쌍 (x1,y1,x2,y2,x3,y3,...) 입니다.

값의 단위는 CSS 픽셀입니다.

#### `download`

특성이 존재할 경우, 이 하이퍼링크는 리소스 다운로드 용도로 사용하는 것을 의도했음을 나타냅니다.

#### `href`

`<area>` 하이퍼링크의 대상입니다. 유효한 URL이야 합니다. 생략할 경우, 이`<area>`요소는 하이퍼링크를 나타내지 않습니다.

#### `ping`

하이퍼링크를 따라갈 때. 백그라운드에서 브라우저가 POST요청을 본문 `PING`으로 전성할 URL의 목록입니다. 공백으로 구분하며 주로 추적용으로 사용합니다.

#### `shape`

지정할 스팟의 모양을 정합니다. `rect`, `circle`, `poly` 가 있습니다.

#### `target`

이 속성은 링크된 리소스가 어디에 표시될지 지정합니다.

- _self : 결과를 현재 HTML4 프레임 또는 HTML5 브라우징 컨텍스트에 로드합니다.  이 target속성이 정의되어있지 않은경우 이 값이 기본값이 됩니다.
- _blank: 결과를 이름없는 새로운 HTML4 윈도우나 HTML5 브라우징 컨텍스트에 로드합니다.
- _parent: 결과를 현재 HTML4 프레임의 부모 프레임셋에 로드하거나 부모 HTML5 브라우징 컨텍스트에 로드합니다. 만약 부모가 없을경우 _self와 동일하게 여겨집니다.
- _top: HTML4 에서는, 다른 모든 프레임을 취소하고 결과를 꽉찬 본래의 윈도우에 로드합니다. HTML5에서는, 결과를 최상위 브라우징 컨텍스트에 로드합니다. 만약 부모가 없다면 이 옵션은 _self와 같이 행동합니다. 

이 속성은 href속성이 존재할때만 사용합니다.
