### 📝 풀이
1. is 키워드를 이용한 타입 가드다.
2. isAdmin, isUser 함수의 반환 타입을 `매개변수명 is interface`로 하면 매개변수 값이 비교 연산자와 일치하면 `boolean` 값을 반환해준다.

> 💡 **참고**
> 
> `is 키워드`는 매개변수를 interface(해당 문제에서는 User interface)로 지정하고 특정 `property`의 존재 유무를 `bool`타입으로 반환한다.

### 🐤 Before
```ts
// line 46
export function isAdmin(person: Person) {...}

// line 50
export function isUser(person: Person) {...}
```

### 🐔 After
```ts
// line 46
export function isAdmin(person: Person): person is Admin {...}

// line 50
export function isUser(person: Person): person is User {...}
```