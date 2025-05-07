## 🔍 What are some differences between **interfaces** and **types** in TypeScript?

We can use both `interface` and `type` to shape an object. However, there are some significant differences. Let's dive into them:

---

### ✅ 1. Structure

- First, let's have a look at how we define `type` and `interface` respectively. It's a convention to use capital letter for the first letter (**PascalCase**) when we declare types.

```ts
type Student = {
  name: string;
  age: number;
};
```

```ts
interface Teacher {
  name: string;
  age: number;
}
```

- Did you notice we used '=' (equals sign) to declare type, but there is no equal sign in interface?

### ✅ 2. Extending

- Now let's learn how we can extend types using both `type` and `interface`.

* If we want to add another property named school in the `type` `Student`, we can write it using another class name like the following using intersection (&)-

```ts
type StudentWithSchool = Student & { school: string };
```

- We can also use `interface` to extend the properties of a type. For example, if we want to include the designation of the teacher in a new class, we can write-

```ts
interface TeacherWithDesignation extends Teacher {
  designation: string;
}
```

---

### ✅ 3. Declaration Merging

- We can re-declare **Interfaces** and TypeScript merges them for us:

  ```ts
  interface User {
    name: string;
  }

  interface User {
    age: number;
  }

  // Resulting User: { name: string; age: number }
  ```

- However, **Types** cannot be re-declared:

  ```ts
  type User = { name: string };
  // type User = { age: number }; ❌ Error: Duplicate identifier
  ```

✅So, we will use `interface` if we need flexibility across modules.

---

### ✅ 4. Unions and Primitives

- **Only `type`** can represent **unions**, **intersections**, and **primitives**:

  ```ts
  type ID = number | string;
  type Ions = "cation" | "anion"; //string literal union, which is a primitive type data
  ```

- `interface` cannot represent these structures.

✅ We will use `type` when dealing with complex type logic.

✅ Interface is only used to declare non-primitive data types, such as objects and class-like structures. (Remember we always use curly braces with `interface`?)

---

### ✅ 5. Functions

- Let's have a look at how we use `type` and `interface` to declare functions.

```ts
type AddTwoNumbers = (num1: number, num2: number) => number;

const addTwoNumbers: AddTwoNumbers = (a, b) => a + b;
```

```ts
interface MultiplyTwo {
  (num: number): number;
}

const multiplyTwo: MultiplyTwo = (n) => n * 2;
```

✅ What we have learnt-

- `interface` is great for object shapes and inheritance.

- `type` is more flexible for unions, primitives, and advanced combinations.

- Both are powerful — use whichever fits your use case best!

---

---

## Using Union and Intersection Types in TypeScript

In TypeScript, we can combine types using `Union` and `Intersection` types. These allow us to create more flexible and reusable type definitions. So, these two are two of the significant powers of Typescript. 💪

### 🎯 What is a Union Type?

- A Union Type describes a value that can be one of several types. We use the vertical bar (|) to separate each type.

```ts
type WindowStates = "open" | "closed" | "minimized" | string;
```

### 🎯 What is an Intersection Type?

- An Intersection Type combines multiple types into one. We use the 'and' operator (&) to add these types. This allows for type composition.

```ts
type Person = {
  name: string;
  age: number;
};

type Employee = {
  employeeId: string;
  department: string;
};

type Staff = Person & Employee;

const staffMember: Staff = {
  name: "Ayesha",
  age: 28,
  employeeId: "EMP123",
  department: "HR",
};
```

I hope you enjoyed this post. Thanks for reading.
