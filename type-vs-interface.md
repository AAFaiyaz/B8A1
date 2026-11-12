# `type` Aliases vs `interface` in TypeScript

`type` and `interface` both can be used for describing object. The differences are in what else each one can do.

## 1. What they can describe

An `interface` can only describe an object (including functions and classes). A `type` can be used for describing any data types. For examples

```typescript
type ID = string | number; // union
type Status = "active" | "inactive"; // literal union
type Point = [number, number]; // tuple
type Handler = (event: string) => void; // function type
```

None of these can be written as an `interface`.

## 2. Merge Differences

Two interfaces with the same name can be merge into one. Two types with the same name are an error:

```typescript
interface User {
  name: string;
}
interface User {
  age: number;
}
// User is now { name: string; age: number }

type Admin = { name: string };
type Admin = { age: number }; // Error
```

## 3. Extending

Interfaces use `extends`, while types combine with an intersection `&`:

```typescript
interface Animal {
  name: string;
}
interface Dog extends Animal {
  breed: string;
}

type Cat = { name: string } & { indoor: boolean };
```

There are other advanced scenarios where they behave differently than each other.

## When to choose which

- **Use `interface`** for object, especially ones that others will extend or implement, like class contracts, public APIs and library types.

- **Use `type`** for anything that isn't a plain object: unions, tuples, function types, aliases for primitives, and mapped or conditional types.
- **A common rule of thumb** is to use `interface` until you need something only `type` can do.
