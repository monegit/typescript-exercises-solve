### 📝 풀이
1. 이 문제는 유틸리티 타입을 이용해 해결할 수 있었다.
2. Omit을 이용하여 User, Admin에서 'type' 키를 제거하고, 그 자리에 `{ type: "powerUser" }` 을 넣은 타입을 만들어준다.

---

### 🐤 Before
```ts
// line 34
type PowerUser = unknown;
```

### 🐔 After
```ts
// line 34
type PowerUser = Omit<Admin, "type"> &
  Omit<User, "type"> & { type: "powerUser" };
```