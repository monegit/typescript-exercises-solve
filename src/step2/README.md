### 📝 풀이
1. 해당 문제는 `type alias`로 쉽게 해결 가능한 문제다.
2. type alias로 `interface User`와 `interface Admin`을 `Person`에 **union type**으로 묶어서 타입을 지정해준다.
3. User로 타입 지정된 부분을 Person으로 변경해준다.

---

### 🐤 Before
> [problem.ts](problem.ts)
```ts
// line 33
export type Person = unknown;

// line 35
export const persons: User[] = [...]

// line 58
export function logPerson(user: User) {...}
```

### 🐔 After
> [index.ts](index.ts)
```ts
// line 33
export type Person = User | Admin;

// line 35
export const persons: Person[] = [...]

// line 58
export function logPerson(user: Person) {...}
```