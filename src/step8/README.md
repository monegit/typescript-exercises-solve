### π νμ΄
1. μ΄ λ¬Έμ λ μ νΈλ¦¬ν° νμμ μ΄μ©ν΄ ν΄κ²°ν  μ μμλ€.
2. Omitμ μ΄μ©νμ¬ User, Adminμμ 'type' ν€λ₯Ό μ κ±°νκ³ , κ·Έ μλ¦¬μ `{ type: "powerUser" }` μ λ£μ νμμ λ§λ€μ΄μ€λ€.

---

### π€ Before
```ts
// line 34
type PowerUser = unknown;
```

### π After
```ts
// line 34
type PowerUser = Omit<Admin, "type"> &
  Omit<User, "type"> & { type: "powerUser" };
```