### ๐ ํ์ด

1. ์ ํ์ ์ผ๋ก ํ๋กํผํฐ๋ฅผ ์ฌ์ฉํ๋ ๋ฌธ์ 
2. filterUsers์์ persons ๋ฐฐ์ด์ ์๋ ๊ฐ์ฒด๋ฅผ filter๋ก ๊ฑธ๋ฌ ๊ฐ์ฒด๊ฐ `User` ํ์์ด๋ฉด ํด๋น ๊ฐ์ฒด์ผ๋, age๊ฐ 23์ธ ๊ฐ์ฒด๋ฅผ ๋ฐํ
3. ํ์ง๋ง filterUsers์ ์ธ์๋ User๋ก ๋ฐ์ { age: 23 } ํ์์ผ๋ก ๋ฐ์ง ๋ชปํจ
4. ๊ทธ๋์ filterUsers ํจ์์ criteria์ ํ์์ ์ ํธ๋ฆฌํฐ ํ์ Partial\<User>๋ก ๋ฐ๊ฟ์ค๋ค.

> ๐ก **์ฐธ๊ณ **
> 
> **Partial** : `Type` ์งํฉ์ ๋ชจ๋  ํ๋กํผํฐ๋ฅผ ์ ํ์ ์ผ๋ก ํ์์ ์์ฑํฉ๋๋ค. ์ด ์ ํธ๋ฆฌํฐ๋ ์ฃผ์ด์ง ํ์์ ๋ชจ๋  ํ์ ํ์ ์งํฉ์ ๋ํ๋ด๋ ํ์์ ๋ฐํํฉ๋๋ค.
>
> **Exclude** : `ExcludedUnion`์ ํ ๋นํ  ์ ์๋ ๋ชจ๋  ์ ๋์จ ๋ฉค๋ฒ๋ฅผ Type์์ ์ ์ธํ์ฌ ํ์์ ์์ฑํฉ๋๋ค.

---

**<center>Using Partial</center>**

### ๐ค Before
```ts
// line 95
export function filterUsers(persons: Person[], criteria: User): User[] {...}
```

### ๐ After
```ts
// line 95
export function filterUsers(
  persons: Person[],
  criteria: Partial<User>
): User[] {...}
```
---

**<center>Using Exclude</center>**

### ๐ค Before
```ts
// line 95
export function filterUsers(persons: Person[], criteria: User): User[] {...}

// line 97
const criteriaKeys = Object.keys(criteria) as (keyof User)[];
```

### ๐ After
```ts
// add type
type Criteria = Exclude<{ age: number }, User>;

// line 97
export function filterUsers(persons: Person[], criteria: Criteria): User[] {...}

// line 99
const criteriaKeys = Object.keys(criteria) as (keyof Criteria)[];
```

