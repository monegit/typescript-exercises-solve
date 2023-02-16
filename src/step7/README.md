### 📝 풀이
1. 이 문제는 generic 문제다.
2. any로도 풀어지긴 하지만 오답이어서 밑 generic 힌트를 보고 문제를 해결했다.


> 💡 **참고**
> 
> **Generic** : 사용자가 제공하는 `type`을 `return type`으로 다시 사용하기 때문에 `any type`같이 동적 타입 할당 보다는 범용성이 더 높아진다.
---

### 🐤 Before
```ts
// line 81
export function swap(v1, v2) {...}
```

### 🐔 After
```ts
// line 81
export function swap<Type1, Type2>(v1: Type1, v2: Type2): [Type2, Type1] {...}
```