### 📝 풀이

1. 선택적으로 프로퍼티를 사용하는 문제
2. filterUsers에서 persons 배열에 있는 객체를 filter로 걸러 객체가 `User` 타입이면 해당 객체일때, age가 23인 객체를 반환
3. 하지만 filterUsers의 인자는 User로 받아 { age: 23 } 형식으로 받지 못함
4. 그래서 filterUsers 함수의 criteria의 타입을 유틸리티 타입 Partial\<User>로 바꿔준다.

> 💡 **참고**
> 
> **Partial** : `Type` 집합의 모든 프로퍼티를 선택적으로 타입을 생성합니다. 이 유틸리티는 주어진 타입의 모든 하위 타입 집합을 나타내는 타입을 반환합니다.
>
> **Exclude** : `ExcludedUnion`에 할당할 수 있는 모든 유니온 멤버를 Type에서 제외하여 타입을 생성합니다.

---

**<center>Using Partial</center>**

### 🐤 Before
```ts
// line 95
export function filterUsers(persons: Person[], criteria: User): User[] {...}
```

### 🐔 After
```ts
// line 95
export function filterUsers(
  persons: Person[],
  criteria: Partial<User>
): User[] {...}
```
---

**<center>Using Exclude</center>**

### 🐤 Before
```ts
// line 95
export function filterUsers(persons: Person[], criteria: User): User[] {...}

// line 97
const criteriaKeys = Object.keys(criteria) as (keyof User)[];
```

### 🐔 After
```ts
// add type
type Criteria = Exclude<{ age: number }, User>;

// line 97
export function filterUsers(persons: Person[], criteria: Criteria): User[] {...}

// line 99
const criteriaKeys = Object.keys(criteria) as (keyof Criteria)[];
```

