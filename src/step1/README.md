### 📝 풀이
1. 해당 문제는 `interface` 혹은 `type alias`로 해결 가능한 문제
2. 하지만 [problem.ts](problem.ts)의 주석 중 `Exercise`를 보면 **interface**를 사용하여 User를 정의하라고 함.
3. User를 interface로 바꿔주고, unknown을 User로 변경해준다.

---

### 🐤 Before
> [problem.ts](problem.ts)
```ts
// line 79
export type User = unknown;

// line 81
export const users: unknown[] = [...]

// line 94
export function logPerson(user: unknown) {...}
```

### 🐔 After
> [index.ts](index.ts)
```ts
// line 79
export interface User {
  name: string;
  age: number;
  occupation: string;
}

// line 85
export const users: User[] = [...]

// line 98
export function logPerson(user: User) {...}
```