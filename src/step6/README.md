### ๐ ํ์ด
1. Function Overload๋ฅผ ์ด์ฉํ ๋ฌธ์ ๋ค.
2. `personType`์ด user์ด๋ฉด User ํ์์ผ๋ก, admin์ด๋ฉด Admin ํ์์ผ๋ก ํจ์๋ฅผ ์ค๋ฒ๋ก๋ ํด์ค๋ค.
3. ํจ์ ๊ตฌํ๋ถ ๋ถ๋ถ์ Person ํ์์ด `User | Admin` ํ์์ด๊ธฐ ๋๋ฌธ์ ์ธ์ criteria๋ฅผ Partial\<Person>๋ก, ๋ฐํ ํ์์ Person[]๋ก ํด์ค๋ค.

> ๐ก **์ฐธ๊ณ **
>
> **Function Overload** : ์ธ์(argument)๊ฐ ๋ค๋ฅด์ง๋ง ์ด๋ฆ์ด ๊ฐ์ ํจ์๋ฅผ ์ฌ๋ฌ๊ฐ ๋ง๋๋ ๋ฐฉ๋ฒ์ ๋งํ๋ค. ์๋ฅผ ๋ค์ด์ ๋ ์ง๋ฅผ ์ถ๋ ฅํ๋ ํจ์๋ฅผ ๋ง๋ค๋ `timestamp`, `year, month, day`์ ๊ฐ์ด ์๋ก ๋ค๋ฅธ ๋งค๊ฐ๋ณ์๋ก ๊ฐ์ ๊ธฐ๋ฅ์ ์ํํ๋ ํจ์๋ฅผ ๋ง๋ค๋ ์ฐ์ธ๋ค.


---

### ๐ค Before
```ts
// line 68
export function filterPersons(
  persons: Person[],
  personType: string,
  criteria: unknown
): unknown[] {...}
```

### ๐ After
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