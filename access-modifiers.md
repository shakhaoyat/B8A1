# Access Modifiers in TypeScript OOP

## Introduction
Access modifiers control which parts of a class can be reached from outside. They support encapsulation, which keeps internal details hidden and exposes only what is necessary. TypeScript offers public,private,protected, and readonly.

## Public and Private
Members are public by default and can be accessed anywhere. A private member is only accessible inside the class that declares it.

```ts
class Account {
  public owner: string;
  private balance: number;

  constructor(owner: string, balance: number) {
    this.owner = owner;
    this.balance = balance;
  }

  getBalance(): number {
    return this.balance;
  }
}
```

Reading account.balance outside the class causes a compile error.

## Protected
A protected member is visible inside the class and its subclasses, but not outside them.

```ts
class Person {
  protected name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class Student extends Person {
  introduce(): string {
    return `Hi, I am ${this.name}`;
  }
}
```

## Readonly
A readonly property can be assigned only at declaration or in the constructor. It cannot change afterward, which is useful for identifiers.

```ts
class User {
  readonly id: number;
  constructor(id: number) {
    this.id = id;
  }
}
```

## Conclusion
Access modifiers make classes safer and easier to maintain. Use private for internal state,protected for inheritance, public for the interface, and readonly for values that must never change.
