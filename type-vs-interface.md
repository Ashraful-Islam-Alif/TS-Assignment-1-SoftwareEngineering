Type Alias vs Interface in TypeScript

Question: What are the core differences between type aliases and interface in TypeScript? When should you choose one over the other?

Introduction

In TypeScript we can describe data in two ways: with a type alias or with an interface. For plain objects they look similar, but they are not the same.

Core Differences

An interface is generally connected to objects. A type alias is more connected to literals, unions, tuples and primitives. We can write type ID = number or type Role = "admin" | "member", but an interface cannot do this.

ts
type ID = number;
type Role = "admin" | "member";

interface User {
name: string;
id: ID;
role: Role;
}

An interface can be extended using extends, while a type alias uses the & symbol for intersection.

ts
interface Animal {
species: string;
}
interface Cat extends Animal {
breed: string;
}

type Vehicle = { brand: string };
type Car = Vehicle & { model: string };

Another difference is declaration merging. If we write the same interface twice, TypeScript merges them into one. A type alias with the same name twice gives an error.

ts
interface IEmployee {
name: string;
}
interface IEmployee {
id: number;
}
When to Choose

Use interface when we are describing an object. Use type when we need a union, a literal, a tuple or a primitive alias.

Conclusion

Interface is best for objects, and type alias is best for unions, literals and tuples.
