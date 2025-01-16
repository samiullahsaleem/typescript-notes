
# TypeScript Notes

This repository contains comprehensive TypeScript notes that cover both basic and advanced topics. These notes include practical examples, explanations of core concepts, and utility types frequently asked in interviews.

## Table of Contents
1. [Introduction to TypeScript](#introduction-to-typescript)
2. [Variables and Types](#variables-and-types)
3. [Functions](#functions)
4. [Classes and Interfaces](#classes-and-interfaces)
5. [Generics](#generics)
6. [Enums](#enums)
7. [Type Assertions](#type-assertions)
8. [Type Inference](#type-inference)
9. [Union and Intersection Types](#union-and-intersection-types)
10. [Modules](#modules)
11. [Decorators](#decorators)
12. [Advanced Types](#advanced-types)
13. [Utility Types](#utility-types)
14. [Common Interview Topics](#common-interview-topics)
15. [Advanced Topics](#advanced-topics)
16. [TypeScript and JavaScript Differences](#typescript-and-javascript-differences)

---

## 1. Introduction to TypeScript
TypeScript is a superset of JavaScript that adds static typing to the language. It helps to catch errors early during development and makes code more predictable. TypeScript is compiled down to JavaScript, which can run anywhere JavaScript runs.

### Key Benefits:
- Type safety
- Object-oriented features (e.g., classes, interfaces)
- Readable and maintainable code
- Better refactoring and IDE support

---

## 2. Variables and Types
TypeScript allows explicit type declarations as well as type inference. Here are the basic types:

### Basic Types:
- **String**: `let name: string = "John";`
- **Number**: `let age: number = 30;`
- **Boolean**: `let isActive: boolean = true;`
- **Array**: `let numbers: number[] = [1, 2, 3];`
- **Tuple**: `let tuple: [string, number] = ["hello", 2];`
- **Any**: `let anything: any = "Hello";`

### Special Types:
- **Void**: Used for functions that don’t return a value.
- **Null and Undefined**: Represent the absence of value.
- **Never**: Represents a function that never returns (e.g., throws an error).

---

## 3. Functions
Functions in TypeScript can have defined parameter types and return types.

### Function Declaration:
```typescript
function greet(name: string): string {
  return "Hello, " + name;
}
```

### Arrow Functions:
```typescript
const add = (x: number, y: number): number => x + y;
```

### Optional Parameters:
```typescript
function logMessage(message: string, level: string = "info"): void {
  console.log(`[${level}] ${message}`);
}
```

---

## 4. Classes and Interfaces

### Classes
TypeScript supports object-oriented programming features like classes and inheritance.

```typescript
class Animal {
  name: string;
  constructor(name: string) {
    this.name = name;
  }

  speak(): void {
    console.log(`${this.name} makes a sound.`);
  }
}
```

### Interfaces
Interfaces define the shape of an object.

```typescript
interface Person {
  name: string;
  age: number;
}

const employee: Person = {
  name: "Alice",
  age: 25,
};
```

---

## 5. Generics
Generics allow creating reusable components.

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>("Hello, Generics!");
```

---

## 6. Enums
Enums allow for defining a set of named constants.

```typescript
enum Direction {
  Up = 1,
  Down,
  Left,
  Right,
}

let move: Direction = Direction.Up;
```

---

## 7. Type Assertions
Type assertions help when you are certain of the type of a value.

```typescript
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```

---

## 8. Type Inference
TypeScript can infer types when they are not explicitly declared.

```typescript
let num = 10; // inferred as number
```

---

## 9. Union and Intersection Types

### Union Types:
Used when a value can be of multiple types.

```typescript
function printId(id: string | number): void {
  console.log(id);
}
```

### Intersection Types:
Combines multiple types into one.

```typescript
interface Person {
  name: string;
}

interface Employee {
  employeeId: number;
}

type EmployeeDetails = Person & Employee;

const emp: EmployeeDetails = { name: "John", employeeId: 1234 };
```

---

## 10. Modules
TypeScript supports modules, which allow you to split code into smaller, reusable components.

### Exporting from a module:
```typescript
export class MyClass {
  constructor() {
    console.log("MyClass initialized.");
  }
}
```

### Importing from a module:
```typescript
import { MyClass } from './myModule';
```

---

## 11. Decorators
Decorators are a feature used to annotate or modify classes, methods, properties, or parameters. Decorators are often used in frameworks like Angular.

```typescript
function Logger(target: any) {
  console.log(target);
}

@Logger
class MyClass {
  constructor() {
    console.log("MyClass Initialized.");
  }
}
```

---

## 12. Advanced Types

### Mapped Types:
```typescript
type ReadOnly<T> = {
  readonly [K in keyof T]: T[K];
};
```

### Conditional Types:
```typescript
type IsString<T> = T extends string ? "Yes" : "No";
```

### Index Types:
```typescript
type Person = {
  [key: string]: string;
};
```

---

## 13. Utility Types
Utility types are built-in types provided by TypeScript to simplify complex type definitions.

- **Partial**: Makes all properties in a type optional.
```typescript
type PartialPerson = Partial<Person>;
```

- **Required**: Makes all properties in a type required.
```typescript
type RequiredPerson = Required<Person>;
```

- **Readonly**: Makes all properties in a type read-only.
```typescript
type ReadonlyPerson = Readonly<Person>;
```

- **Pick**: Picks a subset of properties from a type.
```typescript
type NameOnly = Pick<Person, 'name'>;
```

- **Omit**: Omit specific properties from a type.
```typescript
type WithoutAge = Omit<Person, 'age'>;
```

---

## 14. Common Interview Topics

### Questions Often Asked in TypeScript Interviews:
- What are the benefits of using TypeScript?
- What is the difference between `any` and `unknown`?
- Explain the concept of generics in TypeScript.
- How does TypeScript handle type inference?
- What are the uses of `readonly` and `private` modifiers?
- What are Union and Intersection types?
- How would you declare a function with optional parameters?
- What is the difference between interfaces and type aliases?

---

## 15. Advanced Topics

### Type Guards:
```typescript
function isString(value: unknown): value is string {
  return typeof value === 'string';
}
```

### Type Aliases for Complex Types:
```typescript
type StringOrNumber = string | number;
type User = { id: number, name: string };
```

### Mixins:
Mixins allow combining multiple classes into a single class.
```typescript
class CanSpeak {
  speak() {
    console.log("Speaking...");
  }
}

class Person {
  name: string;
}

class TalkingPerson extends CanSpeak(Person) {}
```

### Modules and Namespaces:
TypeScript modules are different from namespaces. Use modules for larger projects where code is divided into multiple files.

---

## 16. TypeScript and JavaScript Differences

- **Static vs Dynamic Typing**: TypeScript has static typing while JavaScript is dynamically typed.
- **Compilation**: TypeScript code must be compiled to JavaScript.
- **Type Annotations**: TypeScript supports static type annotations to catch errors at compile time.
- **ES6+ Features**: TypeScript supports many ES6+ features like arrow functions, async/await, and classes out of the box.

