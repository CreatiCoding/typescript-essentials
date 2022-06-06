# 3 day

- Object Literal Type

  - 객체를 선언하면 자동으로 선언됨
  - Object.create 함수를 쓰면 any로 타입이 지정된다.
  - object 타입: 원시형 값을 넣는 걸 방지하고자 사용함

- array

  - 같은 타입의 값들을 모아놓은 타입
  - 충돌날 수 있어서 Array<number> 보다 number[]을 추천
  - (number | string)[] vs Array<number | string>

- tupple

  - `let x: [string, number]` 와 같이 요소 순서에 타입을 지정할 수 있음
  - 순서가 맞지 않다면, not assignable 로 순서에 맞는 타입을 보장하도록 오류 발생시킴
  - 지정된 범위를 넘어선 곳에 추가를 하지 못하도록 막아줌
  - 구조분해할당을 하면, 각 변수에 타입이 지정됨
  - 좋은 추론을 통해 정확한 타이핑을 할 수 있어 런타임이 안전한 코드를 생산할 수 있다.

- any

  - any가 달려있다면 어떤 함수 호출이나 동작에 제약이 없다.
  - 보호 장치가 없다고 볼 수 있으므로 웬만하면 사용하지 않도록 하자.
  - 타이핑이 안되어 있는 경우에 오류를 발생시키는 no-explicit-any 규칙이 있다.
  - https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/eslint-plugin/docs/rules/no-explicit-any.md
  - strict 를 활성화하면 no-explicit-any도 활성화된다.
  - promise 혹은 action과 같이 일종의 오염성을 가지고 있으므로 안 쓸수록 좋다.
  - 누군가 이미 any를 쓰고 있으므로 오염의 특징을 가진 any를 피할 수 없는 곳이 발생할 수 밖에 없다.
  - as number로 assertion 을 하여 해결할 수 있음
  - unknown을 활용한 타입가드를 이용하면 타입누수를 해결할 수 있다.

- unknown

  - any 보다 Type-safe한 타입
  - 모르는 변수의 타입(api를 통해 불러오는 동적 데이터)
  - 좀 더 명시적으로 "타입이 어떻게 될지 예측이 안된다."라는 의미로 any보다 unknwon이 더 적절한 경우가 있다.
  - declare const maybe: unknwon;
  - const aNUmber: number = maybe;
  - unknwon은 다른 타입의 변수에 바로 할당할 수 없도록 한다.
  - maybe === true인 블럭 안에서는 boolean 타입 변수에 maybe를 대입할 수 있다.
  - (런타임 함수 typeof 를 이용하면 타입이 문자열로 튀어나온다)
  - (typeof 타입가드) typeof maybe === "string" 인 스코프에서는 string 타입으로 사용할 수 있다.
  - 타입가드에는 typeof, instanceof, 사용자 정의가 존재한다.
  - any도 타입가드 자체는 할 수 있긴 하다.

- never

  - 보통 return 에 사용된다.
  - 함수가 정상적으로 종료되지 않는 것을 의미한다.
  - `function error(message): never { throw new Error(message); }`
  - `function infiniteLoop(): never { while(true) {} }`
  - never 타입을 반환하는 함수를 return 해도 never 타입이 된다.
  - never는 모든 타입의 Sub 타입
  - never에는 그 어떤 것도 할당할 수 없음 (any 조차)
  - 잘못된 타입을 넣는 실수를 막을 때 사용한다.
  - let a: string = "hello";
  - if(typeof a !== "string") { a; }
  - 조건부 타입
    - type Indexable<T> = T extends string ? T & { [index: string]: any } : never;
    - type ObjectIndexable = Indexable<{}>
    - T 가 문자열이 아니라면 never를 넣어주도록 하여, never 변수에 대입을 하지 못하도록 막는다.

- void

  - 보통 return 에 사용된다.
  - 어떠한 상태도 가지지 않는 타입을 의미
  - undefined를 리턴하는 함수의 반환 타입으로 사용됨
  - void 라는 값을 가질 필요가 없지만 다른 언어에서 많이 쓰기 때문에 ts에서도 의미상으로 리턴 타입을 이용한다.
  - void 반환 타입의 함수는 오로지 undefined만을 return 하거나 return; 만 사용할 수 있다.
