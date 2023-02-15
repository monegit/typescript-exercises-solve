### 📝 풀이
1. Function Overload를 이용한 문제다.
2. `personType`이 user이면 User 타입으로, admin이면 Admin 타입으로 함수를 오버로드 해준다.
3. 함수 구현부 부분은 Person 타입이 `User | Admin` 타입이기 때문에 인자 criteria를 Partial\<Person>로, 반환 타입은 Person[]로 해준다.

> 💡 **참고**
>
> **Function Overload** : 인자(argument)가 다르지만 이름이 같은 함수를 여러개 만드는 방법을 말한다. 예를 들어서 날짜를 출력하는 함수를 만들때 `timestamp`, `year, month, day`와 같이 서로 다른 매개변수로 같은 기능을 수행하는 함수를 만들때 쓰인다.


---

### 🐤 Before
```ts
// line 68
export function filterPersons(
  persons: Person[],
  personType: string,
  criteria: unknown
): unknown[] {...}
```

### 🐔 After
```ts
// line 68
export function filterPersons(
  persons: Person[],
  personType: string,
  criteria: Partial<Person>
): Person[] {...}

// add function
export function filterPersons(
  persons: Person[],
  personType: "user",
  criteria: Partial<User>
): User[];

// add function
export function filterPersons(
  persons: Person[],
  personType: "admin",
  criteria: Partial<Admin>
): Admin[];
```