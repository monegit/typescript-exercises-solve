### π νμ΄
1. is ν€μλλ₯Ό μ΄μ©ν νμ κ°λλ€.
2. isAdmin, isUser ν¨μμ λ°ν νμμ `λ§€κ°λ³μλͺ is interface`λ‘ νλ©΄ λ§€κ°λ³μ κ°μ΄ λΉκ΅ μ°μ°μμ μΌμΉνλ©΄ `boolean` κ°μ λ°νν΄μ€λ€.

> π‘ **μ°Έκ³ **
> 
> `is ν€μλ`λ λ§€κ°λ³μλ₯Ό interface(ν΄λΉ λ¬Έμ μμλ User interface)λ‘ μ§μ νκ³  νΉμ  `property`μ μ‘΄μ¬ μ λ¬΄λ₯Ό `bool`νμμΌλ‘ λ°ννλ€.

---

### π€ Before
```ts
// line 46
export function isAdmin(person: Person) {...}

// line 50
export function isUser(person: Person) {...}
```

### π After
```ts
// line 46
export function isAdmin(person: Person): person is Admin {...}

// line 50
export function isUser(person: Person): person is User {...}
```