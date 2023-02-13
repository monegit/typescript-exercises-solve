### 📝 풀이
1. 이 문제는 `User`과 `Admin`이 차집합 하는 프로퍼티를 사용하려고 하는데 **type guard**를 하지 않아 발생하는 오류다.
2. 새 함수를 만들어 `is`문을 사용하여 타입 가드를 해주거나, 아래와 같이 `in`을 이용하여 타입 가드를 만들어 해결한다.


> 💡 **참고**
> 
> `union type`은 `type guard`가 없을 경우 교집합 하는 `property`만 사용 가능하다.
> 
> `in 연산자`는 객체 내부에 특정 `property`의 존재 유무를 `bool`타입으로 반환한다.
> 
> `is 연산자`는 매개변수를 interface(해당 문제에서는 User interface)로 지정하고 특정 `property`의 존재 유무를 `bool`타입으로 반환한다.

---

### 🐤 Before
> [problem.ts](problem.ts)
```ts
// line 57
let additionalInformation: string;

// line 58
if (person.role) {...}
```

### 🐔 After
> [index.ts](index.ts)
```ts
// in 연산자

// line 57
let additionalInformation: string = "";

// line 59
if ("role" in person) {...}
```

```ts
// is 연산자

// add 'isUser' function
function isUser(arg: any): arg is User {
  return arg.occupation !== undefined;
}

// edit 'logPerson' function
export function logPerson(person: Person) {
	...

  if (isUser(person)) {
    additionalInformation = person.occupation;
  } else {
    additionalInformation = person.role;
  }
	
	...
}
```