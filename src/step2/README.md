### ๐ ํ์ด
1. ํด๋น ๋ฌธ์ ๋ `type alias`๋ก ์ฝ๊ฒ ํด๊ฒฐ ๊ฐ๋ฅํ ๋ฌธ์ ๋ค.
2. type alias๋ก `interface User`์ `interface Admin`์ `Person`์ **union type**์ผ๋ก ๋ฌถ์ด์ ํ์์ ์ง์ ํด์ค๋ค.
3. User๋ก ํ์ ์ง์ ๋ ๋ถ๋ถ์ Person์ผ๋ก ๋ณ๊ฒฝํด์ค๋ค.

---

### ๐ค Before
> [problem.ts](problem.ts)
```ts
// line 33
export type Person = unknown;

// line 35
export const persons: User[] = [...]

// line 58
export function logPerson(user: User) {...}
```

### ๐ After
> [index.ts](index.ts)
```ts
// line 33
export type Person = User | Admin;

// line 35
export const persons: Person[] = [...]

// line 58
export function logPerson(user: Person) {...}
```