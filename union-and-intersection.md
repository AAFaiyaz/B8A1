# Combining Union (`|`) and Intersection (`&`) Types

- Union (`A | B`): the value is one of the types.
- Intersection (`A & B`): the value has all of the types at once.

## Example

### 1. An ID that can be a number or a string

```typescript
type ID = string | number;
type Product = { id: ID } & { name: string; price: number };

const laptop: Product = { id: 101, name: "Laptop", price: 899 };
const mouse: Product = { id: "M-7", name: "Mouse", price: 25 };
```

Every product has an `id`, a `name` and a `price` (`&`), and the `id` can be a number or a string (`|`).
