# 템플릿 리터럴 (Template literal)

ES6부터 템플릿 리터럴(Template literal)이라고 불리는 새로운 문자열 표기법을 도입하였다. 템플릿 리터럴은 ‘ 또는 “ 같은 통상적인 따옴표 문자 대신 백틱(backtick) 문자 `를 사용한다.

## 멀티라인 문자열

일반 문자열에서는 줄바꿈(개행)이 허용되지 않는다.

```js
const template = '<ul>\n\t<li><a href="#">Home</a></li>\n</ul>';

console.log(template);
```

일반적인 문자열에서 줄바꿈은 허용되지 않으며 공백(white-space)를 표현하기 위해서는 백슬래시(\)로 시작하는 이스케이프 시퀀스(Escape Sequence)를 사용하여야 한다.

템플릿 리터럴은 일반적인 문자열과 달리 여러 줄에 걸쳐 문자열을 작성할 수 있으며 템플릿 리터럴 내의 모든 white-space는 있는 그대로 적용된다.

```js
const template = `<ul class="nav-items">
  <li><a href="#home">Home</a></li>
</ul>`;

console.log(template);
```

```html
<!-- 결과값 -->
<ul class="nav-items">
  <li><a href="#home">Home</a></li>
</ul>
```

## 표현식 삽입 (String Interpolation)

템플릿 리터럴은 + 연산자를 사용하지 않아도 간단한 방법으로 새로운 문자열을 삽입할 수 있는 기능을 제공한다. 이를 문자열 인터폴레이션(String Interpolation)이라 한다.

```js
const first = "Ung-mo";
const last = "Lee";

// ES6: String Interpolation
console.log(`My name is ${first} ${last}.`);
// "My name is Ung-mo Lee."

// ES5: 문자열 연결
console.log("My name is " + first + " " + last + ".");
// "My name is Ung-mo Lee."
```

문자열 인터폴레이션은 ${ … }으로 표현식을 감싼다. 문자열 인터폴레이션 내의 표현식은 문자열로 타입이 강제로 변환되어 삽입된다.

```js
// ES6: String Interpolation
console.log(`1+2=${1 + 2}`); // 1 + 2 = 3

// ES5: 일반 문자열에서의 표현식 삽입은 문자열로 취급
console.log("1+2=${1 + 2}"); // 1 + 2 = ${1 + 2}
```
