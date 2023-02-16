### 📝 풀이

1. 이 문제는 제네릭으로 해결할 수 있다.
2. AdminsApiResponse와 UsersApiResponse 객체를 제거하고 내용을 ApiResponse에 넣어준다. 그리고 data에 `T`을 넣어 제네릭 처리 해준다.

---

### 🐤 Before
```ts
// line 61
export type ApiResponse<T> = unknown;

// line 73
export function requestAdmins(
  callback: (response: ApiResponse<Admin[]>) => void
) {...}

// line 80
export function requestUsers(
  callback: (response: ApiResponse<User[]>) => void
) {...}

// line 97
export function requestCurrentServerTime(
  callback: (response: unknown) => void
) {...}

// line 106
export function requestCoffeeMachineQueueLength(
  callback: (response: unknown) => void
) {...}
```

### 🐔 After
```ts
// line 61
export type ApiResponse<T> =
  | {
      status: "success";
      data: T;
    }
  | {
      status: "error";
      error: string;
    };

// line 71
export function requestAdmins(callback: (response: AdminsApiResponse) => void) {...}

// line 80
export function requestUsers(callback: (response: UsersApiResponse) => void) {...}

// line 89
export function requestCurrentServerTime(
  callback: (response: ApiResponse<number>) => void
) {...}

// line 98
export function requestCoffeeMachineQueueLength(
  callback: (response: ApiResponse<number>) => void
) {...}
```