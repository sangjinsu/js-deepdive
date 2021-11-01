# 타입 변환과 단축 평가

### 타입 변환

- 개발자 의도에 따라 다른 타입으로 변환할 수 있다
  - 명시적 타입 변환
  - 타입 캐스팅 

- 자바스크립트 엔진에 의해 암묵적으로 변환한다
  - 암묵적 타입 변환
  - 타입 강제 변환 

### Falsy 값

- false
- undefined
- null
- 0, -0
- NaN
- ' ' (빈 문자열)

### 단축 평가

- 논리 연산의 결과를 결정하는 피연산자를 타입변환 하지 않고 그대로 반환 한다

- 표현식을 평가하는 도웆ㅇ에 평가 결과가 한정된 경우 나머지 평가 과정을 생략하는 것을 말한다 

  | 단축 평가 표현식    | 평가 결과 |
  | ------------------- | --------- |
  | true \|\| anything  | true      |
  | false \|\| anything | anything  |
  | true && anything    | anything  |
  | flase && anything   | false     |

#### 객체를 가리키기를 기대하는 변수가 null  또는 undefined 가 아닌지 확인하고 프로퍼티를 참조할 때

```js
var elem = null;
var value = elem.value // => TypeError
```

```js
var elem = null;
var value = elem && elem.value // null
```

### 옵셔널 체이닝 연산자

- ES11
- `?.` 는 좌항의 피연산자가 null 또는 undefined 인 경우 undefined 를 반환하고 그렇지 않으면 우항의 프로퍼티 참조를 이어간다 

```js
var elem = null

var value = elem?.value
console.log(value) // undefined 
```

- 논리 연산자 && 는 좌항 피연산자가 Falsy 값이면 좌항 피연산자를 그대로 반환한다. 
- 좌항 연산자가 Falsy  값인 0이나 `''` 인 경우이다. 하지만 `''` 은 객체로 평가될 수도 있다 

```js
var str = ''
var length = str && str.length // ''
var length = str?.length // 0
```

 

### null 병합 연산자

- ES11
- `??` 는 좌항의 피연산자가 null 또는 undefined 인 경우 우항의 피연산자를 반환하고 그렇지 않으면 좌항의 피연산자를 반환한다. 
- null 병합 연산자 `??` 는 변수에 기본값을 설정할 때 유용하다

```js
var foo = null ?? 'string' // 'string'
var foo = '' || 'string' // ''
```

- null 병합 연산자는 좌항이 Falsy 값이라고 해도 null 또는 undefined 가 아니면 좌항을 그대로 반환한다.

