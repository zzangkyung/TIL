# this

## this 키워드

this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(self-referencing variable)이다.
this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.

### 객체 리터럴

```js
const circle = {
    radius = 5,
    getDiameter() {
        // this는 메서드를 호출한 객체를 가리킨다.
        return 2 * this.radius;
    }
};

console.log(circle.getDiameter()); //10
```

객체 리터럴의 메서트 내부에서의 this는 메서드를 호출한 객체, circle을 가리킨다.

### 생성자 함수

```js
function Circle(radius) {
    // this는 생성자 함수가 생성할 인스턴스를 가리킨다.
    this.radius. = radius;
};

Circle.prototype.getDiameter = fuction() {
    // this는 생성자 함수가 생성할 인스턴스를 가리킨다.
    return 2 * this.radius;
};

const circle = new Circle(5);
console.log(circle.getDiameter()); // 10
```

생성자 함수 내부의 this는 생성자 함수가 생성할 인스턴스를 가리킨다. 상황에따라 가리키는 대상이 다르다.

## 함수 호출 방식과 this 바인딩

this 바인딩(this에 바인딩될 값)은 함수가 어떻게 호출되었는지에 따라 동적으로 결정된다.

- 함수의 상위 스코프를 결정하는 방식인 렉시컬 스코프(Lexical scope)는 함수를 선언할 때 결정된다. 렉시컬 스코프와 this 바인딩은 결정 시기가 다르다. (this 바인딩과 혼동하지 않도록 주의)

### 함수 호출 방식

1. 일반 함수 호출
2. 메소드 호출
3. 생성자 함수 호출
4. Function.prototype.apply/call/bind 메소드에 의한 간접 호출

## 1. 일반 함수 호출

전역객체(Global Object)는 모든 객체의 유일한 최상위 객체를 의미하며 일반적으로 Browser-side에서는 window, Server-side(Node.js)에서는 global 객체를 의미한다.

```js
// in browser console
this === window; // true

// in Terminal (Node.js)
this === global; // true
```

전역객체는 전역 스코프(Global Scope)를 갖는 전역변수(Global variable)를 프로퍼티로 소유한다. 글로벌 영역에 선언한 함수는 전역객체의 프로퍼티로 접근할 수 있는 전역 변수의 메소드이다.

```js
function foo() {
  console.log("foo's this: ", this); // window
  function bar() {
    console.log("bar's this: ", this); // window
  }
  bar();
}
foo();
```

기본적으로 this는 전역객체(Global object)에 바인딩된다. 전역함수는 물론이고 심지어 내부함수의 경우도 this는 외부함수가 아닌 전역객체에 바인딩된다.
