# Understanding Type Narrowing in TypeScript

## Introduction
TypeScript lets a variable hold several possible types through unions. Type narrowing is the process of refining a broad type into a more specific one so the compiler knows which operations are safe. It removes guesswork and prevents many runtime errors.

## Narrowing with typeof
The typeof operator works well for primitives. Inside each branch, TypeScript treats the variable as that exact type.

```ts
function format(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value.toFixed(2);
}
```

## Narrowing with instanceof
Use instanceof when working with classes. It checks the prototype chain at runtime.

```ts
function describe(error: Error | string): string {
  if (error instanceof Error) {
    return error.message;
  }
  return error;
}
```

## Narrowing with the in operator
The in operator checks whether a property exists on an object. It is ideal for distinguishing object shapes in a union.

```ts
type Car = { drive: () => void };
type Boat = { sail: () => void };

function move(vehicle: Car | Boat): void {
  if ("drive" in vehicle) {
    vehicle.drive();
  } else {
    vehicle.sail();
  }
}
```

## Conclusion
Type narrowing turns flexible union types into safe, specific ones. By choosing typeof for primitives, instanceof for classes, and in for object shapes, we write code that the compiler can verify. This leads to fewer bugs and clearer intent in every function we write.
