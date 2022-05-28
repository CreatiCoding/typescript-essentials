# 2day

- Static Types: 개발하면서 오류를 알 수 있다.
- Dynamic Types: 런타임으로 돌려야 오류를 알 수 있다.

- Primitive Type

  - 실제 값을 저장하는 자료형
  - boolean, number, string, symbol, null, undefined
  - literal 값으로 `Primitive Type`의 `Sub Type`을 나타낼 수 있음
  - Wrapper 객체로 만들 수 있지만, 주의해야할 점은 `Primitive Type`과는 다르다는 점이다.
  - 대문자로 시작하는 Wrapper Type은 타입으로 사용해서는 안된다.

- Boolean

  - 팁) strict: true 가 중요하다.
  - boolean 타입 변수를 typeof 해보면 boolean가 나온다.
  - Boolean 타입 변수에는 boolean 값을 넣을 수 있지만, 그 반대는 불가능하다.

- Number

  - JS와 마찬가지로 TS도 모든 숫자는 부동 소수점 값이다.
  - 16진수, 10진수, 2진수, 8진수 리터럴을 지원한다.
  - NaN, 1_000_000 과 같은 표기를 지원한다.

- String

  - JS에서 가능한 ', " 와 `(backtick)을 이용한 template string 방식을 모두 지원한다.

- Symbol

  - new Symbol 불가능
  - Symbol은 함수이며, primitive value를 인자로 받을 수 있다.
  - 인자로 받은 값이 동일해도, 반환된 심볼 값은 서로 다르다.
  - 고유하고 수정불가능한 값으로 만들어 접근을 제어하는 경우에 사용한다.
  - `const sym = SYmbol(); obj[sym];`
  - 함수로 사용할 때는 `Symbol`로 타입으로 사용할 때는 `symbol`로 사용함을 유의해야한다.

- Undefined && Null

  - undefined와 null은 모든 타입의 서브 타입이므로, number에 null과 undefined를 넣을 수 있다.
  - 따라서 strict(--strictNullChecks)를 사용하면, 개발하면서 null, undefined를 할당할 수 없게 할 수 있다.
  - Union Type을 쓰면, 변수를 nullable하거나 undefined 가 되도록 할 수 있다.
  - Union Type을 쓰면 나중에 소개될 예정인 타입가드를 할 수 있다.
  - null을 런타임에서 typeof 연산자를 이용해서 알아내면, object다.
  - undefined를 런타임에서 typeof 연산자를 이용해서 알아내면, undefined다.
  - strict
